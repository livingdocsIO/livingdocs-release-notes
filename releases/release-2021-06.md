
editor until: 66.4.3
server until: 128.2.1

**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Newsletter](#newsletter)
- [Webinar](#webinar)
- [System Requirements](#system-requirements)
- [Patches](#repositories)
- [Highlights](#highlights)
- [Breaking Changes](#breaking-changes-fire)
- [Deprecations](#deprecations)
- [APIs](#apis-gift)
- [Internal Changes](#internal-changes)
- [Other Changes](#other-changes)

# Newsletter

* Newsletter: **TODO**
* Subscribe here: https://confirmsubscription.com/h/j/61B064416E79453D


# Webinar

#### Features

* Recording: **TODO**
* Documentation: **TODO**

#### Developers

* Recording: **TODO**
* Slides: **TODO**

# System Requirements

#### Minimal
* Node 14 :fire:
* NPM 7
* Postgres 9.6
* Elasticsearch 6.x
* Redis 5
* Base Docker Images
  * livingdocs-server: `livingdocs/server-base:14`
  * livingdocs-editor: `livingdocs/editor-base:14`

#### Suggested
* Node 16
* NPM 7
* Postgres 13
* Elasticsearch 7
* Redis 6
* Base Docker Images
  * livingdocs-server: `livingdocs/server-base:16`
  * livingdocs-editor: `livingdocs/editor-base:16`

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2021-06`
`@livingdocs/editor` | `release-2021-06`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2021-06",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2021-06

### Livingdocs Server Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2021-06",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2021-06

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text





# Highlights

## Media Library - Multi Language :tada:

With the introduction of the multi language metadata feature, one can now translate metadata into different languages.

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4283)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3512)
  * [Documentation TODO@benib]()

## Media Library - Add Support for Files

Additionally to the existing images and videos, we now also support files in the Media Library.

* References
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3595)
  * [Documentation TODO@benib]()


## Media Library - Video - Add Transcoding Metadata Plugin :tada:

With the video transcoding metadata plugin
- You can notify an external system to start transcoding a video
- The external system can call the public API and respond with transcoding state
- The editor shows the current state

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4324)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3568)
  * [Documentation TODO@romankaravia]()



# Breaking Changes :fire:

### Migrate firstPublicationDate to documents table (pre deployment) :fire:

For productive systems please run a manual migration using `node ./db/manual-migrations/007-populate-first-publication-date.js` to process the documents in batches. The manual migration must be done before `livingdocs-server migrate up`, which contains the same migration, but locks the database by ~10s for 100k documents.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3505)


### Migrate the database

TODO@ralph

- Expected duration?
- Possible data losses?
- Is it a simple migration? (fast/easy downgradable)

```sh
# run grunt migrate to update to the newest database scheme
# migration - 111-add-comments-table.js
#   create comments table + add events to the stream_events_types table
livingdocs-server migrate up
```


### Drop Node 12 support :fire:

- :fire: Upgrade to npm v7
- :fire: Drop node `v12`. Only node `v14` and `v15` are supported from now on.
- 🛡️ Run the process as non-root user in production

#### Migration Howto
- Change the content of the `.nvmrc` in your project root to `15`
- Change the `engines.node` declaration in the `package.json` to `>=14` or `>=15`
- Change the docker image versions in your `Dockerfile` to `livingdocs/editor-base:14.2` or `livingdocs/editor-base:15.0`.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4256)


### Remove editor configs :fire:

- 🔥 Removed editor config `supportedBrowsers`. No replacement is provided for now. If you really need one, talk to us.
- 🔥 Removed editor config `sidePanelBehaviour`. The main navigation opens/closes on click (by ignoring double-clicks). The possibility to activate open/close on mouseenter (hover) is removed.
- 🔥 Removed dependency `bowser` (https://www.npmjs.com/package/bowser). If you use it in downstream, we suggest to replace by feature/touch input detection or adding the dependency to your downstream project

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4244)


### Remove set() hook for metadata plugins :fire:

:fire: Remove `set()` hook for metadata plugins. Use `onUpdate()` instead.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3541)


### Remove Deprecated Upload Configs :fire:

We removed a few server configs which are deprecated for a long time.

- :fire: removed `files.aws`. Use `files.storage` instead
- :fire: removed `files.public`. Use `files.publicUrl` instead
- :fire: removed `designs.bucket` and `designs.bucketPath`. Use `designs.assets.storage` instead
- :fire: removed `designs.public`. Use `designs.assets.publicUrl` instead
- :fire: removed `images.public`. Use `images.publicUrl` instead
- :fire: removed `images.bucket` and `images.bucketPath`. Use `images.storage` instead
- :fire: removed `images.upload`. Use `images.uploadRestrictions` instead
- :fire: do not support deprecated format in `images.processing.convert` anymore. Use the new format instead (see example)
  ```js
  // old format
  images.processing.convert: {pdf: 'png'}

  // new format
  convert: [{sourceFormat: 'pdf', targetFormat: 'png'}]
  ```

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3577)

### Remove Gravatar for User Avatars as Default Solution :fire:

User Avatars are now generated using initials of the user name (first letter of firstname, first letter of lastname).

Gravatar: If you want to keep using Gravatar for user avatars, you have to opt-in by setting `app.useGravatar: true` in the editor config.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4250)


### LegacyDocumentModel Getters :fire:

This change should not affect customers, but based on how deep you dived into Livingdocs document models, it could affect you.

Some writing operations of the `documentsApi` return a `LegacyDocumentModel`.
`LegacyDocumentModel.revision`, `LegacyDocumentModel.document`, `LegacyDocumentModel.metadata` and `LegacyDocumentModel.last_publication` are now getters and will :fire: throw when you try to assign a value. If you really need to assign a value, please use the new `LegacyDocumentModel.revisionEntity` or similar property.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3542)



# Deprecations

We did a cleanup for asset related server configs and moved them into the mediaLibrary feature. The old configs are still supported, but we suggest to immediately move them.

🔧  Deprecate server config `files`. Move config to server config `mediaLibrary.files`
🔧  Deprecate server config `videos`. Move config to server config `mediaLibrary.videos`

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3595)



# APIs :gift:

## Public API - Add Filters for latestPublications

Introduce more filters on `api/v1/documents/latestPublications`.

`/api/v1/documents/latestPublications`
- 🎁 Introduce `?reverse=true` to order publications in ascending order
- 🎁 Introduce `?contentTypes=regular,interview` content type filters
- 🎁 Introduce `?documentTypes=article,page` document type filters
- 🎁 Introduce `?id.gte=1&id.lte=100` range filters
Supported filters: `id.gte`, `id.gt`, `id.lte`, `id.lt`, `publishedAt.gte`, `publishedAt.gt`, `publishedAt.lte`, `publishedAt.lt`

`/api/v1/publicationEvents`
- 🎁 Introduce `?reverse` in addition to `/api/v1/publicationEvents?reverse=true`
- 🎁 Introduce `?contentTypes=regular,interview` content type filters
- 🎁 Introduce `?documentTypes=article,page` document type filters
- 🎁 Introduce `?id.gte=1&id.lte=100` range filters
Supported filters: `id.gte`, `id.gt`, `id.lte`, `id.lt`, `createdAt.gte`, `createdAt.gt`, `createdAt.lte`, `createdAt.lt`


References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3596)
* [Documentation](https://github.com/livingdocsIO/livingdocs-editor/pull/4336)

## Public API - Media Library - Add Version property

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3567)


## Public API - Document Import - Set Creation Date of Publication

Allows to import documents with a publicationDate flag which will set the creation date of a publication.

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3569)
* [Documentation](https://github.com/livingdocsIO/documentation/pull/390)


## livingdocs-server project-truncate

`livingdocs-server project-truncate -p <your-project> -y` truncates documents in Elasticsearch too (instead of only truncating Postgres documents).

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3545)




# Internal Changes

## Opt-In for Vue based metadata form rendering

References:
* [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4231)




# Other Changes

### Features

* Add `minLength`, `recommendedMinLength` and `recommendedMaxLength` to `doc-editable` directive [livingdocs-editor #4255](https://github.com/livingdocsIO/livingdocs-editor/pull/4255) :gift:
* Woodwing: Add media source example into the example server [livingdocs-server #3565](https://github.com/livingdocsIO/livingdocs-server/pull/3565) :gift:
* Auth: Sync OpenId Connect user groups on login [livingdocs-server #3563](https://github.com/livingdocsIO/livingdocs-server/pull/3563) :gift:
* Storage: Add support for storage prefix [livingdocs-server #3587](https://github.com/livingdocsIO/livingdocs-server/pull/3587) :gift:


### Improvements

* Do not use offensive project handles [livingdocs-server #3589](https://github.com/livingdocsIO/livingdocs-server/pull/3589) :gift:
* Show tasks in toolbar as soon as the content-type has a task config [livingdocs-editor #4359](https://github.com/livingdocsIO/livingdocs-editor/pull/4359) :gift:
* Configure icons for each ContentType [livingdocs-editor #4339](https://github.com/livingdocsIO/livingdocs-editor/pull/4339) :gift:

### Bugfixes

#### Security

* Prevent identity creation without a user  [livingdocs-server #3560](https://github.com/livingdocsIO/livingdocs-server/pull/3560) :beetle:
* Do not send out too many 'new device login' emails [livingdocs-server #3571](https://github.com/livingdocsIO/livingdocs-server/pull/3571) :beetle:
* Users will be able to log in even if new device emails cant be sent [livingdocs-server #3597](https://github.com/livingdocsIO/livingdocs-server/pull/3597) :beetle:
* Correctly redirect upon signup [livingdocs-editor #4232](https://github.com/livingdocsIO/livingdocs-editor/pull/4232) :gift:
* Log users in even if they dont have a default design [livingdocs-editor #4275](https://github.com/livingdocsIO/livingdocs-editor/pull/4275) :gift:

#### Editor

* Link tool
  * Make removing an existing link possible again [livingdocs-editor #4321](https://github.com/livingdocsIO/livingdocs-editor/pull/4321) :gift:
  * Improve delivery path pattern matching and handling of matching paths with nonexisting IDs [livingdocs-editor #4325](https://github.com/livingdocsIO/livingdocs-editor/pull/4325) :gift:
* Multiselect: Only allow to transform available components of a content-type [livingdocs-editor #4331](https://github.com/livingdocsIO/livingdocs-editor/pull/4331) :gift:
* Clipboard
  * Fix drag and drop of a container [livingdocs-editor #4243](https://github.com/livingdocsIO/livingdocs-editor/pull/4243) :gift:
  * Render includes when dropping a component from the clipboard [livingdocs-editor #4330](https://github.com/livingdocsIO/livingdocs-editor/pull/4330) :gift:
  * Do not insert default content when dropping a component [livingdocs-editor #4358](https://github.com/livingdocsIO/livingdocs-editor/pull/4358) :gift:
* Search Filter: Fix multiSourceSearch to use filters [livingdocs-editor #4257](https://github.com/livingdocsIO/livingdocs-editor/pull/4257) :gift:
* Editor Admin
  * Fix ordering of semantic versions in design screen [livingdocs-editor #4260](https://github.com/livingdocsIO/livingdocs-editor/pull/4260) :gift:
  * Fix group screen errors [livingdocs-editor #4226](https://github.com/livingdocsIO/livingdocs-editor/pull/4226) :gift:
  * Webhooks: fix the form layout for the event checkboxes [livingdocs-editor #4320](https://github.com/livingdocsIO/livingdocs-editor/pull/4320) :gift:
* Includes: Fix checkboxes for twitch and instagram include [livingdocs-editor #4262](https://github.com/livingdocsIO/livingdocs-editor/pull/4262) :gift:
* Show correct message when server is offline and proxiedHost is enabled [livingdocs-editor #4264](https://github.com/livingdocsIO/livingdocs-editor/pull/4264) :gift:
* Metadata
  * li-text: correctly render when `config.useAsTitle` [livingdocs-editor #4270](https://github.com/livingdocsIO/livingdocs-editor/pull/4270) :gift:
  * li-image: Crop url fix [livingdocs-editor #4348](https://github.com/livingdocsIO/livingdocs-editor/pull/4348) :gift:
  * li-image / li-poster-image: Crop handling [livingdocs-editor #4352](https://github.com/livingdocsIO/livingdocs-editor/pull/4352) :gift:
  * li-date-time-validity: Ensure date input format for all metadata fields is ISO 8601 compatible [livingdocs-editor #4356](https://github.com/livingdocsIO/livingdocs-editor/pull/4356) :gift:

#### Server

* Fix Desk-Net plugin [livingdocs-server #3547](https://github.com/livingdocsIO/livingdocs-server/pull/3547) :beetle:
* Seeding: Always reset project handle cache on every project seeding [livingdocs-server #3556](https://github.com/livingdocsIO/livingdocs-server/pull/3556) :beetle:
* Lists: Fix config schema validation [livingdocs-server #3579](https://github.com/livingdocsIO/livingdocs-server/pull/3579) :beetle:
* Indexing
  * Do not delete consumers when we can't transfer the pending messages [livingdocs-server #3581](https://github.com/livingdocsIO/livingdocs-server/pull/3581) :beetle:
  * Fix typo in xtransferexit and reduce the redis calls during xcleanup [livingdocs-server #3584](https://github.com/livingdocsIO/livingdocs-server/pull/3584) :beetle:
  * Queue Fixes [livingdocs-server #3607](https://github.com/livingdocsIO/livingdocs-server/pull/3607) :beetle:
  * Resume indexing after a process and queue got paused [livingdocs-server #3615](https://github.com/livingdocsIO/livingdocs-server/pull/3615) :beetle:
* Media Sources: Fix Unsplash plugin [livingdocs-server #3588](https://github.com/livingdocsIO/livingdocs-server/pull/3588) :beetle:
* Print: Fix crash on certificate errors [livingdocs-server #3590](https://github.com/livingdocsIO/livingdocs-server/pull/3590) :beetle:
* Copy: Copy Config Fix [livingdocs-server #3613](https://github.com/livingdocsIO/livingdocs-server/pull/3613) :beetle:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
