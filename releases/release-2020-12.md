
TODO
- server until 113.0.0
- editor until 57.29.0

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
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text





# Highlights

## EXAMPLE :tada:

...Description...

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/2143)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/246)




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

### Features

* ... :gift:

### Design

* ... :gift:

### Improvements

* ... :gift:

### Bugfixes

* ... :beetle:



EDIToooooooooooooooooooooooooorrrrrrrrrrrr
* v57.29.0 feat(dashboard): Scroll to last article [livingdocs-editor #4006](https://github.com/livingdocsIO/livingdocs-editor/pull/4006) :gift:
* v57.28.14 Cloudinary Support [livingdocs-editor #4023](https://github.com/livingdocsIO/livingdocs-editor/pull/4023) :gift:
* v57.28.13 [Bug Fix] Documents embedded in references are correctly displayed on the publish screen [livingdocs-editor #4019](https://github.com/livingdocsIO/livingdocs-editor/pull/4019) :gift:
* v57.28.12 fix(includes): set clean data from paramsSchema form instead of reactive vue objects to the include directive [livingdocs-editor #4018](https://github.com/livingdocsIO/livingdocs-editor/pull/4018) :gift:
* v57.28.11 Restore vue eslint [livingdocs-editor #4017](https://github.com/livingdocsIO/livingdocs-editor/pull/4017) :gift:
* v57.28.10 Atomic Removal [livingdocs-editor #4012](https://github.com/livingdocsIO/livingdocs-editor/pull/4012) :gift:
* v57.28.9  show merge error for tasks in task panel v2 [livingdocs-editor #4009](https://github.com/livingdocsIO/livingdocs-editor/pull/4009) :gift:
* v57.28.8 Fix mediatype hardcodes [livingdocs-editor #3989](https://github.com/livingdocsIO/livingdocs-editor/pull/3989) :gift:
* v57.28.7 fix(editor): don't show UI elements in non-interactive iframe view [livingdocs-editor #4008](https://github.com/livingdocsIO/livingdocs-editor/pull/4008) :gift:
* v57.28.6 fix(admin): display error message on error during user create on admin screen [livingdocs-editor #4007](https://github.com/livingdocsIO/livingdocs-editor/pull/4007) :gift:
* v57.28.5 fix(websockets): correctly check for encrypted connection in websocket upgrade request [livingdocs-editor #4005](https://github.com/livingdocsIO/livingdocs-editor/pull/4005) :gift:
* v57.28.4 Fix Add Member Screen for Users that are already in a Group - master [livingdocs-editor #4004](https://github.com/livingdocsIO/livingdocs-editor/pull/4004) :gift:
* v57.28.3 fix: correctly indicate total users [livingdocs-editor #4002](https://github.com/livingdocsIO/livingdocs-editor/pull/4002) :gift:
* v57.28.2 fix(embeds): Avoid transforming free-html content [livingdocs-editor #3997](https://github.com/livingdocsIO/livingdocs-editor/pull/3997) :gift:
* v57.28.1 Correctly load a user's profile [livingdocs-editor #3998](https://github.com/livingdocsIO/livingdocs-editor/pull/3998) :gift:
* v57.28.0 fix(includes): resolve includes from  viewManager [livingdocs-editor #3949](https://github.com/livingdocsIO/livingdocs-editor/pull/3949) :gift:
* v57.27.13 Limit the users list in the admin screen to 500 entries [livingdocs-editor #3994](https://github.com/livingdocsIO/livingdocs-editor/pull/3994) :gift:
* v57.27.12 Twitch Include [livingdocs-editor #3988](https://github.com/livingdocsIO/livingdocs-editor/pull/3988) :gift:

* v57.27.10 improve auth flows with cookies [livingdocs-editor #3952](https://github.com/livingdocsIO/livingdocs-editor/pull/3952) :gift:
* v57.27.9 fix(metadata updater): don't log error when a different object with the same values is set [livingdocs-editor #3986](https://github.com/livingdocsIO/livingdocs-editor/pull/3986) :gift:
* v57.27.8 Fix char counter [livingdocs-editor #3984](https://github.com/livingdocsIO/livingdocs-editor/pull/3984) :gift:
* v57.27.7 Link-Buttons [livingdocs-editor #3982](https://github.com/livingdocsIO/livingdocs-editor/pull/3982) :gift:
* v57.27.6 fix conflict highlights after resizing [livingdocs-editor #3978](https://github.com/livingdocsIO/livingdocs-editor/pull/3978) :gift:
* v57.27.5 Fix public API docs [livingdocs-editor #3976](https://github.com/livingdocsIO/livingdocs-editor/pull/3976) :gift:
* v57.27.4 In defaultSearchEntityLabel remove the s [livingdocs-editor #3970](https://github.com/livingdocsIO/livingdocs-editor/pull/3970) :gift:
* v57.27.3 Fix metadata save trigger [livingdocs-editor #3967](https://github.com/livingdocsIO/livingdocs-editor/pull/3967) :gift:
* v57.27.2 fix(embeds): do not add padding bottom unless it's a responsive conta… [livingdocs-editor #3965](https://github.com/livingdocsIO/livingdocs-editor/pull/3965) :gift:
* v57.27.1 fix video upload [livingdocs-editor #3963](https://github.com/livingdocsIO/livingdocs-editor/pull/3963) :gift:

* v57.26.1 fix(properties): correctly set the component option value or empty string from properties panel [livingdocs-editor #3962](https://github.com/livingdocsIO/livingdocs-editor/pull/3962) :gift:
* v57.26.0 (Editable Teasers): Properties Panel Refactoring [livingdocs-editor #3951](https://github.com/livingdocsIO/livingdocs-editor/pull/3951) :gift:

* v57.25.5 fix(iframes): pasting iframes [livingdocs-editor #3953](https://github.com/livingdocsIO/livingdocs-editor/pull/3953) :gift:
* v57.25.4 Document Reference Polish [livingdocs-editor #3950](https://github.com/livingdocsIO/livingdocs-editor/pull/3950) :gift:
* v57.25.3 trackjs doesn't accept undefined as userId [livingdocs-editor #3946](https://github.com/livingdocsIO/livingdocs-editor/pull/3946) :gift:
* v57.25.2 fix: tasks in history UI [livingdocs-editor #3943](https://github.com/livingdocsIO/livingdocs-editor/pull/3943) :gift:
* v57.25.1 allow strings for dateRange query [livingdocs-editor #3941](https://github.com/livingdocsIO/livingdocs-editor/pull/3941) :gift:
* v57.25.0 Pass server error messages to li-notifications [livingdocs-editor #3929](https://github.com/livingdocsIO/livingdocs-editor/pull/3929) :gift:
* v57.24.4 fix(embeds): add addResponsiveContainer config [livingdocs-editor #3935](https://github.com/livingdocsIO/livingdocs-editor/pull/3935) :gift:
* v57.24.3 Show the login buttons for all the auth providers using a ui config [livingdocs-editor #3934](https://github.com/livingdocsIO/livingdocs-editor/pull/3934) :gift:

* v57.24.1 improve conflict mode [livingdocs-editor #3927](https://github.com/livingdocsIO/livingdocs-editor/pull/3927) :gift:
* v57.24.0 Allow to register icons downstream [livingdocs-editor #3925](https://github.com/livingdocsIO/livingdocs-editor/pull/3925) :gift:
* v57.23.1 fix: guard from undefined in include sidebars [livingdocs-editor #3920](https://github.com/livingdocsIO/livingdocs-editor/pull/3920) :gift:


* v57.22.6 Visualize Redis Queue Infos [livingdocs-editor #3924](https://github.com/livingdocsIO/livingdocs-editor/pull/3924) :gift:
* v57.22.5 Editor autosave breaks if language is reset on metadata [livingdocs-editor #3922](https://github.com/livingdocsIO/livingdocs-editor/pull/3922) :gift:
* v57.22.4 fix: use consistent button styles on metadata screen [livingdocs-editor #3918](https://github.com/livingdocsIO/livingdocs-editor/pull/3918) :gift:
* v57.22.3 fix: allow to sort channels [livingdocs-editor #3908](https://github.com/livingdocsIO/livingdocs-editor/pull/3908) :gift:

* v57.22.1 fix(dashboards): show contentType label instead of handle [livingdocs-editor #3907](https://github.com/livingdocsIO/livingdocs-editor/pull/3907) :gift:
* v57.22.0 Document Reference Polish [livingdocs-editor #3897](https://github.com/livingdocsIO/livingdocs-editor/pull/3897) :gift:
* v57.20.0 Add support for proxying websockets [livingdocs-editor #3905](https://github.com/livingdocsIO/livingdocs-editor/pull/3905) :gift:
* v57.19.6 Image upload improvements [livingdocs-editor #3861](https://github.com/livingdocsIO/livingdocs-editor/pull/3861) :gift:
* v57.19.5 Inline Cahr Counter [livingdocs-editor #3898](https://github.com/livingdocsIO/livingdocs-editor/pull/3898) :gift:
* v57.19.4 Support documentId in dataSources [livingdocs-editor #3896](https://github.com/livingdocsIO/livingdocs-editor/pull/3896) :gift:
* v57.19.2 fix(media-library-dnd): fix drop behavior for galleries [livingdocs-editor #3884](https://github.com/livingdocsIO/livingdocs-editor/pull/3884) :gift:
* v57.19.1 Correctly handle drops from media library in all browsers [livingdocs-editor #3878](https://github.com/livingdocsIO/livingdocs-editor/pull/3878) :gift:






Bugfixes
* v104.3.3 Fix Desk-Net Plugin for embedded designs [livingdocs-server #3183](https://github.com/livingdocsIO/livingdocs-server/pull/3183) :gift:
* v105.0.1 fix(imatrics): fix tag slugging [livingdocs-server #3188](https://github.com/livingdocsIO/livingdocs-server/pull/3188) :gift:
* * v109.0.2 fix(include services): allow ui.label for paramsSchema entries [livingdocs-server #3239](https://github.com/livingdocsIO/livingdocs-server/pull/3239) :gift:

Improvements
* v105.1.0 Migrate server operations screen to websockets [livingdocs-server #3192](https://github.com/livingdocsIO/livingdocs-server/pull/3192) :gift:
* Support `migrateAsync` method on migration files [livingdocs-server #3204](https://github.com/livingdocsIO/livingdocs-server/pull/3204) :gift:
* * v105.2.1 Improve import jobs log in Editor [livingdocs-server #3202](https://github.com/livingdocsIO/livingdocs-server/pull/3202) :gift:
* Postgres: Add missing primary keys to support logical replication [livingdocs-server #3236](https://github.com/livingdocsIO/livingdocs-server/pull/3236) :gift:
* * v109.0.1 Introduce a document_content_types table to keep the media types similar [livingdocs-server #3238](https://github.com/livingdocsIO/livingdocs-server/pull/3238) :gift:
* * v110.1.0 Twitch Include [livingdocs-server #3246](https://github.com/livingdocsIO/livingdocs-server/pull/3246) :gift:

Security:
* * Registration: Do not allow long usernames or // in a username [livingdocs-server #3257](https://github.com/livingdocsIO/livingdocs-server/pull/3257) :gift:
* * v110.1.2 Escape user input in email html [livingdocs-server #3256](https://github.com/livingdocsIO/livingdocs-server/pull/3256) :gift:

Design
* Updated mail templates [livingdocs-server #3203](https://github.com/livingdocsIO/livingdocs-server/pull/3203) :gift:


BIG FEATURES
--------------------------------

* (breaking) v110.0.0 Improve auth flows with cookies [livingdocs-server #3225](https://github.com/livingdocsIO/livingdocs-server/pull/3225) :gift:
--> add some ads to show that the security is now much better

airship
* v57.27.11 airship integration for push notifications  [livingdocs-editor #3975](https://github.com/livingdocsIO/livingdocs-editor/pull/3975) :gift:
* v109.1.0 airship integration for push notifications [livingdocs-server #3231](https://github.com/livingdocsIO/livingdocs-server/pull/3231) :gift:

Videos in Media Library
* v108.1.0 Add video type [livingdocs-server #3234](https://github.com/livingdocsIO/livingdocs-server/pull/3234) :gift:
* * v57.27.0 Add video type [livingdocs-editor #3957](https://github.com/livingdocsIO/livingdocs-editor/pull/3957) :gift:

Allow Migration from Reference to Embedded Design
* v57.24.2 Allow migration from reference to embedded design [livingdocs-editor #3932](https://github.com/livingdocsIO/livingdocs-editor/pull/3932) :gift:
* v105.3.2 Allow migration from reference to embedded design [livingdocs-server #3208](https://github.com/livingdocsIO/livingdocs-server/pull/3208) :gift:

Indexing
--------
* v111.0.0 Elasticsearch Custom Index [livingdocs-server #3185](https://github.com/livingdocsIO/livingdocs-server/pull/3185) :gift:
* --- doc: https://github.com/livingdocsIO/livingdocs/pull/328
* (breaking change!) v105.0.0 Queue Refactoring Preparations [livingdocs-server #3187](https://github.com/livingdocsIO/livingdocs-server/pull/3187) :gift:
* (breaking) v106.0.0 Remove publicationTransformModule option in indexing feature [livingdocs-server #3222](https://github.com/livingdocsIO/livingdocs-server/pull/3222) :gift:
* (breaking) v108.0.0 Migrate to Redis Streams [livingdocs-server #3224](https://github.com/livingdocsIO/livingdocs-server/pull/3224) :gift:
## 🔥  BREAKING CHANGES
- Existing messages from `bull` won't be processed anymore.
- If you had pending index or imports, you'll need to restart them in some kind. Our whole setup already supported retries everywhere except in the importer of the public api. It's probably best if you re-trigger the imports after deployment.
- ❌  We removed the bull dashboard and replaced it with an operations screen in the admin interface of the editor.


Internal Document Links
Documentation: https://github.com/livingdocsIO/livingdocs/pull/329
* v57.23.0 Internal Document Links: link selected text to internal documents [livingdocs-editor #3909](https://github.com/livingdocsIO/livingdocs-editor/pull/3909) :gift:
* v105.3.0 internal document links: add deliveries config and document reference extraction [livingdocs-server #3150](https://github.com/livingdocsIO/livingdocs-server/pull/3150) :gift:





Unclear---------
* v109.1.1 Media services [livingdocs-server #3243](https://github.com/livingdocsIO/livingdocs-server/pull/3243) :gift:
  - Q: https://github.com/livingdocsIO/livingdocs-server/pull/3243#issuecomment-746328416
  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
