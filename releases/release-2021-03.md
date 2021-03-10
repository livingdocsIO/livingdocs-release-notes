LATEST:
- server: 118.0.1
- editor: 60.1.0


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

#### Features

* Recording: **TODO**
* Documentation: **TODO**

#### Developers

* Recording: **TODO**
* Slides: **TODO**

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2021-03`
`@livingdocs/editor` | `release-2021-03`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2021-03",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2021-03

### Livingdocs Server Patches
- [v124.5.3](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v124.5.3): fix: update framework to release-2021-03
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2021-03",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2021-03

### Livingdocs Editor Patches
- [v63.8.4](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.4): fix(collaboration): Fix the avatar support in the collaboration mode
- [v63.8.3](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.3): fix(publish screen): don't log errors to console when MetadataValidationErrors are returned for publish request
- [v63.8.2](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v63.8.2): fix: update framework to release-2021-03
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text





# Highlights

## EXAMPLE :tada:

## Multi Cluster Indexing :tada:

There are a bunch of new features for indexing
- :gift: Support multiple elasticsearch clusters during indexing
- :gift: Add config to enable/disable consumers (e.g. to disable consumers for a delivery instance)
- :gift: Custom indexes can target a specific elasticsearch cluster
- :candy: Improved error handling

References:
  * [Multi Cluster Indexing Preparation - I](https://github.com/livingdocsIO/livingdocs-server/pull/3299)
  * [Multi Cluster Indexing Preparation - II](https://github.com/livingdocsIO/livingdocs-server/pull/3348)
  * [Multi Cluster Indexing](https://github.com/livingdocsIO/livingdocs-server/pull/3361)
  * [Support Disabling Elasticsearch Clusters](https://github.com/livingdocsIO/livingdocs-server/pull/3373)
  * [Improve CLI Help for Indexing](https://github.com/livingdocsIO/livingdocs-server/pull/3371)
  * [Documentation](TODO@marc)


## Asset Management - Videos :tada:

TODO@ralph are there more pr's?

References:
  * [Add Storage Config for Video](https://github.com/livingdocsIO/livingdocs-server/pull/3296)
  * [Video Storage Config Documentation](https://github.com/livingdocsIO/livingdocs/pull/350)
  * [Documentation](TODO@beni)


## Named Crops :tada:

The Named Crops feature supports multiple crops per image in a document.

<img width="589" src="https://user-images.githubusercontent.com/821875/103688930-dc9c9180-4f92-11eb-894d-45ae105e72a4.png">


References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4051)
  * [Framework PR](https://github.com/livingdocsIO/livingdocs-framework/pull/511)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3261)
  * [Editor PR (Design Improvements)](https://github.com/livingdocsIO/livingdocs-editor/pull/4101)
  * [Documentation](TODO@beni)



## Notification Center

References:
* [Documentation](TODO@okan TODO@beni)
* [Document Notifications](https://github.com/livingdocsIO/livingdocs-server/pull/3251)


## SSO for Azure Active Directory :tada:

Add SSO support for Azure Active Directory.

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3355)
  * [Documentation](TODO@okan)

## Media Sources :tada:

Allow to connect/integrate external asset services (e.g. Unsplash, Shutterstock, Pixabay, ...) as a Media Source in the Livingdocs Media Library. Working with a Media Source in Livingdocs feels the same as working with other assets of the Media Library.

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3266)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4106)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/357)


## Tracing :tada:

...add a description TODO@alex...

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3205)
  * [Documentation](TODO@alex)












# Breaking Changes :fire:

## Migrate the database

It's a simple/fast migration with no expected data losses.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 148-add-documents-project-id-not-null.js
#   add index on media_library_entries.media_type_id
# migration - 149-declare-expect_equal_version-as-immutable.js
#   update function expect_equal_version
# migration - 150-drop-legacy-tables.js
#   drop old tables assets / access_tokens / category_events / import_hugo_feeds
# migration - 151-add-references-columns.js
#   add column documents.references document_publications.references
# migration - 152-add-index-on-document-publications-created-at.js
#   add index on document_publications.created_at
# migration - 153-add-media-library-refs.js
#   add column media_library_entries.references
# migration - 154-add-index-on-authorization-code-events-aggregate-id.js
#   add index on authorization_code_events.aggregate_id
# migration - 155-add-content-type-id-on-document-publication-events.js
#   add column document_publication_events.content_type_id
# migration - 155-add-document-user-relations.js
#   add table document_user_relations
livingdocs-server migrate up
```

