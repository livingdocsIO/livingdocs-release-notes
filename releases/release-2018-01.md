
## Repositories

This release consists of the following new versions of the `livingdocs-server` and `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `66.0.x`
`@livingdocs/editor` | `27.0.x`

### Livingdocs Server

How to require the server in your package.json:

```json
"dependencies": {
  "@livingdocs/server": "66.0.x",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-server/tree/release-2018-01


### Livingdocs Editor

How to require the editor in your package.json:

```json
"dependencies": {
  "@livingdocs/editor": "27.0.x",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-editor/tree/release-2018-01



# Highlights

## Content Types - Server :fire: :gift:

**Breaking Change** The channel configurations now is based on contentTypes.

### Required Actions

* Db Migration Needed: Make sure all entries in the `documents`table in postgres have a `contentType` set (see migration)
* Elasticsearch Mappings need to be updated.
* Migrate channel configuration to the new format


### Postgres migration

For all existing documents a manual migration will have to be run before the server can be upgraded safely. We created a manual migration as this is a long running operation for databases with many documents. The migration can be found in the server in `db/manual-migrations/002-write-content-type.js`.


### Updated elasticsearch mapping

The `contentType` was added to the `documents` index.

To update the mapping run:
```bash
grunt search-index:document:update-mapping
```

### Server Configuration

Example Channel Configuration in the new format:
```js
projects: {

    // Example static channel configurations
    channelConfigurations: [{
      // If a channel has the channel `name` 'web' the channel configuration with
      // the `handle` 'web' will be used.
      handle: 'web',
      editMode: 'default',

      copy: [{
        source: {
          channelHandle: 'web',
          // If a design contains a layout gallery the content type is 'gallery'
          contentType: 'gallery'
        },
        targets: [{
          channelHandle: 'web',
          contentType: 'gallery'
        }]
      }],

      // Content Types
      contentTypes: [{
        handle: 'gallery',
        documentType: 'article',

        metadata: {},
        renditions: require.resolve('./path/to/rendition/config')
      }]
    }]
  },
```

Rendition config (the format is exactly the same as before, it just must be in a different file as it contains code and is not really a configuration):
```js
const CheerioHtml = require('../../../lib/render-pipeline/output/cheerio_html')

module.exports = {
  'web': {
    output: {
      'page-html': new CheerioHtml()
    }
  }
}
```

New copy configuration with contentTypes instead of layouts:
```js
projects:
  channelConfigurations [
    copy: [{
      source: {
        // 'channelHandle' instead of 'design'
        channelHandle: 'web',
        // 'contentType' instead of 'layout'
        contentType: 'regular'
      },
      // 'targets' instead of 'target'
      targets: [
        channelHandle: 'print',
        contentType: 'regular'
        // ...other properties remain the same
      ]
    }]  
  ]
```


### Public Api

#### GET public-api/v1/project

Changed return value with the contentType in the response
-> See the public api docs for details

#### GET public-api/v1/channels/:channelHandle

Modified return value. This is exactly the same as one channel in the project response.
(there is also a schema: `LivingdocsPublicChannel`)
-> See the public api docs for details

#### GET public-api/v1/documents/... (is it public api)

`content_type` is now included in the response
-> See the pulic api docs for details


### Editing Api

#### GET /documents

`content_type` is now included in the response
`content_type` can be used in `fields` (GET /documents?fields=content_type)
`content_type` can be used as a filter (GET /documents?content_type=article)

#### GET /project

New channel configuration is included in the response


### Feature Apis

#### documentApi.create()

`content_type` is required. It will be verified, that the `content_type` exists.
`revision.data.layout = content_type`
`document_type` is set as before. It uses the `document_type` defined in the specified `content_type` config.

#### documentCopyApi.copy()
-> requires contentType param instead of layout

#### documentCopyApi.getCopyTargets()

New Response:
```js
[{
  channelHandle: 'web'
  contentType: 'article'
}, {
  channelHandle: 'web'
  contentType: 'minimal'
}, {
  channelHandle: 'print'
  contentType: 'default'
}]
```

#### channelApi

Changes in `features.api('li-projects').channel`:

- Changed: channelApi.getRenderConfigForRenderWorker()
  -> new required param `contentType`
- Removed: channelApi.getChannelsWithLayoutsByProject()
- Removed: channelApi.getDocumentTypeConfig()
- Removed: channelApi.getPageConfig()
- Removed: channelApi.getArticleConfig()
- Removed: channelApi.getChannelConfigByChannelName()

#### projectApi

- projectsApi.getProject()

New return value:
```js
{
  id: 1,
  projectHandle: 'project-handle',
  name: 'project-handle', // deprecated
  defaultChannelId: 10, // previous: default_channel_id
  config: {},
  channels: [{
    channelHandle: 'web', // previous: name
    designName: 'timeline', // previous: design_name
    designVersion: '1.0.0', // previous: current_version
    availableVersions: [], // previous: available_versions
    disabledVersions: [], // previous: disabled_versions
    editMode: 'default', // previous: mode
    copySources: [ // previous: copy_cource_channels
      {channelHandle: 'web', contentType: 'article'}
      {channelHandle: 'web', contentType: 'minimal'}
    ],
    contentTypes: [...], // new
    pushNotifications: {...} // new
  }]
}
```

Removed:

* channels[0].config
  * channel.config.articles.copy_source_channels
  * channel.config.articles.available_versions
  * channel.config.articles.disabled_versions

Previous value for `copy_source_channels`:
```js
copy_cource_channels = [
  {design: 'basic', layout: 'default'}
  {design: 'basic', layout: 'minimal'}
]
```

### RenderPipeline

#### registerRenderHooks

`documentType` got replaced with `contentType` in the `beforeRenderHook`

```js
  # before
  const renderPipeline = liServer.features.api('li-render-pipeline')
  renderPipeline.registerRenderHooks({
    projectHandle: 'my-project',
    channelHandle: 'web',
    beforeRenderHook: ({documentType, rendition}, callback) => {
      liServer.log.warn(`Hook called for documentType: ${documentType}!`)
      callback(null, rendition)
    }
  }, done)

  # after
  const renderPipeline = liServer.features.api('li-render-pipeline')
  renderPipeline.registerRenderHooks({
    projectHandle: 'my-project',
    channelHandle: 'web',
    beforeRenderHook: ({contentType, rendition}, callback) => {
      liServer.log.warn(`Hook called for contentType: ${contentType}!`)
      callback(null, rendition)
    }
  }, done)
```

#### importApi.import()

import({importJob, rawDocument, shouldCreateNew, updateCondition, userId}, callback)
- pass `importJob.contentType` instead of `importJob.documentType`
  the passed layout will be ignored (should we implement that backwards compatible?)

[Server PR #1696](https://github.com/upfrontIO/livingdocs-server/pull/1696)


## Content Types - Editor :fire:

**Breaking Change** The editor depends on the server >= 66.x.y. Make sure all users refresh their session after the new editor is deployed.

The editor consumes contentTypes from the server through the channel configuration.
The create new document Dialog shows the information from the contentType configuration.
But the groups and defaultContent configuration are still loaded from the layouts in the design.

There is a new filter with type `contentType` that can be used in the dashboard or document searches.

[Editor PR #1759](https://github.com/upfrontIO/livingdocs-editor/pull/1759)


## Allow to replace an image by an image drop :gift:

When dragging an image from the file system over an image in the editor the image will replace said image.

[Editor PR #1796](https://github.com/upfrontIO/livingdocs-editor/pull/1796)


## Improved document history :gift: :fire:

### Editing Api

#### PUT /documents/:id

New param `force_new_revision` to force the creation of a new revision (we use that in the editor in the case a user restores an old version in the history)

#### GET /revisions

Mark on the revision (list) if a revision was created because a user published the document. The response will contain an event field that can read publish or be null (for edit).

The /revisions endpoint previously didn't require passing a `document_id`. This is now mandatory since the endpoint makes no sense without a `document_id`.

[Server PR #1762](https://github.com/upfrontIO/livingdocs-server/pull/1762)


## Extended design loader configurations :gift: :fire:

The Design Loader gets its own configuration:
```js
designLoader: {
  hostedDesigns: [{ // optional
    designName: 'timeline',
    url: 'http://assets.livingdocs.io/timeline'
  }],
  localDesigns: [{ // optional
    path: '/designs/timeline/v1.1.0' // path to design
  }],
  designRepository: { // optional, defaults to the local design server
    remoteHost: 'http://api.livingdocs.io'
  },
  cacheSize: 100 // defaults to '20'
}
```

For details see the detailed changelog in the [PR #1787](https://github.com/upfrontIO/livingdocs-server/pull/1787)

## Removed `designLoader` module in the editor :fire: :wrench:

**Breaking Change**
The module `designLoader` was removed. Use `designProxy` instead. It offers the same api.

[Editor PR #1803](https://github.com/upfrontIO/livingdocs-editor/pull/1803)


## Mark list that have pending changes with a blue dot :gift:

In the editor lists screen a blue circle is shown for lists with pending changes.

In the server the `documentListApi` returns the inbox size of every list.

[Editor PR #1792](https://github.com/upfrontIO/livingdocs-editor/pull/1792)   
[Server PR #1776](https://github.com/upfrontIO/livingdocs-server/pull/1776)


## Fix the behaviour of read-only mode during collaboration :beetle:

*Needs Clarification*

[Editor PR #1791](https://github.com/upfrontIO/livingdocs-editor/pull/1791)


# Further Changes

* Editor
  * add visibility config switch for the "transform component" in the side panel [#1793](https://github.com/upfrontIO/livingdocs-editor/pull/1793) :wrench:
  * disable copy button on saving [#1795](https://github.com/upfrontIO/livingdocs-editor/pull/1795) :beetle:
  * keep image focus after cropping [#1769](https://github.com/upfrontIO/livingdocs-editor/pull/1769) :beetle:
  * Specify homepage in project settings
  [#1767](https://github.com/upfrontIO/livingdocs-editor/pull/1767) [#1751](https://github.com/upfrontIO/livingdocs-server/pull/1751) :gift:
* Elasticsearch
  * make elasticsearch apiVersion configurable [#1754](https://github.com/upfrontIO/livingdocs-server/pull/1754) :gift:
  * replace top-level filter parameter with post_filter [#1726](https://github.com/upfrontIO/livingdocs-server/pull/1726) :wrench:
* Hooks
  * handle resolveHandle errors [#1766](https://github.com/upfrontIO/livingdocs-server/pull/1766) :beetle:
  * publication hooks registration ignores missing projects/channels [#1771](https://github.com/upfrontIO/livingdocs-server/pull/1771) :gift:
* Print
  * advanced woodwing infobox [#1710](https://github.com/upfrontIO/livingdocs-server/pull/1710) :gift:
  * send `<br>` to printAPI [#1746](https://github.com/upfrontIO/livingdocs-server/pull/1746) :wrench:
  * set publicationDates period to 30d [#1778](https://github.com/upfrontIO/livingdocs-editor/pull/1778) :wrench:
* Redis
  * use ioredis instead of node-redis [#1773](https://github.com/upfrontIO/livingdocs-server/pull/1773) :wrench:
* Design loader
  * Fix assets.public_url camelization in design-loader [#1788](https://github.com/upfrontIO/livingdocs-server/pull/1788) :wrench:
* Tests
  * Get headless chromium properly to work [#1784](https://github.com/upfrontIO/livingdocs-editor/pull/1784) :beetle:

---

  **Icon Legend**

  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
