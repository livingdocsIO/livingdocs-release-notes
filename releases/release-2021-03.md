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





# Highlights

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





## Media Library - Index/Filter :tada:

Define which media library metadata are indexed and define dashboard filter for all metadata.

TODO@meinrad - add doc for media library indexing/filter

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3389)

## Media Library - Videos :tada:

TODO@ralph are there more pr's? Create a list of improvements for video management.

References:
  * [Add Storage Config for Video](https://github.com/livingdocsIO/livingdocs-server/pull/3296)
  * [Video Storage Config Documentation](https://github.com/livingdocsIO/livingdocs/pull/350)
  * [Video Poster Image](https://github.com/livingdocsIO/livingdocs-editor/pull/4187)
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

TODO@okan / TODO@beni - add doc for Notification Center
TODO@okan - add doc for document subscriptions - https://github.com/livingdocsIO/livingdocs-server/pull/3344

References:
* [Documentation](TODO@okan TODO@beni)
* [Document Notifications](https://github.com/livingdocsIO/livingdocs-server/pull/3251)
* [Manage Document Subscriptions](https://github.com/livingdocsIO/livingdocs-server/pull/3344)
* [Manage Document Subscriptions UI](https://github.com/livingdocsIO/livingdocs-editor/pull/4013)


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



## Tracing :tada:

...add a description TODO@alex...

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3205)
  * [Documentation](TODO@alex)



## Simplify Setup of Article Teasers

A simpler way to setup teasers is introduced. It is based on Includes and the possiblity to define the UI with a `paramsSchema`.

TODO@beni - text ok?

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/359)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3385)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4152)












# Breaking Changes :fire:

## Migrate the database :fire:

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

## Revision Migration :fire:

We changed the `doc-link` and `doc-html` directives to be objects instead of strings (see next section in the release-notes to compare the :fire: old/new format).

After the deployment (when everything is running fine again) you should run the task :fire: `npx livingdocs-server revision-migration` and then choose the migration with the name `doc-link and doc-html`. This migrates all revisions to use the new data format.

The default revision migration is quite agressive regarding db load, but we recommend to choose a less agressive approach, which you can run during the day without issues.
```js
// server config for a less agressiv revision migration
documentMigration: {
   scheduler: {
        batchSize: 100, // default: 100
        concurrency: 2, // default: 10
       }
    }
}
```

The revision migration should be run through all stages of deployment (dev, stage, prod). If you run into troubles you can fine-tune the job scheduler in the configuration e.g. changing the batchSize or the concurrency.

Please make sure that all code that consumes Livingdocs (web frontend, native apps, etc.) support both formats and are still working as expected.

References:
- [Revision Migration Framework](https://github.com/livingdocsIO/livingdocs-server/pull/3268)
- [doc-link and doc-html Migration](https://github.com/livingdocsIO/livingdocs-server/pull/3268)


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


## Migrate References :fire:

As described in the [APIs](#apis-gift) section, we extend some endpoints (public API + server API) with reference information of a document. Old document references need to be converted into the new format with a manual db migration.

After the release, execute the manual db migration `node ./db/manual-migrations/006-generate-references`

These are the key changes/issues
- It's a database heavy operation and should be executed outside business time (when having a lot of documents)
- generate document and publication references and store them on the db
- remove document revision references (TODO@alex what are the consequences for public- and serverAPIs?)

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3341)


## CLI Script to Fix Group Memberships :fire:

We're having some customers running an old state of the groups tables which got partially corrupted by some old user merge logic that we've fixed about a year ago. The new `npx livingdocs-server fix-group-memberships` command fixes those tables completely.

- :fire: Run `npx livingdocs-server fix-group-memberships` to fix corrupt membership data

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3418)


## Remove Legacy Postgres Tables :fire:

These Postgres tables have been removed:
- `assets` - got replaced by `media_library_entries` earlier last year
- `access_tokens` - The access_tokens table got removed in release-2020-12 as we now only track session ids
- `category_events` - This table wasn't in use at all
- `import_hugo_feeds` - This table also got created about 4 years ago and isn't in use

:fire: Please make sure that you don't directly access those tables in your code.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3386)


## Remove Grunt Tasks :fire:

Removed all Grunt tasks. If you still need a task, you can just copy the code to your downstream. But almost all functionality has been replaced with `livingdocs-server` CLI and the editor administration UI.
Please give us some feedback when you miss some functionality of a Grunt task, so we can provide that in the future in another form.

- 🔥 remove `grunt channel-create`
- 🔥 remove `grunt channel`
- 🔥 remove `grunt data-migration-create-and-prepare`
- 🔥 remove `grunt data-migration-accept`
- 🔥 remove `grunt data-migration-list`
- 🔥 remove `grunt data-migration-get`
- 🔥 remove `grunt data-migration-cancel`
- 🔥 remove `grunt data-migration-resume-all`
- 🔥 remove `grunt data-migration-get-report`
- 🔥 remove `grunt data-migration-list-errors`
- 🔥 remove `grunt data-migration`
- 🔥 remove `grunt list-create`
- 🔥 remove `grunt list-edit`
- 🔥 remove `grunt list`
- 🔥 remove `grunt project-create`
- 🔥 remove `grunt project`
- 🔥 remove `grunt user-authenticate`
- 🔥 remove `grunt user-password`
- 🔥 remove `grunt user-password-lock`
- 🔥 remove `grunt user-email`
- 🔥 remove `grunt user-edit`
- 🔥 remove `grunt user-create`
- 🔥 remove `grunt user-create-admin`
- 🔥 remove `grunt user-delete`
- 🔥 remove `grunt user`
- 🔥 remove `grunt webhook-subscribe`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3399)


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

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4106)


### Webhook Payload Change (publish/unpublish) :fire:

- :fire: Document publish webhook, changed value of `event` from `document.published` to `document.publish`
- :fire: Document unpublish webhook, changed value of `event` from `document.unpublished` to `document.unpublish`

TODO@okan: Update business documentation (update old payload formats, add new media library payloads)

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3359)