## Migrate references

As described in the [APIs](#apis-gift) section, we extend some endpoints (public API + server API) with reference information of a document. Old document references need to be converted into the new format with a manual db migration.

After the release, execute the manual db migration `node ./db/manual-migrations/006-generate-references`

These are the key changes/issues
- It's a database heavy operation and should be executed outside business time (when having a lot of documents)
- generate document and publication references and store them on the db
- remove document revision references (TODO@alex what are the consequences for public- and serverAPIs?)

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3341)


## Remove Legacy Postgres Tables :fire:

These Postgres tables have been removed:
- `assets` - got replaced by `media_library_entries` earlier last year
- `access_tokens` - The access_tokens table got removed in release-2020-12 as we now only track session ids
- `category_events` - This table wasn't in use at all
- `import_hugo_feeds` - This table also got created about 4 years ago and isn't in use

:fire: Please make sure that you don't directly access those tables in your code.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3386)



## Changed API for indexingApi :fire:

- :fire: Removed `indexingApi.bulk`. The index clients are directly exposed in the index init features and on there we have a `esClient.customBulk` method you can use.
- :fire: `indexingApi.document.addDocumentUpdate` moved to `indexingApi.addDocumentUpdate`
- :fire: `indexingApi.document.reindex` got replaced by `indexingApi.addBackgroundIndexingJobsByBatches`
- :fire: `indexingApi.document.addJob` got removed. Please use `indexingApi.addBackgroundIndexingJobsByBatches` instead
- :fire: `indexingApi.media.addMediaUpdate` moved to `indexingApi.addMediaUpdate`
- :fire: `indexingApi.media.reindex` got replaced by `indexingApi.addBackgroundIndexingJobsByBatches`
- :fire: The cli tasks `es-media-reindex` and `es-search-reindex` got replaced by `elasticsearch-index`
  ```bash
  livingdocs-server elasticsearch-index --handle li-media
  livingdocs-server elasticsearch-index --handle li-documents
  livingdocs-server elasticsearch-index --handle li-publications
  ```
- :fire: Upgrade to [`pino@6.11.0`](https://github.com/pinojs/pino/releases/tag/v6.0.0)
  ```js
  // Previously, Pino supported multiple arguments and concatenated them into a string
  // With the upgrade, the api changed slightly and to form the same message, `%s` and `%j` must be used

  // Example 1
  //   Before
  log.info({foo: 'bar'}, 'a message', { an: 'object'})
  //   After
  log.info({foo: 'bar'}, 'a message %j', { an: 'object' })
  //   Output
  "foo":"bar","msg":"a message {\"an\":\"object\"}"


  // Example 2
  //   Before
  log.info({foo: 'bar'}, 'a', 'silly', 'message')
  //   After
  log.info({foo: 'bar'}, 'a %s %s', 'silly', 'message')
  //   Output
  "foo":"bar","msg":"a silly message"
  ```

TODO@marc - update doc with new CLI commands.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3361)


## Changed format of 'document.update' event :fire:

The `document.update` event will only receive `user: {id: userId}`. Previously the user object could have more params on it (like admin or project_id) depending on what user object was passed into documentApi.updateV2(). Note that currently it is also possible that `user: {id: undefined}` is passed as the user.id is not required in documentApi.updateV2().

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3352)



## Removed 'li-netlify-publish-hooks' feature :fire:

