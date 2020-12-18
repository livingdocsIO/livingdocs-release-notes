TODO
- server until 114.0.0
- editor until 57.33.1

**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Newsletter](#newsletter)
- [Webinar](#webinar)
- [Patches](#repositories)
- [Highlights](#highlights)
- [Breaking Changes](#breaking-changes-fire)
- [APIs](#apis-gift)
- [Other Changes](#other-changes)

# Newsletter

* Newsletter: **TODO**
* Subscribe here: https://confirmsubscription.com/h/j/61B064416E79453D


# Webinar

* Recording: **TODO**
* Documentation: **TODO**

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2020-12`
`@livingdocs/editor` | `release-2020-12`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2020-12",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2020-12

### Livingdocs Server Patches
- [v114.0.6](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.6): fix(indexing): Make the redis prefix optional
- [v114.0.5](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.5): fix: handle auth errors in case of a malformed JWT
- [v114.0.4](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.4): fix: update framework version to release-2020-12
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2020-12",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2020-12

### Livingdocs Editor Patches
- [v57.33.7](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.7): fix(expired image): Rendering fixed

- Fixed visibility of inline add button when overlapping with expired image (basically inline add button is now in front of all other area components)
- Fixed text rendering in expired image badge
- [v57.33.6](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.6): fix: update framework to release-2020-12
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text





# Highlights

## Mobile - Inline Editing :tada:

With this release, we allow a user to inline add/edit components and its settings (e.g. images) in the editor with your mobile.

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3900)


## Editable Teasers :tada:

Editable teasers are embedded editable livingdocs components. Technically editable teasers are doc-includes returning livingdocs components, which can be edited like any other component. For more information read the [documentation - TODO: Beni]() and look into the [example](https://github.com/livingdocsIO/livingdocs-server/pull/3235) on the example-server.

References:
  * [Editable Teasers Editor Integration](https://github.com/livingdocsIO/livingdocs-editor/pull/3961)
  * [Base Work - Properties Panel Refactoring](https://github.com/livingdocsIO/livingdocs-editor/pull/3951)
  * [Base Work - Resolve Includes](https://github.com/livingdocsIO/livingdocs-editor/pull/3949)
  * [Example - Teaser Include on Example Server](https://github.com/livingdocsIO/livingdocs-server/pull/3235)
  * [Documentation - TODO: Beni]()


## Internal Document Links :tada:

When selecting text in the editor, the link tool in the editable toolbar allows to link to documents instead of URLs only. The input field is a combined input and detects if you want to search, or if you entered an URL.

![image](https://user-images.githubusercontent.com/821875/95599481-6ea70380-0a51-11eb-9cb5-639db68b238c.png)

- If you search, you get back a list of internal documents
- If you paste an URL that matches one of your deliveries, the link is automatically upgraded to a document reference.

References:
  * [Internal Document Links PR with Screenshots and Explanations](https://github.com/livingdocsIO/livingdocs-editor/pull/3909)
  * [Internal Document Links Extended Search](https://github.com/livingdocsIO/livingdocs-editor/pull/4027)
  * [Internal Document Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3150)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/329)


## Custom Indexes / Queue Base Work :tada:

### Base Work
To support all kind of features which need (job-)queues (now/future), we did some base work. These are the most important changes:
- Get rid of [bullmq](https://github.com/taskforcesh/bullmq)
- Introduce [Redis streams](https://github.com/livingdocsIO/livingdocs-server/pull/3224) for messaging (more control/reliability/transparency)

### Custom Indexes
Some customers want to have their customised Elasticsearch publication index to make customised search requests. The switch to Redis streams was necessary to
make custom indexes possible. Why you could need a custom index and how to setup one, can be found [here](https://github.com/livingdocsIO/livingdocs/pull/328).

References:
  * [Base Work - Queue Refactoring - Part I](https://github.com/livingdocsIO/livingdocs-server/pull/3187)
  * [Base Work - Queue Refactoring - Part II](https://github.com/livingdocsIO/livingdocs-server/pull/3193)
  * [Base Work - Redis Streams](https://github.com/livingdocsIO/livingdocs-server/pull/3224)
  * [Visualize Redis Queue Infos - Editor](https://github.com/livingdocsIO/livingdocs-editor/pull/3924)
  * [Visualize Redis Queue Infos - Server](https://github.com/livingdocsIO/livingdocs-server/pull/3193)
  * [Custom Elasticsearch Index](https://github.com/livingdocsIO/livingdocs-server/pull/3185)
  * [Custom Elasticsearch Index - Documentation](https://github.com/livingdocsIO/livingdocs/pull/328)
  * [Indexing Cleanup](https://github.com/livingdocsIO/livingdocs-server/pull/3284)


## Videos :tada:

We introduce videos in Livingdocs with these abilities:

- upload videos and set metadata in media library
- upload videos and set metadata in editor via drag + drop / upload button
- import videos via public API
- Add project configuration for mediaVideo MediaType
- Add new directive `doc-video` in a livingdocs design

References:
  * [Editor PR with Screenshots](https://github.com/livingdocsIO/livingdocs-editor/pull/3957)
  * [Editor PR with Improvements (drag+drop from filesystem)](https://github.com/livingdocsIO/livingdocs-editor/pull/3989)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3234)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/337)


## Cloudinary Storage Support :tada:

Beside Amazon S3 we introduced Cloudinary as storage. Look into the [documentation - TODO: Marc]() for instructions.

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4023)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3270)
  * [Documentation - TODO: Marc]()


## Migrations from Referenced to Embedded Design via UI :tada:

More and more customers switch from referenced to embedded designs. To support them we added a flag in the operations screen
of the editor to migrate all documents from a reference to an embedded design.

References:
  * [Editor PR with Screenots and Explanation](https://github.com/livingdocsIO/livingdocs-editor/pull/3932)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3208)
  * [Documentation - TODO: Gabriel](https://github.com/livingdocsIO/livingdocs/pull/334)


## More Secure Authentication Workflow :tada:

We worked on the security for the user authentication in Livingdocs. Some improvements are:

- Increased security for the accessTokens
- if an accessToken is stolen, it can't be used without a valid client cookie
- accessTokens can't renew themselves anymore
- an accessToken is bound to a valid client and session

For more information, read [here](https://github.com/livingdocsIO/livingdocs-server/pull/3225).

References:
  * [Server PR Part I](https://github.com/livingdocsIO/livingdocs-server/pull/3225)
  * [Server PR Part II](https://github.com/livingdocsIO/livingdocs-server/pull/3282)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3952)


## Airship Integration for Push Notifications :tada:

We integrated Airship for push notifications.

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3975)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3231)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/340)



# Breaking Changes :fire:

## Migrate the database :fire:

It's a simple/fast migration with no expected data losses.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 142-add-legacy-design-name.js
#   rename document_migrations.design_name to target_design_name
# migration - 143-drop-unused-postgres-extensions.js
#   drop unused uuid-ossp extension
# migration - 144-add-missing-primary-keys.js
#   add missing primary keys to tables to support replication better
# migration - 145-document-content-types.js
#   introduce document_content_types table to support migrations better in the future
# migration - 146-add-metadata-id-to-revisions.js
#   add document_revisions.metadata_id to support metadata to document/publication relations better in the future
# migration - 147-add-user-sessions.js
#   add user_sessions table to support new auth workflow
livingdocs-server migrate up
```

## Drop Support for Elasticsearch < 6.8.5 :fire:

:fire: The support for Elasticsearch versions < 6.8.5 has been dropped. Please upate your Elasticsearch cluster.

TODO: Ralph - write a guide how to update to the newest version on a productive system (without downtime)

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3275)

## Migration to Redis Streams :fire:

- :fire: Existing messages from `bull` won't be processed anymore.
- :fire: If you had pending index or imports, you'll need to restart them. Our whole setup already supported retries everywhere except in the importer of the public api. It's probably best if you re-trigger the imports after deployment.
- ❌ Removed bull dashboard and replaced it with an operations screen in the admin interface of the editor.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3224)

## Slug Metadata in Slug Routing Pattern :fire:

If you activated the routing feature and if you are using a route pattern containing `:slug` and at the same time you have a metadata property with the handle `slug` the behavior will change in such a way that the route pattern for `:slug` will be built out of the `slug` metadata property value and not the document title. In most cases this is what you want. If it is not, you can rename the handle of your existing slug metadata property to prevent clashes.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3227)

## DocumentsApi - Removed functions :fire:

- :fire: Removed `DocumentEntity.find` and `DocumentEntity.findById` methods, please use the official apis
- :fire: Removed `RevisionEntity.find` and `RevisionEntity.findById` methods, please use the official apis
- :fire: Changed parameters of `documentApi.getLocks` from `(documentId)` to `({projectId, documentId})`, so we can save a few roundtrips to check whether a user is allowed to access the document.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3237)

## S3 Storage Default :fire:

:fire: The S3 default changed from `{ACL: 'public-read'}` to `undefined` - it now uses the bucket ACL-defaults.

#### How to revert to the behaviour before the release :fire:
To restore the behaviour you can explicitly pass the `{ACL: 'public-read'}` in `(images|files).storage.config.params.ACL`

```js
storage: {
  strategy: 's3',
  config: {
    bucket: 'li-bucket-dev',
    region: 'eu-central-1',
    accessKeyId: 'secret',
    secretAccessKey: 'secret',
    params: {
      ACL: 'public-read' // <--------- add this to go back to the old behavior
    }
  }
}
```

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3262)

## DocumentRelationApi - Changed Params :fire:

🔥 Changed params on `documentRelationApi.setDocumentEmbedRefrences` from `(documentVersion)` to `({documentVersion, trx})`

NOTE: The new param `trx` is optional and only necessary if you want to call within a transactional context. If you do pass it, you are responsible to call `trx.commit` or `trx.rollback` when you're done.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3259)

## Index Feature - Removed publicationTransformModule :fire:

- 🔥 Remove server config option search.indexer.publicationTransformModule
- 🔥 Remove parameter publication-transform-module in livingdocs-server es-publication-reindex task

Note: This change should have no consequences for customers.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3222)

## Index Feature - Removed/Renamed Functions :fire:

- 🔥 Removed `req.accessToken` from all requests. Please migrate to `req.verifiedToken.bearerToken`
- 🔥 Removed `searchManager.putDocument`. Please migrate to `indexingApi.addJob` that executes the same method internally

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3187)

