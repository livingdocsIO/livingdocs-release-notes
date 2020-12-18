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
- [Deprecations](#deprecations)
- [APIs](#apis-gift)
- [Internal Changes](#internal-changes)
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
- [v57.33.6](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.6): fix: update framework to release-2020-12
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text





# Highlights


Edit/Add components/settings on mobile
* v57.31.0 enable Inline add of components and make UI usable for mobile [livingdocs-editor #3900](https://github.com/livingdocsIO/livingdocs-editor/pull/3900) :gift:



Cloudinary Support
* v57.28.14 Cloudinary Support [livingdocs-editor #4023](https://github.com/livingdocsIO/livingdocs-editor/pull/4023) :gift:
* https://github.com/livingdocsIO/livingdocs-server/pull/3270


Editable Teasers
* v57.26.0 (Editable Teasers): Properties Panel Refactoring [livingdocs-editor #3951](https://github.com/livingdocsIO/livingdocs-editor/pull/3951) :gift:
* * prep ticket - * v57.28.0 fix(includes): resolve includes from  viewManager [livingdocs-editor #3949](https://github.com/livingdocsIO/livingdocs-editor/pull/3949) :gift:
* v57.30.0 Editable Teasers [livingdocs-editor #3961](https://github.com/livingdocsIO/livingdocs-editor/pull/3961) :gift:
* v113.2.0 (example server) teaser include components examples [livingdocs-server #3235](https://github.com/livingdocsIO/livingdocs-server/pull/3235) :gift:


Security - new auth workflow
* (breaking) v110.0.0 Improve auth flows with cookies [livingdocs-server #3225](https://github.com/livingdocsIO/livingdocs-server/pull/3225) :gift:
* * v57.27.10 improve auth flows with cookies [livingdocs-editor #3952](https://github.com/livingdocsIO/livingdocs-editor/pull/3952) :gift:
--> add some ads to show that the security is now much better
* v114.0.0 Support project token rotation on the /auth/me endpoint [livingdocs-server #3282](https://github.com/livingdocsIO/livingdocs-server/pull/3282) :gift:

airship
* v57.27.11 airship integration for push notifications  [livingdocs-editor #3975](https://github.com/livingdocsIO/livingdocs-editor/pull/3975) :gift:
* v109.1.0 airship integration for push notifications [livingdocs-server #3231](https://github.com/livingdocsIO/livingdocs-server/pull/3231) :gift:

Videos in Media Library
* v108.1.0 Add video type [livingdocs-server #3234](https://github.com/livingdocsIO/livingdocs-server/pull/3234) :gift:
* * v57.27.0 Add video type [livingdocs-editor #3957](https://github.com/livingdocsIO/livingdocs-editor/pull/3957) :gift:
* * v57.28.8 Drag + Drop Videos from Filesystem [livingdocs-editor #3989](https://github.com/livingdocsIO/livingdocs-editor/pull/3989) :gift:

Allow Migration from Reference to Embedded Design
* v57.24.2 Allow migration from reference to embedded design [livingdocs-editor #3932](https://github.com/livingdocsIO/livingdocs-editor/pull/3932) :gift:
* v105.3.2 Allow migration from reference to embedded design [livingdocs-server #3208](https://github.com/livingdocsIO/livingdocs-server/pull/3208) :gift:

Indexing
--------
Improve the redis queue UI
* v57.22.6 Visualize Redis Queue Infos [livingdocs-editor #3924](https://github.com/livingdocsIO/livingdocs-editor/pull/3924) :gift:
  * https://github.com/livingdocsIO/livingdocs-server/pull/3193

* --- doc: https://github.com/livingdocsIO/livingdocs/pull/328
* (breaking change!) v105.0.0 Queue Refactoring Preparations [livingdocs-server #3187](https://github.com/livingdocsIO/livingdocs-server/pull/3187) :gift:
* (breaking) v106.0.0 Remove publicationTransformModule option in indexing feature [livingdocs-server #3222](https://github.com/livingdocsIO/livingdocs-server/pull/3222) :gift:
* (breaking) v108.0.0 Migrate to Redis Streams [livingdocs-server #3224](https://github.com/livingdocsIO/livingdocs-server/pull/3224) :gift:
* * v113.3.0 Indexing and job queue cleanup [livingdocs-server #3284](https://github.com/livingdocsIO/livingdocs-server/pull/3284) :gift:
* * v111.0.0 Elasticsearch Custom Index [livingdocs-server #3185](https://github.com/livingdocsIO/livingdocs-server/pull/3185) :gift:
## 🔥  BREAKING CHANGES
- Existing messages from `bull` won't be processed anymore.
- If you had pending index or imports, you'll need to restart them in some kind. Our whole setup already supported retries everywhere except in the importer of the public api. It's probably best if you re-trigger the imports after deployment.
- ❌  We removed the bull dashboard and replaced it with an operations screen in the admin interface of the editor.


Internal Document Links
Documentation: https://github.com/livingdocsIO/livingdocs/pull/329
* v57.23.0 Internal Document Links: link selected text to internal documents [livingdocs-editor #3909](https://github.com/livingdocsIO/livingdocs-editor/pull/3909) :gift:
* v105.3.0 internal document links: add deliveries config and document reference extraction [livingdocs-server #3150](https://github.com/livingdocsIO/livingdocs-server/pull/3150) :gift:
* * v57.32.0 Internal Text Links: Extended Search [livingdocs-editor #4027](https://github.com/livingdocsIO/livingdocs-editor/pull/4027) :gift:





# Breaking Changes :fire:

## Migrate the database

- Expected duration?
- Possible data losses?
- Is it a simple migration? (fast/easy downgradable)

```sh
# run grunt migrate to update to the newest database scheme
# migration - 111-add-comments-table.js
#   create comments table + add events to the stream_events_types table
livingdocs-server migrate up
```

* (breaking) Use slug metadata in slug routing pattern if available [livingdocs-server #3227](https://github.com/livingdocsIO/livingdocs-server/pull/3227) :gift:

* (breaking) v109.0.0 Remove unused DocumentEntity and RevisionEntity methods [livingdocs-server #3237](https://github.com/livingdocsIO/livingdocs-server/pull/3237) :gift:


* (breaking) v112.0.0 Change S3 ACL default | Rotate S3-SES Token | update docker compose file [livingdocs-server #3262](https://github.com/livingdocsIO/livingdocs-server/pull/3262) :gift:
* -> uses now ACL default, before public-read

* v112.2.1 Add minimal Elasticsearch version check (v 6.8.5) [livingdocs-server #3275](https://github.com/livingdocsIO/livingdocs-server/pull/3275) :gift:
* -> elastic 6.8.5 is now mandatory


* v113.0.0 Fix document import for transactional consistency [livingdocs-server #3259](https://github.com/livingdocsIO/livingdocs-server/pull/3259) :gift:


breaking? check it - * v57.29.1 Design Release Fixes 2020 12 [livingdocs-editor #4015](https://github.com/livingdocsIO/livingdocs-editor/pull/4015) :gift:






# Deprecations




# APIs :gift:

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




# Internal Changes




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