🔥 Removes the `li-netlify-publish-hooks` feature (which seems not to be used by anyone) as the more generic webhooks feature already offers the same behavior. The [webhook](https://docs.livingdocs.io/reference-docs/server-initalization/webhooks) documentation can help to migrate the feature.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3362)




## Changed doc-link and doc-html directive to objects :fire:

- :fire: Update [Framework](https://github.com/livingdocsIO/livingdocs-framework/pull/509) to v18 - New documents will store link and html directives as objects. Old documents will still store them as strings until you run a manual migration.
- :fire: Public API: `GET /latestPublication` and `GET /latestPublications` return the JSON as stored in the database. Thus after the update you will receive the old and new format until you run a manual migration.

After the update newly created doc-link and doc-html directives are stored as

```js
// Example Old
content = [{
  id: 'doc-ez23k2',
  identifier: 'design.link',
  content: {
    link: 'https://livingdocs.io'
  }
}, {
  id: 'doc-iej286',
  identifier: 'design.html',
  content: {
    html: '<div></div>'
  }
}]


// Example New
content = [{
  id: 'doc-ez23k2',
  identifier: 'design.link',
  content: {
    link: {
      href: 'https://livingdocs.io'
    }
  }
}, {
  id: 'doc-iej286',
  identifier: 'design.html',
  content: {
    html: {
      html: '<div></div>',
      target: '_blank'
    }
  }
}]
```


- 🔥 `getContent()` of html and link directives changes return type

The html and link directives will in future be data directives, i.e. store object literals. This means that the `getContent()` method will return an object literal and not a string value anymore. The change looks as follows.

```js
// old
const html = htmlDirective.getContent()
const href = linkDirective.getContent()

// new
const {html} = htmlDirective.getContent()
const {href, target} = linkDirective.getContent()
```

:fire: This change requires you to change all cases of `getContent` on link and html directives in your code. In particular look out for custom document conversions and include code.

If you used direct JSON access in a livingdoc directive (not recommended),
you will also need to change the access.

```js
// old
const html = htmlDirective.content.value
const href = linkDirective.content.value

// new
const {html} = htmlDirective.content
const {href, target} = linkDirective.content
```


References:
* [Framework PR](https://github.com/livingdocsIO/livingdocs-framework/pull/509)
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3242)
* [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3981)


## Fix close tags in Angular templates :fire:

:fire: If you have downstream **Angular** templates, change all XHTML like closing tags `<some-tag/>` to valid HTML5 `<some-tag></some-tag>`.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4107)


## Add property 'isAutomatic' to Metadata plugin 'li-image' :fire:

A crop object in the crops array on the value of a metadata `li-image` property contains the boolean property `isAutomatic` now. If you have any metadata property of type `li-image` configured, you need to add the `isAutomatic` property to the mapping.

```js
// TODO@beni: Add Instruction what exactly to do here
```

:fire: removed the editor config `app.ui.article.publish.cropStyles`. It has no effect anymore

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4051)

##


References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4106)


### Media Library Dashboard Configuration Change :fire:

:fire: Removed project config `editorSettings.mediaLibrary.editorSelection.displayFilters`

If you want to keep the filters, you need to move the config to the `mediaType` project config.

```js
// mediaType config example
{
  handle: 'image',
  type: 'mediaImage',
  metadata: [],
  editor: {
    dashboard: {
      // use the config of editorSettings.mediaLibrary.editorSelection.displayFilters
      // if you want to keep the old behavior
      displayFilters: []
    }
  }
}
```




# Deprecations

## swisscomTV.customLanguageHandle

The server config `swisscomTV.customLanguageHandle` is not used any longer for the reference extraction. All metadata of type `li-language` will be extracted to the references if they have a `groupId`.




# APIs :gift:

## References

We worked on document reference extraction. The list below contains public APIs and server APIs with an additional `reference` property in the response. Look into the [documentation](TODO@alex) to get different types of references.

- :candy: `POST /document-copy/:documentId/copy`
- :candy: `POST /document-copy/:documentId/transform`
- :candy: `POST /publications/:publicationId/republish`
- :candy: `documentApi.getLatestDocument()`
- :candy: `documentCopyApi.copyByDocumentId()`
- :candy: `documentCopyApi.copyWithoutConfig()`
- :candy: `documentCopyApi.transformByDocumentId()`
- :candy: `publicationApi.getLatestPublication()`
- :candy: `publicationApi.getLatestPublications()`
- :candy: `publicationApi.getPublicationsByDate()`
- :candy: `publicationApi.getPublicationsByDocumentIds()`
- :candy: `publicationApi.republish()`

