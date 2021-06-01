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
* Postgres 9.6 (Deprecate Postgres 9 and 10)
* Elasticsearch 6.x
* Redis 5
* Base Docker Images
  * livingdocs-server: `livingdocs/server-base:14.3`
  * livingdocs-editor: `livingdocs/editor-base:14.3`

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
- [v135.1.16](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.16): fix(file-upload): Do not handle files as strings when calculating the byte size
- [v135.1.15](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.15): fix(search): Invoke search requests against elasticsearch with the correct publication index
- [v135.1.14](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.14): test(sitemaps): use datefns instead of magic strings
- [v135.1.13](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.13): fix(files): Fix exposed `files.publicUrl` in `/serverConfiguration` endpoint

We're also introducing the `mediaLibrary` config, so we can remove the old keys already in the next version
- [v135.1.12](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.12): fix(import): Delay media indexing and notifications
- [v135.1.11](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.11): chore: Do not fallback to an empty array for the `documentVersion.content` getter
- [v135.1.10](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.10): fix(imatrics): Fix typos in the imatrics implementation that got introduced during the introduction of the new DocumentVersion getters
- [v135.1.9](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.9): fix(indexing): Fix channelId comparison in live indexing
- [v135.1.8](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v135.1.8): Group projection: add archived to return object



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
- [v67.6.16](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v67.6.16): chore: Upgrade nzz and bluewin tests to node 16
- [v67.6.15](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v67.6.15): chore: fix shaky cypress
- [v67.6.14](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v67.6.14): fix(media-library): Fix context menu download link
- [v67.6.13](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v67.6.13): fix(css): Load the fonts only once
- [v67.6.12](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v67.6.12): chore: use userInfoService and add ignoreArchived
- [v67.6.11](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v67.6.11): fix(media upload): make cancelling a single upload in the upload dialog work again
- [v67.6.10](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v67.6.10): fix(media library): don't show upload dialog for uploads without required metadata
- [v67.6.9](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v67.6.9): Upgrade fastify-reply-from to get rid of deprecation message with node 16




# Highlights

## Document Import between Projects (Drag + Drop)