### Prefix all app Routes with a Project Handle :fire:

#### Rename UI Router Application States 'app' -> 'project'
🔥 We renamed all ui router application states. All states for the editor routing are affected.
Examples, where it could be used in customer projects are:
- `ui-sref`
- `$state.go('')`
- `state.$href`
- or within the project config the `mainNavigation` may also be affected if it uses editor states instead of urls.

In most cases this is the easy migration guide for almost all states prefixed with 'app.*'
**Before**: `$state.go('app.welcome')`
**After**: `$state.go('project.welcome')`

_Note: Exception are server admin routes route like 'app.admin.users' is still 'app.admin.users' and user routes like 'app.user'_


#### Rename Project Routes/States

:fire: Changed url schema from `/projects/id/*` to `/p/projectHandle/config/*`
```js
// Example
https://0.0.0.0:9000/projects/111/settings           // from
https://0.0.0.0:9000/p/e2e-magazine/config/settings  // to
```

:fire: Changed state from `app.settings*` to `project.config*`
```js
// Example
return this.$state.go('project.settings.contentType.content')   // from
return this.$state.go('project.config.contentType.content')     // to
```

:fire: Changed url schema from `/access/id/*` to `/p/projectHandle/admin/*`
```js
// Example
https://0.0.0.0:9000/access/111/members            // from
https://0.0.0.0:9000/p/e2e-magazine/admin/members  // to
```

:fire: Changed state from `app.access*` to `project.admin*`
```js
// Example
return this.$state.go('project.access.current.groups')   // from
return this.$state.go('project.admin.current.groups')    // to
```

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4171)


### Upload Media Assets via Streams instead of a Buffer :fire:

- :fire: removed `mediaLibraryApi.addImageCb`, use `mediaLibraryApi.addImage` (promise) instead
- :fire: changed `mediaLibraryApi.addImages({..., tempBase64})` to `mediaLibraryApi.addImages({..., stream})` (pass an image stream for an exif extraction)
- :fire: `imagesApi.processJob` does not support callbacks anymore
- :fire: changed `designsApi.write.uploadAsset({..., file})` to `designsApi.write.uploadAsset({..., readStream})`. Instead of passing a `buffer` you have to pass a `readStream`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3396)


### Render Pipeline CheerioHtml: Use onTimeRendering by default :fire:

If you use custom outputFormatters which use the frameworks rendering you should switch them to `livingdoc.render()`. This gives you a big performance boost (10x - 20x faster) and ensures consistency with the new default of the CheerioHtml output renderer.

```js
// current - slow
html = rendition.livingdoc.toHtml()

// better alternative - fast
html = rendition.livingdoc.render()
```

You can still use the old renderer with `CheerioHtml({useLegacyRendering: true})` in your `contentType` configuration.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3401)



### Include Api Refactoring :fire:

- 🔥 `includeApi.registerService()` We're sunsetting of the old service config format which used ui and server properties instead of the new format with uiComponents and rendering. This format has been deprecated with a logged warning for a few years now. If the server starts successfully you don't use the old format.
- 🔥 Removed `includeApi.resolveChannelOutputs()` (but this function should only have been used internally)

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3405)


### Group Api - Optimistic Locking :fire:

:fire: `groupApi.updateGroup({..., version})` - version changed the optimistic locking behavior. Previously when doing an update against a group, the version must have been +1 of the state on the server. When doing requests from now on, the version in the request must match the version on the server.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3449)

### Woodwing Asset Api :fire:

:fire: removed url from `woodwingAssetsApi.uploadImageToWoodwingAssets({..., url})` and added stream (readStream) `woodwingAssetsApi.uploadImageToWoodwingAssets({..., stream})`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3437)

### Media Library Filter :fire:

- 🔥 Media Library Index: `caption`, `source` and `google-vision` fields are not indexed automatically anymore. The config `config: {index:true}` must be set in the metadata configuration.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3389)








# Deprecations

## Node 12 Support

💣 Node 12 is deprecated. Please upgrade your docker images and local environments to node 14.

This follows our upgrade cycle that we drop the old lts version one year after the introduction of the [current LTS version](https://nodejs.org/en/about/releases/).

In your docker images change
- `FROM livingdocs/server-base:12` to `FROM livingdocs/server-base:14` or `:15`
- `FROM livingdocs/editor-base:12` to `FROM livingdocs/editor-base:14` or `:15`
- `FROM livingdocs/node:12` to `FROM livingdocs/node:14` or `:15`

In your `.nvmrc` (if present) change
- The string from `12` to `14` or `15`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3442)


## swisscomTV.customLanguageHandle

The server config `swisscomTV.customLanguageHandle` is not used any longer for the reference extraction. All metadata of type `li-language` will be extracted to the references if they have a `groupId`.




# APIs :gift:

## Publication Events

TODO@marc - update public API doc (incl. backport)

- :candy: Support `/api/v1/publicationEvents?reverse=true` query parameter to retrieve events in reverse order starting at the latest event

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3447)

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

- 🎁 Add new endpoint `GET /api/beta/documents/:documentId/incomingDocumentReferences`
- :candy: `GET /api/beta/documents/:documentId/latestPublication` - add next extracted references format
- :candy: `GET /api/beta/documents/:documentId/latestPublications` - add next extracted references format
- 🎁 Add new endpoint `GET /api/beta/documents/:documentId/incomingMediaReferences`
- 🎁 Add new endpoint `GET /api/beta/mediaLibrary/:mediaId/incomingDocumentReferences`
- 🎁 Add new endpoint `GET /api/beta/mediaLibrary/:mediaId/incomingMediaReferences`