References:
* [Documentation](TODO@alex)
* [Extract References PR](https://github.com/livingdocsIO/livingdocs-server/pull/3341)
* [Extract References for Videos PR](https://github.com/livingdocsIO/livingdocs-server/pull/3383)
* [Add Endpoints PR](https://github.com/livingdocsIO/livingdocs-server/pull/3365)


## Public API Beta

For all public API endpoints documentation, go to 'https://your-editor.com/public-api'.

- 🎁 Add new endpoint `/api/beta/documents/:documentId/incomingDocumentReferences`
- `/api/beta/documents/:documentId/latestPublication` - add next extracted references format
- `/api/beta/documents/:documentId/latestPublications` - add next extracted references format

References:
* [Documentation](TODO@alex)
* [Add Endpoints PR](https://github.com/livingdocsIO/livingdocs-server/pull/3365)


## Server API - includesApi

- :gift: Add `includesApi.getServiceConfig({serviceName})` method to `includesApi`.











#### Add context object to import endpoints :gift:

A `context` (max 8192 bytes) parameter can be passed to:

- `POST api/v1/import/documents`
- `POST api/v1/import/images`
- `POST api/v1/import/videos`

If the webhook parameter is defined as well, context will be passed to the webhook once the job is finished.

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs-editor/pull/4100)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3353)





# Internal Changes











# Other Changes

### Design

* Priority truck polish [livingdocs-editor #4091](https://github.com/livingdocsIO/livingdocs-editor/pull/4091) :gift:
* Style Guide: Clean up the style guide [livingdocs-editor #4149](https://github.com/livingdocsIO/livingdocs-editor/pull/4149) :gift:

### Improvements

* Dashboards
  * Properly handle pagination for a resultList [livingdocs-editor #4153](https://github.com/livingdocsIO/livingdocs-editor/pull/4153) :gift:
  * List dashboard: Hide 'go to article' button in list UI when dragging [livingdocs-editor #4094](https://github.com/livingdocsIO/livingdocs-editor/pull/4094) :gift:
  * Add 'video-' and 'imageLibrary' dashboard [livingdocs-editor #4046](https://github.com/livingdocsIO/livingdocs-editor/pull/4046) :gift:
* Editor
  * Image cropping: Use downscaled image size for very large images [livingdocs-editor #4141](https://github.com/livingdocsIO/livingdocs-editor/pull/4141) :gift:
  * Editing: Add Iframe height watcher (guard) [livingdocs-editor #4108](https://github.com/livingdocsIO/livingdocs-editor/pull/4108) :gift:
* CLI
  * Add 'newerThan' argument for task 'cleanup-documents' [livingdocs-server #3333](https://github.com/livingdocsIO/livingdocs-server/pull/3333) :gift:
* Import
  * Support files with no file ending of mimeType image [livingdocs-server #3380](https://github.com/livingdocsIO/livingdocs-server/pull/3380) :gift:
* Error handling: Add extended description to error declaration class [livingdocs-server #3214](https://github.com/livingdocsIO/livingdocs-server/pull/3214) :gift:


### Bugfixes

* Media library
  * Rename pusher topic to media and allow - in mediaId [livingdocs-server #3382](https://github.com/livingdocsIO/livingdocs-server/pull/3382) :beetle:
  * Video: Use video public URL and not image public URL [livingdocs-editor #4048](https://github.com/livingdocsIO/livingdocs-editor/pull/4048) :beetle:
* Access Management: Groups - hide iMatrics for projects that don't use it [livingdocs-editor #4062](https://github.com/livingdocsIO/livingdocs-editor/pull/4062) :beetle:
* Metadata: Correctly handle image URL's when picking from article [livingdocs-editor #4132](https://github.com/livingdocsIO/livingdocs-editor/pull/4132) :beetle:
* Editor Link Tool: fix link validation / update link info / no reload on enter [livingdocs-editor #4142](https://github.com/livingdocsIO/livingdocs-editor/pull/4142) :beetle:
* Comments: Fix comment highlight when paging through comment cards [livingdocs-editor #4147](https://github.com/livingdocsIO/livingdocs-editor/pull/4147) :beetle:










  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