Allows to export/import a document via drag + drop (only between 2 projects of the same design on the same server). A user can drag a document A in project A onto the dashboard of project B, then the dropped document will be imported.

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4387)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3604)
  * [Documentation](https://github.com/livingdocsIO/documentation/pull/404)


## Comment mentions :tada:

Allows to mention another user in the comments. When writing '@' in a comment a user search will appear to select a user to be mentioned. The mentioned user then gets a notification. Check the [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4375) if you want to get some visual impressions.

Important: If you want to use comments mentioning, you have to enable [Notifications](https://docs.livingdocs.io/enterprise/guides/watching-documents/)

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4375)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3652)
  * [Documentation](https://github.com/livingdocsIO/documentation/pull/403)


## Composition API (in beta)

There is a new public api endpoint:
```http
POST /api/beta/composition/:documentId
```

This endpoint is meant to serve as a replacement of `GET api/v1/documents/:documentId/latestPublication` for deliveries when rendering documents. The goal of the composition endpoint is to gather all required information to render a document in one endpoint and to work for different rendering strategies (e.g. render from JSON or use the prerendered Html). The composition Api currently supports rendering Html without any configuration, can preload references in metadata and can return resolved includes as JSON.

It also offers optimised performance for all those tasks and will replace the RenderPipeline feature.

We plan to add additional functionalities like automatic design updates of documents and more to the composition Api in upcoming releases and are open for inputs what we could add to the composition Api.

* [Composition API](https://github.com/livingdocsIO/livingdocs-server/pull/3667)
* [Public API Doc](https://github.com/livingdocsIO/livingdocs-editor/pull/4434)

## Media Library - Multi Language :tada:

With the introduction of the multi language metadata feature, one can now translate metadata into different languages.

* References
  * [Documentation](https://github.com/livingdocsIO/documentation/pull/402)
  * [Multilanguage Metadata for Images](https://github.com/livingdocsIO/livingdocs-editor/pull/4283)
  * [Multilanguage Metadata for Videos](https://github.com/livingdocsIO/livingdocs-editor/pull/4372)
  * [Prefilling for Images](https://github.com/livingdocsIO/livingdocs-editor/pull/4357)
  * [Multilanguage Media Upload](https://github.com/livingdocsIO/livingdocs-editor/pull/4364)
  * [Multilanguage Media Library Types](https://github.com/livingdocsIO/livingdocs-server/pull/3512)
  * [Media Library Support for Granular Patches](https://github.com/livingdocsIO/livingdocs-server/pull/3624)
  * [Replace / Translate Assets Editor](https://github.com/livingdocsIO/livingdocs-editor/pull/4393) :gift:

## Media Library - File - Add Support for Files :tada:

Additionally to the existing images and videos, we now also support files in the Media Library. Files can be added to documents in order to allow downloads, e.g. providing a downloadable press release next to an article.

* References
  * [File Upload Editor](https://github.com/livingdocsIO/livingdocs-editor/pull/4373)
  * [File Icons Editor](https://github.com/livingdocsIO/livingdocs-editor/pull/4385)
  * [File Upload Server](https://github.com/livingdocsIO/livingdocs-server/pull/3595)
  * [Documentation Media Type mediaFile](https://github.com/livingdocsIO/documentation/pull/395)
  * [Documentation Media Library Config](https://github.com/livingdocsIO/documentation/pull/393)


## Media Library - Video - Add Transcoding Metadata Plugin :tada:

With the video transcoding metadata plugin
- You can notify an external system to start transcoding a video
- The external system can call the public API and respond with transcoding state
- The editor shows the current state

* References
  * [Documentation](https://github.com/livingdocsIO/documentation/pull/397)
  * [Basic Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4324)
  * [Basic Server PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3568)
  * [Update Transcoding State in Realtime w/o reload](https://github.com/livingdocsIO/livingdocs-editor/pull/4382)
  * [Realtime Metadata Sync for li-transcoding state](https://github.com/livingdocsIO/livingdocs-server/pull/3665)


## Sitemaps + Feeds :tada:

- Consume Sitemaps via public API
- We support you to implement your own RSS Feed (RSS 2.0) via server APIs (because feeds are highly customizable)

* References
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3664)
  * [Guide on how to generate Sitemaps & Feeds](https://github.com/livingdocsIO/documentation/pull/401)
  * [Public API doc](https://github.com/livingdocsIO/livingdocs-editor/pull/4409)


## New License Model and Billing :tada:

We provide a new "Billing" screen in the server admin backend that shows per month which kinds of users are on the system and the changes from month to month. In that way customers can keep track of their inferred license costs.
Also, all screens to invite users to your projects now require you to specify the kind of user: Editorial User (full license), Freelancer or Technical User (free). The employment type can be corrected if need be on the server admin detail screen.

* References
  * [License Model - Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4334)
  * [License Model - Server PR Iteration 1](https://github.com/livingdocsIO/livingdocs-server/pull/3594)
  * [License Model - Server PR Iteration 2](https://github.com/livingdocsIO/livingdocs-server/pull/3637)
  * [Billing - Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4388)
  * [Billing - Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3669)




# Breaking Changes :fire:

This time we have a rather high amount of breaking changes, therefore we grouped the breaking changes into different sections:

- [Pre Deployment](#pre-deployment-fire)
- [Main](#main-fire)
- [Configs](#configs-fire)
- [Drop Callback Support](#drop-callback-support-fire)

## Pre Deployment :fire:

### Migrate firstPublicationDate to documents table (pre deployment) :fire:

In order for a delivery to know when a document was first published, we want to provide the firstPublicationDate when a Publication is fetched from the Public API. To be able to fullfill that goal we need a db migration.

For productive systems please run a manual migration using `node ./db/manual-migrations/007-populate-first-publication-date.js` to process the documents in batches. The manual migration must be done before `livingdocs-server migrate up`, which contains the same migration, but locks the database by ~10s for 100k documents.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3505)

### Move metadata id's (pre deployment) :fire:

Tidy-up after populating `document_revisions.metadata_id` as part of the `firstPublicationDate` feature in [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3505)

For productive systems please run a manual migration using `node ./db/manual-migrations/008-move-metadata_id.js` to process the documents in batches. The manual migration must be done before `livingdocs-server migrate up`, which contains the same migration, but locks the database. We propose to have enough disk space left for this migration (2 x used disk space by the database). After the migration, the disk space should be smaller, but during the migration, it will grow.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3518)

## Main :fire:

### Migrate the database

It's a simple/fast migration with no expected data losses.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 156-add-content-type-id-on-document-publication-events.js
# migration - 157-add-documents-data-column.js
# migration - 158-remove-metadata_id-columns.js
# migration - 159-add-content_type_id_indexes.js
# migration - 160-add-li_jsonb_patch-function.js
# migration - 161-add-user-occupations.js
# migration - 162-update-li_jsonb_patch-function.js
livingdocs-server migrate up
```

### Drop Node 12 support :fire:

- :fire: Upgrade to npm v7
- :fire: Drop node `v12`. Only node `v14` / `v15` and `v16` are supported from now on.
- 🛡️ Run the process as non-root user in production

#### Migration Howto (node 16)

- Change the content of the `.nvmrc` in your project root to `16`
- Change the `engines.node` declaration in the `package.json` to `>=16`
- Change the docker image versions in your `Dockerfile` to `livingdocs/server-base:16.0` / `livingdocs/editor-base:16.0`

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4256)


#### Add Strict Schema Validation for JSON Schema :fire:

- We've migrated our json validator from `tv4` to `ajv` and applied a :fire: strict schema validation.
- Invalid json schemas now cause a shutdown of the server.
- If the server stops during startup, you'll need to fix the schemas.

The `type` declaration on a schema is now mandatory. Previously it was implicitly declared.

```js
body: {
  type: 'object', // < this attribute was optional with
                  // the old validator. It's mandatory now.
  properties: {
    something: {type: 'string'}
  }
}
```

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3681)




### Remove set() hook for metadata plugins :fire:

:fire: Remove `set()` hook for metadata plugins. Use `onUpdate()` instead.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3541)


### Remove Gravatar for User Avatars as Default Solution :fire:

User Avatars are now generated using initials of the user name (first letter of firstname, first letter of lastname).

Gravatar: If you want to keep using Gravatar for user avatars, you have to opt-in by setting `app.useGravatar: true` in the editor config.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4250)


### LegacyDocumentModel Getters :fire:

This change should not affect customers, but based on how deep you dived into Livingdocs document models, it could affect you.

Some writing operations of the `documentsApi` return a `LegacyDocumentModel`.
`LegacyDocumentModel.revision`, `LegacyDocumentModel.document`, `LegacyDocumentModel.metadata` and `LegacyDocumentModel.last_publication` are now getters and will :fire: throw when you try to assign a value. If you really need to assign a value, please use the new `LegacyDocumentModel.revisionEntity` or similar property.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3542)

### Old File Upload :fire:

If you used the file upload through drag&drop into documents before, you now have to configure a `mediaType` like this to restore that behavior:

```js
module.exports = {
  type: 'mediaFile',
  handle: 'file',
  info: {
    label: 'File'
  },
  metadata: [
    {
      handle: 'title',
      type: 'li-text',
      ui: {component: 'liMetaTextForm'},
    }
  ]
}
```

References:
- [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4373)

### Remove Registration Endpoints :fire:

- :fire: removed editing API endpoint `register`
- :fire: removed editing API endpoint `register/website`

References:
- [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3594)


## Configs :fire:

### Remove editor configs :fire:

- 🔥 Removed editor config `supportedBrowsers`. No replacement is provided for now. If you really need one, talk to us.
- 🔥 Removed editor config `sidePanelBehaviour`. The main navigation opens/closes on click (by ignoring double-clicks). The possibility to activate open/close on mouseenter (hover) is removed.
- 🔥 Removed dependency `bowser` (https://www.npmjs.com/package/bowser). If you use it in downstream, we suggest to replace by feature/touch input detection or adding the dependency to your downstream project

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4244)

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


### Media Library Server Config :fire:

- :fire: remove serverConfig `assetManagement` (googleVision and enabled has no effect since release-2020-07)
- :fire: remove serverConfig `mediaLibrary.enabled` (had no effect since release-2020-07)
- :fire: remove serverConfig `mediaLibrary.types` (had no effect since release-2020-07) use [mediaTypes](https://docs.livingdocs.io/enterprise/reference-docs/project-config/media_types/) instead
- :fire: remove serverConfig `mediaLibrary.autoTagging` (googleVision has no effect since release-2020-07) use [project integrations](https://docs.livingdocs.io/enterprise/reference-docs/server-configuration/#google-vision-api) instead
- :fire: remove serverConfig `mediaLibrary.paginationSize` (had no effect since release-2020-07)

References:
- [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3642)


### Moved Elasticsearch Properties :fire:

The server configuration `search.indexer` got moved into `elasticIndex`. The old `search.indexer` config got removed.

- :fire: Move `search.indexer.concurrency` to `elasticIndex.concurrency`
- :fire: Move `search.indexer.batchSize` to `elasticIndex.batchSize`
- :fire: Move `search.indexer.maxCpu` to `elasticIndex.maxCpu`

References:
- [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3640)


### Handles and mediaLibraryEntry.asset.url :fire:

#### Handles :fire:

Content Type and Media Type handles must conform to the pattern `^[a-z][a-zA-Z0-9-]{2,49}$`.
Metadata properties must conform to the pattern `^[a-zA-Z][a-zA-Z0-9-_]{2,49}$`.

Please alert us if the pattern is too restrictive. We already applied those patterns in the editor when Content Types got configured on the Project Settings screen. It was just the validation on the server that was missing.
In all the cases known to us, this won't affect the existing setups.

#### mediaLibraryEntry.asset.url
Before the changes in here either the `mediaLibraryEntry.asset.key` or `mediaLibraryEntry.asset.url` were mandatory on an media library asset object. From now on the `url` is not considered as fallback for the key and therefore the `key` property is :fire: `mandatory`.
This change shouldn't affect you and you should see warnings in case you've invoked the internal apis without key, you should see a validation error.
Please let us know if you run into any issues with that.

References:
- [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3672)


## Drop Callback Support :fire:

### Drop Callbacks for Authentication API :fire:

:fire: Remove callback support for `authenticationApi` (`server.features.api('li-authentication')`) functions. Only promise based calls are supported.

References:
- [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3633)

### Drop Callbacks for localAuthenticationApi :fire:

:fire: Remove callback support for localAuthenticationApi (server.features.api('li-authentication-local')) functions. Only promise based calls are supported

References:
- [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3670)




# Deprecations

We did a cleanup for asset related server configs and moved them into the mediaLibrary feature. The old configs are still supported, but we suggest to move them now.

🔧  Deprecate server config `files`. Move config to server config `mediaLibrary.files`
🔧  Deprecate server config `videos`. Move config to server config `mediaLibrary.videos`
🔧  Deprecate server config `images`. Move config to server config `mediaLibrary.images`

References:
* [Server PR - files/videos](https://github.com/livingdocsIO/livingdocs-server/pull/3595)
* [Server PR - images](https://github.com/livingdocsIO/livingdocs-server/pull/3627)


# APIs :gift:

## Server API's

### Includes API

The includes API got a lot of improvements regarding batch loading and performance, please check out the [pull request](https://github.com/livingdocsIO/livingdocs-server/pull/3618) to get more info. The most important features are:
- Bulk include resolver
- Preloading include param refrences
- Duplicate Filtering
- Added `li-list` metadata plugin

Extended APIs:
- 🎁 `includesApi.resolveIncludes({options, includes})`: resolve multiple includes at once. This will automatically batch requests with the new batchLoader. This will drastically reduce the number of database requests as well as response times.
- 🍬 `includesApi.resolveIncludes({..., batchLoader})`: you can now pass in a batchLoader instance.
- 🎁 `includesApi.buildOptions({documentVersion})`: new helper method to build the options params which need to be passed to resolveInclude() and resolveIncludes()

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3618)


### Sitemaps API

Added a new Sitemaps API to simplify setting up and maintaining sitemaps and RSS feeds.

- 🎁 `sitemapsApi.getSitemapIndex({contentTypes, baseUrl, projectId})`
- 🎁 `sitemapsApi.getSitemapUrlSet({date, contentTypes, projectId, baseUrl})`
- 🎁 `sitemapsApi.renderFeedXml({...})`

The renderFeedXml is based on [RSS 2.0 Specification](https://validator.w3.org/feed/docs/rss2.html)

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3664)

### Import API

- 🎁 `server.features.api('li-import').importDocumentAndMedia()` - added new function to import documents and media assets from another project

### Document API

- 🍬 `documentApi.createV2()` Now accepts params content and design (Previously one had to pass revision: {data: {content, design}}.

### Document List API

* 🎁 `documentListApi.get(id, null, {reverseMatched: false})` - Add reverse option

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3654)

### DocumentVersion

Some customers still use internal properties of the `DocumentVersion` model which always can change. Please don't use them.
- :fire: don't use `documentVersion.documentEntity`
- :fire: don't use `documentVersion.revisionEntity`
- :fire: don't use `documentVersion.publicationEntity`
- :fire: don't use `documentVersion.metadataEntity`

Always use the [official API of the documentVersion](https://github.com/livingdocsIO/documentation/pull/406).

We also have deprecated some functions in the `DocumentVersion`. Please go through the list below and replace internal and deprecated calls.

**Deprecations**
- `documentVersion.getContentType()` -> `documentVersion.contentType`
- `documentVersion.getDocumentType()` -> `documentVersion.documentType`
- `documentVersion.getProjectId()` -> `documentVersion.projectId`
- `documentVersion.getChannelId()` -> `documentVersion.channelId`
- `documentVersion.getDocumentId()` -> `documentVersion.id`
- `documentVersion.getDesignDescriptor()` -> `documentVersion.design`
- `documentVersion.getDesignVersion()` -> `documentVersion.design.version`
- `documentVersion.getTitle()` -> `documentVersion.title`
- `documentVersion.getMetadata()` -> `documentVersion.metadata`
- `documentVersion.getMetadataSource()` -> `documentVersion.metadataSource`
- `documentVersion.getSystemdata()` -> `documentVersion.systemdata`





## Public API's

### Add Filters for latestPublications

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

### Media Library - Add Version property

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3567)


### Document Import - Set Creation Date of Publication

Allows to import documents with a publicationDate flag which will set the creation date of a publication.

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3569)
* [Documentation](https://github.com/livingdocsIO/documentation/pull/390)

### Sitemaps

Allows to get sitemap infos. Two new HTTP endpoints accessible with a public API token with the 'read'-scope

- 🎁 Introduce  `GET ${serverUrl}/api/v1/sitemaps/index?contentTypes=articles&baseUrl=https://livingdocs.io` (public API token with 'read'-scope needed)
- 🎁 Introduce  `GET ${serverUrl}/api/v1/sitemaps/entries?date=2020-01&contentTypes=article&baseUrl=https://livingdocs.io/&entriesPerPage=20000` (public API token with 'read'-scope needed)

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3664)
* [Documentation](https://github.com/livingdocsIO/livingdocs-editor/pull/4409)

## Server CLI

### livingdocs-server project-truncate

`livingdocs-server project-truncate -p <your-project> -y` truncates documents in Elasticsearch too (instead of only truncating Postgres documents).

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3545)


# Other Changes

### Opt-In for Vue based metadata form rendering (support us!)

When you opt-in by setting the editor config to `metadata.useVueBasedFormRendering: true`, all Metadata Forms are rendered using a Vue based rendering. For any properties/forms without a Vue component, the Angular component is rendered. This is also how custom metadata plugins using angular forms is supported.

:gift: You can support us with the transition to Vue when opt-in to the vue based form rendering.


References:
* [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4231)

### Features

* Add `minLength`, `recommendedMinLength` and `recommendedMaxLength` to `doc-editable` directive [livingdocs-editor #4255](https://github.com/livingdocsIO/livingdocs-editor/pull/4255) :gift:
* Woodwing: Add media source example into the example server [livingdocs-server #3565](https://github.com/livingdocsIO/livingdocs-server/pull/3565) :gift:
* Auth: Sync OpenId Connect user groups on login [livingdocs-server #3563](https://github.com/livingdocsIO/livingdocs-server/pull/3563) :gift:
* Storage: Add support for storage prefix [livingdocs-server #3587](https://github.com/livingdocsIO/livingdocs-server/pull/3587) :gift:
* Includes: add bulk resolve endpoint to editingApi [livingdocs-server #3688](https://github.com/livingdocsIO/livingdocs-server/pull/3688) :gift:
* Toolbar: Add localised quotation marks to toolbar [livingdocs-editor #4391](https://github.com/livingdocsIO/livingdocs-editor/pull/4391) :gift:


### Improvements

* Do not use offensive project handles [livingdocs-server #3589](https://github.com/livingdocsIO/livingdocs-server/pull/3589) :gift:
* Show tasks in toolbar as soon as the content-type has a task config [livingdocs-editor #4359](https://github.com/livingdocsIO/livingdocs-editor/pull/4359) :gift:
* MediaLibrary
  * Download files in editor via server [livingdocs-server #3627](https://github.com/livingdocsIO/livingdocs-server/pull/3627) :gift:
  * Improve config error handling [livingdocs-server #3647](https://github.com/livingdocsIO/livingdocs-server/pull/3647) :gift:
  * Use video poster image in dashboard card [livingdocs-editor #4363](https://github.com/livingdocsIO/livingdocs-editor/pull/4363) :gift:
* Public API: fix order and validation in `/api/v1/documents/latestPublications` [livingdocs-server #3649](https://github.com/livingdocsIO/livingdocs-server/pull/3649) :gift:
* Editor
  * Emitting event before a connection is initialised no longer throws errors. [livingdocs-editor #4366](https://github.com/livingdocsIO/livingdocs-editor/pull/4366) :gift:
  * Consider image drop cases with insertsBlocked [livingdocs-editor #4377](https://github.com/livingdocsIO/livingdocs-editor/pull/4377) :gift:
  * Configure Icons for each ContentType [livingdocs-editor #4339](https://github.com/livingdocsIO/livingdocs-editor/pull/4339) :gift:
  * Imatrics performance improvements [livingdocs-editor #4347](https://github.com/livingdocsIO/livingdocs-editor/pull/4347) :gift:
  * Includes: bulk resolve includes [livingdocs-editor #4400](https://github.com/livingdocsIO/livingdocs-editor/pull/4400) :gift:

### Bugfixes

#### Security

* Prevent identity creation without a user  [livingdocs-server #3560](https://github.com/livingdocsIO/livingdocs-server/pull/3560) :beetle:
* Do not send out too many 'new device login' emails [livingdocs-server #3571](https://github.com/livingdocsIO/livingdocs-server/pull/3571) :beetle:
* Users will be able to log in even if new device emails cant be sent [livingdocs-server #3597](https://github.com/livingdocsIO/livingdocs-server/pull/3597) :beetle:
* Correctly redirect upon signup [livingdocs-editor #4232](https://github.com/livingdocsIO/livingdocs-editor/pull/4232) :beetle:
* Log users in even if they dont have a default design [livingdocs-editor #4275](https://github.com/livingdocsIO/livingdocs-editor/pull/4275) :beetle:

#### Editor

* Link tool
  * Make removing an existing link possible again [livingdocs-editor #4321](https://github.com/livingdocsIO/livingdocs-editor/pull/4321) :beetle:
  * Improve delivery path pattern matching and handling of matching paths with nonexisting IDs [livingdocs-editor #4325](https://github.com/livingdocsIO/livingdocs-editor/pull/4325) :beetle:
* Multiselect: Only allow to transform available components of a content-type [livingdocs-editor #4331](https://github.com/livingdocsIO/livingdocs-editor/pull/4331) :beetle:
* Clipboard
  * Fix drag and drop of a container [livingdocs-editor #4243](https://github.com/livingdocsIO/livingdocs-editor/pull/4243) :beetle:
  * Render includes when dropping a component from the clipboard [livingdocs-editor #4330](https://github.com/livingdocsIO/livingdocs-editor/pull/4330) :beetle:
  * Do not insert default content when dropping a component [livingdocs-editor #4358](https://github.com/livingdocsIO/livingdocs-editor/pull/4358) :beetle:
* Search Filter: Fix multiSourceSearch to use filters [livingdocs-editor #4257](https://github.com/livingdocsIO/livingdocs-editor/pull/4257) :beetle:
* Editor Admin
  * Fix ordering of semantic versions in design screen [livingdocs-editor #4260](https://github.com/livingdocsIO/livingdocs-editor/pull/4260) :beetle:
  * Fix group screen errors [livingdocs-editor #4226](https://github.com/livingdocsIO/livingdocs-editor/pull/4226) :beetle:
  * Webhooks: fix the form layout for the event checkboxes [livingdocs-editor #4320](https://github.com/livingdocsIO/livingdocs-editor/pull/4320) :beetle:
* Includes: Fix checkboxes for twitch and instagram include [livingdocs-editor #4262](https://github.com/livingdocsIO/livingdocs-editor/pull/4262) :beetle:
* Show correct message when server is offline and proxiedHost is enabled [livingdocs-editor #4264](https://github.com/livingdocsIO/livingdocs-editor/pull/4264) :beetle:
* Metadata
  * li-text: correctly render when `config.useAsTitle` [livingdocs-editor #4270](https://github.com/livingdocsIO/livingdocs-editor/pull/4270) :beetle:
  * li-image: Crop url fix [livingdocs-editor #4348](https://github.com/livingdocsIO/livingdocs-editor/pull/4348) :beetle:
  * li-image / li-poster-image: Crop handling [livingdocs-editor #4352](https://github.com/livingdocsIO/livingdocs-editor/pull/4352) :beetle:
  * li-date-time-validity: Ensure date input format for all metadata fields is ISO 8601 compatible [livingdocs-editor #4356](https://github.com/livingdocsIO/livingdocs-editor/pull/4356) :beetle:
* Images:
  * Fix the step behavior of the zoom buttons on the image cropper [livingdocs-editor #4367](https://github.com/livingdocsIO/livingdocs-editor/pull/4367) :beetle:
  * Fix issue where an image could not be dropped onto a directive of a fixed component if no insert before or after this component is allowed. [livingdocs-editor #4377](https://github.com/livingdocsIO/livingdocs-editor/pull/4377) :beetle:
* Upload Center: Don't close the upload dialog when the crop tool is opened from the upload dialog [livingdocs-editor #4383](https://github.com/livingdocsIO/livingdocs-editor/pull/4383) :beetle:
* Comments: Init comments only when they are enabled on collab bar [livingdocs-editor #4337](https://github.com/livingdocsIO/livingdocs-editor/pull/4337) :beetle:
* Handle multiple open dialogs in dialogService [livingdocs-editor #4383](https://github.com/livingdocsIO/livingdocs-editor/pull/4383) :beetle:


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
* Email: Schema Fix [livingdocs-server #3692](https://github.com/livingdocsIO/livingdocs-server/pull/3692) :gift:



  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