References:
* [Documentation](TODO@alex)
* [Add Endpoints PR I](https://github.com/livingdocsIO/livingdocs-server/pull/3365)
* [Add Endpoints PR II](https://github.com/livingdocsIO/livingdocs-server/pull/3400)


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

## Colt

```js
// Simple import of all colt factories
const {colt} = require('../support/factories')
// --> instead of require('../support/factories').get('user', 'project', 'channel', 'document', 'publication')


// New Test Helper to create a configurable Project.
colt().createConfigProject('project', {...})
```


# Other Changes

### Design

* Priority truck polish [livingdocs-editor #4091](https://github.com/livingdocsIO/livingdocs-editor/pull/4091) :gift:
* Style Guide: Clean up the style guide [livingdocs-editor #4149](https://github.com/livingdocsIO/livingdocs-editor/pull/4149) :gift:


### Features

* Tasks: Assign users to a task [livingdocs-editor #4214](https://github.com/livingdocsIO/livingdocs-editor/pull/4214) :gift:
* Print: Move print to project config [livingdocs-server #3372](https://github.com/livingdocsIO/livingdocs-server/pull/3372) :gift:
  * TODO@gabriel - add documentation to the doc repo

### Improvements

* Dashboards
  * Properly handle pagination for a resultList [livingdocs-editor #4153](https://github.com/livingdocsIO/livingdocs-editor/pull/4153) :gift:
  * List dashboard: Hide 'go to article' button in list UI when dragging [livingdocs-editor #4094](https://github.com/livingdocsIO/livingdocs-editor/pull/4094) :gift:
  * Add 'video-' and 'imageLibrary' dashboard [livingdocs-editor #4046](https://github.com/livingdocsIO/livingdocs-editor/pull/4046) :gift:
* Media Upload/Import
  * Remove hardcoded mediaTypes + Bugfixes [livingdocs-editor #4155](https://github.com/livingdocsIO/livingdocs-editor/pull/4155) :gift:
  * Simplify code [livingdocs-server #3369](https://github.com/livingdocsIO/livingdocs-server/pull/3369) :gift:
  * Allow multiple mediaTypes of same type, allow mediaType parameter for upload/import APIs [livingdocs-server #3406](https://github.com/livingdocsIO/livingdocs-server/pull/3406) :gift:
  * Hardening Media Library Import [livingdocs-server #3430](https://github.com/livingdocsIO/livingdocs-server/pull/3430) :gift:
  * Reimplement `video.asset.size` support for the stream-based upload [livingdocs-server #3439](https://github.com/livingdocsIO/livingdocs-server/pull/3439) :gift:
* Webhooks: Add media library webhooks | extend document.update webhook with metadata filter [livingdocs-server #3359](https://github.com/livingdocsIO/livingdocs-server/pull/3359) :gift:
* Editor
  * Image cropping: Use downscaled image size for very large images [livingdocs-editor #4141](https://github.com/livingdocsIO/livingdocs-editor/pull/4141) :gift:
  * Editing: Add Iframe height watcher (guard) [livingdocs-editor #4108](https://github.com/livingdocsIO/livingdocs-editor/pull/4108) :gift:
* CLI
  * Add 'newerThan' argument for task 'cleanup-documents' [livingdocs-server #3333](https://github.com/livingdocsIO/livingdocs-server/pull/3333) :gift:
* Import
  * Support files with no file ending of mimeType image [livingdocs-server #3380](https://github.com/livingdocsIO/livingdocs-server/pull/3380) :gift:
* Search
  * Add support for a `customFilters` object to pass through custom search parameters [livingdocs-editor #4172](https://github.com/livingdocsIO/livingdocs-editor/pull/4172) :gift: -> TODO@marc - add doc to business doc
* Error handling: Add extended description to error declaration class [livingdocs-server #3214](https://github.com/livingdocsIO/livingdocs-server/pull/3214) :gift:
* Administration
  * Extend the indexing UI screen to support all configured indexes [livingdocs-server #3409](https://github.com/livingdocsIO/livingdocs-server/pull/3409) :gift:
* Add Support for Secure Imgix URLs [livingdocs-server #3410](https://github.com/livingdocsIO/livingdocs-server/pull/3410) :gift:
* Includes: Add interaction blocker config option [livingdocs-server #3397](https://github.com/livingdocsIO/livingdocs-server/pull/3397) :gift:
* Security: Revoke client if another user uses the same client id [livingdocs-server #3441](https://github.com/livingdocsIO/livingdocs-server/pull/3441) :gift:
* Filter: allow document_types to be an array [livingdocs-server #3412](https://github.com/livingdocsIO/livingdocs-server/pull/3412) :gift:


### Bugfixes

* Media library
  * Rename pusher topic to media and allow - in mediaId [livingdocs-server #3382](https://github.com/livingdocsIO/livingdocs-server/pull/3382) :beetle:
  * Video: Use video public URL and not image public URL [livingdocs-editor #4048](https://github.com/livingdocsIO/livingdocs-editor/pull/4048) :beetle:
* Access Management: Groups - hide iMatrics for projects that don't use it [livingdocs-editor #4062](https://github.com/livingdocsIO/livingdocs-editor/pull/4062) :beetle:
* Metadata: Correctly handle image URL's when picking from article [livingdocs-editor #4132](https://github.com/livingdocsIO/livingdocs-editor/pull/4132) :beetle:
* Editor Link Tool: fix link validation / update link info / no reload on enter [livingdocs-editor #4142](https://github.com/livingdocsIO/livingdocs-editor/pull/4142) :beetle:
* Comments: Fix comment highlight when paging through comment cards [livingdocs-editor #4147](https://github.com/livingdocsIO/livingdocs-editor/pull/4147) :beetle:















































EDITOR
------------------------
* v63.8.3 Fix group screen errors [release-2021-03]  [livingdocs-editor #4227](https://github.com/livingdocsIO/livingdocs-editor/pull/4227) :gift:
* v63.8.3 fix(publish screen): don't log errors to console when MetadataValidationErrors are returned for publish request [release-2021-03]  [livingdocs-editor #4223](https://github.com/livingdocsIO/livingdocs-editor/pull/4223) :gift:
* v63.8.2 Fix group screen errors [release-2021-03]  [livingdocs-editor #4227](https://github.com/livingdocsIO/livingdocs-editor/pull/4227) :gift:
* v63.8.1 fix(comments): Show max thread count limit error [livingdocs-editor #4188](https://github.com/livingdocsIO/livingdocs-editor/pull/4188) :gift:

* v63.7.1 fix: Check that imageDirectives is defined before accessing it [livingdocs-editor #4219](https://github.com/livingdocsIO/livingdocs-editor/pull/4219) :gift:
* v63.7.0 Add unsubscribe url [livingdocs-editor #4218](https://github.com/livingdocsIO/livingdocs-editor/pull/4218) :gift:
* v63.6.1 Add block editor interaction to Project Config > Include Services UI [livingdocs-editor #4205](https://github.com/livingdocsIO/livingdocs-editor/pull/4205) :gift:
* v63.6.0 Upload Center [livingdocs-editor #4145](https://github.com/livingdocsIO/livingdocs-editor/pull/4145) :gift:
* v63.5.4 Improvement External Sources [livingdocs-editor #4215](https://github.com/livingdocsIO/livingdocs-editor/pull/4215) :gift:

* v63.5.2 Improve Dashboard Footer [livingdocs-editor #4209](https://github.com/livingdocsIO/livingdocs-editor/pull/4209) :gift:
* v63.5.1 show notifications action card only when it is enabled [livingdocs-editor #4208](https://github.com/livingdocsIO/livingdocs-editor/pull/4208) :gift:
* v63.4.1 Fix document.metadata.update support in the policies [livingdocs-editor #4206](https://github.com/livingdocsIO/livingdocs-editor/pull/4206) :gift:
* v63.3.2 fix(conflict-bar): Position sidebar below collab & conflict bar [livingdocs-editor #4201](https://github.com/livingdocsIO/livingdocs-editor/pull/4201) :gift:
* v63.3.1 Rename project routes  [livingdocs-editor #4183](https://github.com/livingdocsIO/livingdocs-editor/pull/4183) :gift:
* v63.2.3 Fix project not found error [livingdocs-editor #4197](https://github.com/livingdocsIO/livingdocs-editor/pull/4197) :gift:
* v63.2.2 fix: users should not get in redirect loops [livingdocs-editor #4194](https://github.com/livingdocsIO/livingdocs-editor/pull/4194) :gift:
* v63.2.1 Fix the ci builds [livingdocs-editor #4195](https://github.com/livingdocsIO/livingdocs-editor/pull/4195) :gift:
* v63.1.3 Fix media library [livingdocs-editor #4189](https://github.com/livingdocsIO/livingdocs-editor/pull/4189) :gift:
* v63.1.1 fix: guard projects from having a undefined handle in the url [livingdocs-editor #4182](https://github.com/livingdocsIO/livingdocs-editor/pull/4182) :gift:
* v63.1.0 Media Library Dashboards in Main Navigation from mediaTypes config [livingdocs-editor #4180](https://github.com/livingdocsIO/livingdocs-editor/pull/4180) :gift:
* v63.0.0 Remove deprecated editor env config 'dashboards' [livingdocs-editor #4166](https://github.com/livingdocsIO/livingdocs-editor/pull/4166) :gift:

* v61.4.0 chore(includes): Add blockEditorInteraction to test [livingdocs-editor #4181](https://github.com/livingdocsIO/livingdocs-editor/pull/4181) :gift:
* v61.3.4 fix(named crops): fix resetting to automatic crops after user change [livingdocs-editor #4179](https://github.com/livingdocsIO/livingdocs-editor/pull/4179) :gift:
* v61.3.3 fix(metadata image): fix picking an image from media library [livingdocs-editor #4177](https://github.com/livingdocsIO/livingdocs-editor/pull/4177) :gift:
* v61.3.2 Add Support for Secure Imgix URLs [livingdocs-editor #4176](https://github.com/livingdocsIO/livingdocs-editor/pull/4176) :gift:
* v61.3.1 Fix Image Cropper on Mobile [livingdocs-editor #4175](https://github.com/livingdocsIO/livingdocs-editor/pull/4175) :gift:
* v61.1.1 fix(references): Convert reference id to string [livingdocs-editor #4173](https://github.com/livingdocsIO/livingdocs-editor/pull/4173) :gift:
* v61.0.4 Move some print config to project config [livingdocs-editor #4130](https://github.com/livingdocsIO/livingdocs-editor/pull/4130) :gift:
* v61.0.3 Fix editor.workspace references [livingdocs-editor #4170](https://github.com/livingdocsIO/livingdocs-editor/pull/4170) :gift:
* v61.0.2 Correctly go back from publish screen to articles/dashboards [livingdocs-editor #4168](https://github.com/livingdocsIO/livingdocs-editor/pull/4168) :gift:
* v61.0.1 Upgrade axios and increase timeouts for upload [livingdocs-editor #4167](https://github.com/livingdocsIO/livingdocs-editor/pull/4167) :gift:
* v61.0.0 Drop coffee-script support [livingdocs-editor #4164](https://github.com/livingdocsIO/livingdocs-editor/pull/4164) :gift:

* v60.1.3 fix: update framework to 18.3.0 [livingdocs-editor #4162](https://github.com/livingdocsIO/livingdocs-editor/pull/4162) :gift:
* v60.1.2 fix: correctly navigate back from a custom dashboard [livingdocs-editor #4158](https://github.com/livingdocsIO/livingdocs-editor/pull/4158) :gift:
* v60.1.1 Fix x-forwarded-proto support [livingdocs-editor #4156](https://github.com/livingdocsIO/livingdocs-editor/pull/4156) :gift:
* v60.1.0 Properly Handle Pagination for a ResultList [livingdocs-editor #4153](https://github.com/livingdocsIO/livingdocs-editor/pull/4153) :gift:







  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