## Editor CSS Class Renamings :fire:

:fire: If you've done CSS modifications based on the original upstream classes in the editor please look into this PR. We did a lot of small refactorings/renamings.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4015)


# APIs :gift:

TODO: Ralph - overhaul API descriptions

## Public API - Added Import Endpoint for MediaLibrary :gift:

The public API contains a new endpoint for importing a `MediaLibrary`.

New endpoint:
- `POST /api/v1/import/mediaLibrary`

References:
  * Documentation - 'https://your-editor.com/public-api'
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3895)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3152)


## Public API - Added MediaLibrary Endpoint :gift:

The public API contains a new endpoint for updating metadata of a `MediaLibrary` entry.

New endpoint:
- `PATCH /api/v1/mediaLibrary/:id`

References:
  * Documentation - 'https://your-editor.com/public-api'
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4014)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3267)


## Public API - Added Document List Endpoints :gift:

The public API contains new endpoints for document lists.

New endpoints:
- `GET /api/v1/document-lists`  Search endpoint for document lists
- `GET /api/v1/document-lists/:id` Get a document list by :id

References:
  * Documentation - 'https://your-editor.com/public-api'
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3956)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3226)


## Public API - Added Import Endpoint for Videos :gift:

New endpoints:
- `POST api/v1/import/videos` Import videos in Livingdocs

References:
  * Documentation - 'https://your-editor.com/public-api'
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3234)






## Public API - Beta Endpoints for publications :gift:

We added a new base endpoint ...`/api/beta` for...

New endpoints:
- `GET /api/beta/documents/:documentId/latestPublication`
- `GET /api/beta/documents/latestPublications`

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3254)



## Server Events API - Added mediaLibrary Events :gift:


* v111.2.0 feat(media library): emit events mediaLibraryEntry.create, .update, .archive [livingdocs-server #3255](https://github.com/livingdocsIO/livingdocs-server/pull/3255) :gift:
* doc: https://github.com/livingdocsIO/livingdocs/pull/345


# Other Changes

### Security

* Registration: Do not allow long usernames or // in a username [livingdocs-server #3257](https://github.com/livingdocsIO/livingdocs-server/pull/3257) :gift:
* Registration: Escape user input in email html [livingdocs-server #3256](https://github.com/livingdocsIO/livingdocs-server/pull/3256) :gift:

### Design

* Document reference polish
  * Part I  [livingdocs-editor #3897](https://github.com/livingdocsIO/livingdocs-editor/pull/3897) :gift:
  * Part II [livingdocs-editor #3950](https://github.com/livingdocsIO/livingdocs-editor/pull/3950) :gift:
* Use consistent button styles on metadata screen [livingdocs-editor #3918](https://github.com/livingdocsIO/livingdocs-editor/pull/3918) :gift:
* Improve conflict mode [livingdocs-editor #3927](https://github.com/livingdocsIO/livingdocs-editor/pull/3927) :gift:
* Overhauled Link-Buttons [livingdocs-editor #3982](https://github.com/livingdocsIO/livingdocs-editor/pull/3982) :gift:
* Refactor: Remove Atomic Design [livingdocs-editor #4012](https://github.com/livingdocsIO/livingdocs-editor/pull/4012) :gift:
* A huge amount of design fixes for release-2020-12 [livingdocs-editor #4015](https://github.com/livingdocsIO/livingdocs-editor/pull/4015) :gift:
* Updated mail templates [livingdocs-server #3203](https://github.com/livingdocsIO/livingdocs-server/pull/3203) :gift:

### Improvements

#### Editor

* Login: Show login buttons for all auth providers [livingdocs-editor #3934](https://github.com/livingdocsIO/livingdocs-editor/pull/3934) :gift:
* Dashboard: Scroll to last article [livingdocs-editor #4006](https://github.com/livingdocsIO/livingdocs-editor/pull/4006) :gift:
* Operation Screen
  * Migrate server operations screen to websockets [livingdocs-server #3192](https://github.com/livingdocsIO/livingdocs-server/pull/3192) :gift:
  * Improve import jobs log in editor [livingdocs-server #3202](https://github.com/livingdocsIO/livingdocs-server/pull/3202) :gift:
* Allow to register icons in downstream [livingdocs-editor #3925](https://github.com/livingdocsIO/livingdocs-editor/pull/3925) :gift:

#### Server

* Media services improvements [livingdocs-server #3243](https://github.com/livingdocsIO/livingdocs-server/pull/3243) :gift:
* Proxy: Add support for proxying websockets [livingdocs-editor #3905](https://github.com/livingdocsIO/livingdocs-editor/pull/3905) :gift:
* APIs: Serve Cache-Control header in authenticated requests [livingdocs-server #3280](https://github.com/livingdocsIO/livingdocs-server/pull/3280) :gift:
* Migrations: Support `migrateAsync` method on migration files [livingdocs-server #3204](https://github.com/livingdocsIO/livingdocs-server/pull/3204) :gift:
* DataSources: Support documentId in params [livingdocs-editor #3896](https://github.com/livingdocsIO/livingdocs-editor/pull/3896) :gift:
* Postgres:
  * Add missing primary keys to support logical replication [livingdocs-server #3236](https://github.com/livingdocsIO/livingdocs-server/pull/3236) :gift:
  * Introduce a `document_content_types` table to keep the media types similar [livingdocs-server #3238](https://github.com/livingdocsIO/livingdocs-server/pull/3238) :gift:
* Example Server: Add Twitch include example [livingdocs-server #3246](https://github.com/livingdocsIO/livingdocs-server/pull/3246) :gift:
* Notifications: Pass server error messages to li-notifications [livingdocs-editor #3929](https://github.com/livingdocsIO/livingdocs-editor/pull/3929) :gift:

### Bugfixes

* Metadata: Fix metadata save trigger [livingdocs-editor #3967](https://github.com/livingdocsIO/livingdocs-editor/pull/3967) :beetle:
* MediaLibrary
  * Fix drop behavior for galleries [livingdocs-editor #3884](https://github.com/livingdocsIO/livingdocs-editor/pull/3884) :beetle:
  * Correctly handle drops in all browsers [livingdocs-editor #3878](https://github.com/livingdocsIO/livingdocs-editor/pull/3878) :beetle:
* Filter: Allow strings for dateRange query [livingdocs-editor #3941](https://github.com/livingdocsIO/livingdocs-editor/pull/3941) :beetle:
* Public API: Fix public API docs [livingdocs-editor #3976](https://github.com/livingdocsIO/livingdocs-editor/pull/3976) :beetle:
* Operation Screen
  * Correctly indicate total users [livingdocs-editor #4002](https://github.com/livingdocsIO/livingdocs-editor/pull/4002) :beetle:
  * Fix Add Member Screen for users that are already in a group [livingdocs-editor #4004](https://github.com/livingdocsIO/livingdocs-editor/pull/4004) :beetle:
  * Display error message during user create on admin screen [livingdocs-editor #4007](https://github.com/livingdocsIO/livingdocs-editor/pull/4007) :beetle:
* Directives:
  * Don't show UI elements in non-interactive iframe view [livingdocs-editor #4008](https://github.com/livingdocsIO/livingdocs-editor/pull/4008) :beetle:
  * Set clean data from paramsSchema form instead of reactive vue objects to the include directive [livingdocs-editor #4018](https://github.com/livingdocsIO/livingdocs-editor/pull/4018) :beetle:
* Fix focus reset and error log in embedded teaser [livingdocs-editor #4028](https://github.com/livingdocsIO/livingdocs-editor/pull/4028) :beetle:
* Desknet: Fix Desk-Net Plugin for embedded designs [livingdocs-server #3183](https://github.com/livingdocsIO/livingdocs-server/pull/3183) :beetle:
* Imatrics: Fix tag slugging [livingdocs-server #3188](https://github.com/livingdocsIO/livingdocs-server/pull/3188) :beetle:
* Includes: Allow `ui.label` for paramsSchema entries [livingdocs-server #3239](https://github.com/livingdocsIO/livingdocs-server/pull/3239) :beetle:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
