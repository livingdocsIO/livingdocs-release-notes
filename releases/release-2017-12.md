# Release Notes: `November/December 2017 Release`

## Repositories

This release consists of the following new versions of the `livingdocs-server`, the `livingdocs-editor` and the `livingdocs-framework`:

Package | Version
--- | ---
`@livingdocs/server` | `64.0.1`
`@livingdocs/editor` | `25.3.1`
`@livingdocs/framework` | `8.0.5`

### Livingdocs Server

How to require the server in your package.json:

```json
"dependencies": {
  "@livingdocs/server": "64.0.1",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-server/tree/release-2017-12
- Previous release: [63.2.1](https://github.com/upfrontIO/livingdocs-release-notes/blob/master/releases/release-2017-10.md#livingdocs-server)

### Livingdocs Editor

How to require the editor in your package.json:

```json
"dependencies": {
  "@livingdocs/editor": "25.3.1",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-editor/tree/release-2017-12
- Previous release: [23.0.3](https://github.com/upfrontIO/livingdocs-release-notes/blob/master/releases/release-2017-10.md#livingdocs-editor)

### Livingdocs Framework

The framework is already integrated in the package.json of the upstream server and editor. It's **not** necessary to integrate the framework from your side.

The framework does not have a release branch.

How to require the framework in your package.json:

```json
dependencies: {
  "@livingdocs/framework": "8.0.5"
}
```
- Previous release: [7.14.0](https://github.com/upfrontIO/livingdocs-release-notes/blob/master/releases/release-2017-10.md#livingdocs-framework)

## Breaking Changes

Component | Type | Description | PRs | Issues
--- | --- | --- | --- | ---
Server | BREAKING CHANGE | Publication hooks [Read more](#publication-hooks) | [#1740](https://github.com/upfrontIO/livingdocs-server/pull/1740) | [#1633](https://github.com/upfrontIO/livingdocs-planning/issues/1633)
Editor | BREAKING CHANGE | Remove metadataConfigService [Read more](#remove-metadataconfigservice) | [#1726](https://github.com/upfrontIO/livingdocs-editor/pull/1726) | -
Application wide | BREAKING CHANGE | Move image service config to the server only [Read more](#move-image-service-config-to-the-server-only) | [#268](https://github.com/upfrontIO/livingdocs-framework/pull/268), [#1708](https://github.com/upfrontIO/livingdocs-server/pull/1708), [#1746](https://github.com/upfrontIO/livingdocs-editor/pull/1746) | [#1532](https://github.com/upfrontIO/livingdocs-planning/issues/1532)

### Publication Hooks

The behaviour of `registerPublicationHooks` changes. It allowed registering one `publishHook` and one `unpublishHook` on a channel, it now allows registering many of each of these.

- **Before:** any subsequent call to `registerPublicationHooks` for the same channel would simply override/replace the already registered hooks for this channel.
- **From now on:** subsequent calls add the hooks to the list of hooks that are run during (un)publication. They are executed in the same order as they get registered.

### Remove metadataConfigService

Removed the angular service `metadataConfigService`.

You can replace:
- `metadataConfigService.getConfig` with `editor.workspace.metadataForm.getFormConfig`.
- `metadataConfigService.getService` with `editor.workspace.metadataForm.getService`.

`metadataConfigService` is an internal service, but was used by some customers. `editor.workspace.metadataForm` is an internal service too, but is currently the only alternative to have the same effect.

### Move image service config to the server only

We removed the default configuration `imageServices.sz.shaSecret`. Here is an example how to manually set the `shaSecret` should you need it:

```js
  documents: {
    imageServices: {
      'sz': {
        host: 'https://sz.de',
        shaSecret: 'please-change-me-in-the-server-configuration',
        hashVersion: 1,
        srcSet: {
          defaultWidth: 1280,
          widths: [2048, 1280, 980, 720],
          sizes: ['(max-width: 980px) 80vw', '(max-width: 720px) 100vw', '60vw']
        }
      }
    }
  }
```

Here is an example change for the `resrc.it` image service:

Remove the `imageServiceConfig` key in the editor's configuration, from:

```coffee
app:
    imageService: 'resrc.it'
    imageServiceConfig:
      host: 'https://app.resrc.it'
      quality: 75
      scriptUrl: '//d2o08py1e264ss.cloudfront.net/assets/resrc-0.9.0.min.js'
```

To:

```coffee
app:
    imageService: 'resrc.it'
```

Make sure to replicate the configuration you removed from the editor in the server, like:

```js
  documents: {
    imageServices: {
      'resrc.it': {
        host: 'https://app.resrc.it',
        quality: 75,
        scriptUrl: '//d2o08py1e264ss.cloudfront.net/assets/resrc-0.9.0.min.js'
      }
    }
  }
```

## Highlighted Changes

Component | Type | Description | PRs | Issues
--- | --- | --- | --- | ---
Server | Feature | Prometheus routes indexer metrics [Read more](#prometheus-routes-indexer-metrics) | [#1678](https://github.com/upfrontIO/livingdocs-server/pull/1678), [#1689](https://github.com/upfrontIO/livingdocs-server/pull/1689) | [#1570](https://github.com/upfrontIO/livingdocs-planning/issues/1570)
Server | Feature | Add ServerApi method destroy() [Read more](#add-serverapi-method-destroy) | [#1690](https://github.com/upfrontIO/livingdocs-server/pull/1690) | -
Server | Feature | Return menus with document IDs when routing is disabled | [#1674](https://github.com/upfrontIO/livingdocs-server/pull/1674) | [#1580](https://github.com/upfrontIO/livingdocs-planning/issues/1580)
Server | Feature | Add publications resource to public API [Read more](add-publications-resource-to-public-api) | [#1664](https://github.com/upfrontIO/livingdocs-server/pull/1664) | [#1552](https://github.com/upfrontIO/livingdocs-planning/issues/1552)
Server | Feature | Make channelHandle optional in Public API [Read more](#make-channelhandle-optional-in-public-api) | [#1688](https://github.com/upfrontIO/livingdocs-server/pull/1688) | [#1599](https://github.com/upfrontIO/livingdocs-planning/issues/1599)
Server | Bugfix | Fix group duplicated entries in group table | [#1725](https://github.com/upfrontIO/livingdocs-server/pull/1725) | [#1626](https://github.com/upfrontIO/livingdocs-planning/issues/1626)
Server | Bugfix | Handle repeated drag-and-drop imports properly [Read more](#handle-repeated-drag-and-drop-imports-properly) | [#1723](https://github.com/upfrontIO/livingdocs-server/pull/1723) | [#1613](https://github.com/upfrontIO/livingdocs-planning/issues/1613), [#1614](https://github.com/upfrontIO/livingdocs-planning/issues/1614)
Server | Bugfix | Escape HTML entities for non-body fields [Read more](#escape-html-entities-for-non-body-fields) | [#1744](https://github.com/upfrontIO/livingdocs-server/pull/1744) | -
Server | Bugfix | Get default Channel Id from Project config if neither handle nor id available [Read more](#get-default-channel-id-from-project-config-if-neither-handle-nor-id-available) | [#1749](https://github.com/upfrontIO/livingdocs-server/pull/1749) | [#1641](https://github.com/upfrontIO/livingdocs-planning/issues/1641)
Server | Feature | Map article design layout to layout engine [Read more](#map-article-design-layout-to-layout-engine) | [#1655](https://github.com/upfrontIO/livingdocs-server/pull/1655), [#1697](https://github.com/upfrontIO/livingdocs-editor/pull/1697) | [#1550](https://github.com/upfrontIO/livingdocs-planning/issues/1550)
Editor | Feature | Handle the new Metadata Configuration Format in the editor | [#1718](https://github.com/upfrontIO/livingdocs-editor/pull/1718) | [#1583](https://github.com/upfrontIO/livingdocs-planning/issues/1583)
Editor | Feature | Allow linking to an external site in the main menu | [#1732](https://github.com/upfrontIO/livingdocs-editor/pull/1732) | -
Editor | Feature | Inline error messages for metadata screen [Read more](#inline-error-messages-for-metadata-screen) | [#1753](https://github.com/upfrontIO/livingdocs-editor/pull/1753) | [#1491](https://github.com/upfrontIO/livingdocs-planning/issues/1491)
Editor | Feature | As an editor I want to set an anchor link | [#1704](https://github.com/upfrontIO/livingdocs-editor/pull/1704) | [#1472](https://github.com/upfrontIO/livingdocs-planning/issues/1472)
Editor | Bugfix | Only show active groups in "Add Member" screen on project | [#c2b89c3](https://github.com/upfrontIO/livingdocs-editor/commit/c2b89c3) | -
Framework | Feature | New server side one-time rendering (without jQuery and jsdom) [Read more](#new-server-side-one-time-rendering-without-jQuery-and-jsdom) | [#161](https://github.com/upfrontIO/livingdocs-framework/pull/161) | -
Framework | Bugfix | Webpack 3 upgrade | [#272](https://github.com/upfrontIO/livingdocs-framework/pull/272) | -
Framework | Bugfix | Bump upfront-editable from 1.3.1 to 1.4.2 | [#275](https://github.com/upfrontIO/livingdocs-framework/pull/275) | -

## Changes

Component | Type | Description | PRs | Issues
--- | --- | --- | --- | ---
Server | Bugfix | Don't unescape HTML entities on import | [#1742](https://github.com/upfrontIO/livingdocs-server/pull/1742) | -
Server, Editor | Bugfix | Respect `^release-` instead of `^maintenance-` | [#1748](https://github.com/upfrontIO/livingdocs-server/pull/1748), [#1764](https://github.com/upfrontIO/livingdocs-editor/pull/1764) | -
Editor | Bugfix | Avoid hiding of floated elements in Proofreading UI | [#1596](https://github.com/upfrontIO/livingdocs-editor/pull/1596) | -
Server | Feature | Add `template-data` endpoint [Read more](#add-template-data-endpoint-to-improve-editor-code) | [#1737](https://github.com/upfrontIO/livingdocs-server/pull/1737), [#1756](https://github.com/upfrontIO/livingdocs-editor/pull/1756) | -
Server | Bugfix | The DocumentVersion passed to metadataApi.updateOnUpdate() has an old revision | [#1714](https://github.com/upfrontIO/livingdocs-server/pull/1714) | [#1617](https://github.com/upfrontIO/livingdocs-planning/issues/1617)
Server | Bugfix | Escape all `&`s in text instead of just the first occurrence | [#1733](https://github.com/upfrontIO/livingdocs-server/pull/1733) | -
Server | Bugfix | Properly parse `prometheusExporter__enabled` | [#1713](https://github.com/upfrontIO/livingdocs-server/pull/1713) | -
Server, Editor | Feature | Add codeship integration test configuration for downstreams | [#1706](https://github.com/upfrontIO/livingdocs-server/pull/1706), [#1745](https://github.com/upfrontIO/livingdocs-editor/pull/1745) | -
Server | Bugfix | Add fatal log level to the list of valid levels | [#1691](https://github.com/upfrontIO/livingdocs-server/pull/1691) | -
Server | Bugfix | Escape ampersands from hugo sources | [#1677](https://github.com/upfrontIO/livingdocs-server/pull/1677) | [#1549](https://github.com/upfrontIO/livingdocs-planning/issues/1549)
Server | Feature | Migrate render pipeline lib to js | [#1686](https://github.com/upfrontIO/livingdocs-server/pull/1686) | -
Editor | Bugfix | Use headless chrome for tests | [#1711](https://github.com/upfrontIO/livingdocs-editor/pull/1711) | -
Editor | Bugfix | Configuration for the maximum amount of selectable items in multi-select | [#1736](https://github.com/upfrontIO/livingdocs-editor/pull/1736) | -
Editor | Bugfix | Hide Metadata on Publish Panel When There is no FormArrangement Config | [#1713](https://github.com/upfrontIO/livingdocs-editor/pull/1713) | -
Editor, Server | Bugfix | Add publication selection to print article create dialog | [#1740](https://github.com/upfrontIO/livingdocs-editor/pull/1740), [#1705](https://github.com/upfrontIO/livingdocs-server/pull/1705) | - 
Editor | Bugfix | Fix export / publish label for print articles | [#1757](https://github.com/upfrontIO/livingdocs-editor/pull/1757) | -
Editor | Bugfix | Removed hardcoded publication name | [#1760](https://github.com/upfrontIO/livingdocs-editor/pull/1760) | -
Editor | Bugfix | Enable selection mode button for print | [#1721](https://github.com/upfrontIO/livingdocs-editor/pull/1721) | -
Editor | Bugfix | addTask method invocation | [#1725](https://github.com/upfrontIO/livingdocs-editor/pull/1725) | -
Framework | Bugfix | Revert usage of es2015 | [#271](https://github.com/upfrontIO/livingdocs-framework/pull/271) | -
Framework | Bugfix | Remove unused semantic-release-verify-patch | [#274](https://github.com/upfrontIO/livingdocs-framework/pull/274) | -

## In detail

### Inline error messages for metadata screen

We've updated the documentation regarding the feature: https://docs.livingdocs.io/walkthroughs/metadata/metadata-examples.html and https://docs.livingdocs.io/reference-docs/editor-configuration/metadata.html.

### Add `template-data` endpoint to improve editor code

- Allows querying the layout engine for a "standing type" (German: Stehsatz) issue date that is specified in the config. Such an issue is used to store articles that are written beforehand for which the actual issue date is not yet known.

- Currently the editor fires three requests for `publications`, `departments` and `templates`/`layouts` to populate the print template selection view. With this new endpoint all requests are combined and logic can be moved to the server cleaning up the editor code.

### Handle repeated drag-and-drop imports properly

Whether a document is imported automatically (Bluewin) or via huGO drag and drop (NZZ), it makes use of the Import API. This API creates (or in the case of Bluewin sometimes updates) a document and then stores it. A log entry is written to the `imports` table which looks like the following:

id | system_name | external_id | document_id | checksum | created_at | updated_at | project_id | channel_id | revision_id | version
-- | -- | -- | -- | -- | -- | -- | -- | -- | -- | --
2 | hugo-resource | articleAgency-236480311 | 5 | 2017-11-24T17:02:00.000+01:00 | 2017-11-24 16:16:32.477+00 | 2017-11-24 16:35:43.606+00 | 1 | 1 | 5 | 3

There's a unique-constraint on `external_id`. For Bluewin we need to make sure that each article is imported only once and in this case the log is append-only. 

For NZZ it's different: A huGO article might be imported multiple times. In case of a repeated import the log entry is simply forgone. As a consequence the issue in the linked issues arrises: When re-importing an article, the first document that remains referenced in the log entry is returned to the editor (the re-imported document has been correctly created and is visible in the dashboard).

#### ImportAPI approach: `import()` creates new ImportLogs when `shouldCreateNew` is true

When `shouldCreateNew` is set to true then the ImportAPI creates separate ImportLogs for each Import. This solves all issues described above.
The `system_name` is set to null in the drag-and-drop case so the unique constraint on the database doesn't apply and duplicate recognition still works for the automatic importer in the Bluewin project where the `system_name` is always set.
The unique constraint also has been enhanced to include `channel_id` in addition to `system_name` and `external_id`.

### Make channelHandle optional in Public API 

We'd like users of the _Public API_ to not need to handle channels since there's probably going to be one channel per project anyway. In this first step we're going to make the `channelHandle` optional, other than that, the API is going to behave as usual.

#### API Token changes

The API token now holds the default channel id as well. E.g. in the public API controller we now can do:

```js
getChannel (req, res) {
  const projectId = req.verifiedToken.projectId
  const channelId = req.verifiedToken.channelId
  // ...
},
```

#### Publication Hooks

See [breaking changes](#publication-hooks).

##### New param `prepublishHook` for `registerPublicationHooks.hooks`

Prepublish hooks need to pass to their callback `{documentVersion}` as they received one.  
This allows for subsequent prepublish hooks to modify the `{documentVersion}`.

```diff
 liServer.features.api('li-documents').registerPublicationHooks({
   projectHandle: 'your-awesome-project',
   channelHandle: 'some-channel',
+  prepublishHook: (documentVersion, callback) => { callback(null, documentVersion) },
+  //                                                              ^^^^^^^^^^^^^^^
+  //                          very important, you need to forward documentVersion
   publishHook: ({documentType, payload}, callback) => { callback() },
   unpublishHook: ({documentType, payload}, callback) => { callback() }
 }, done)
```

##### Server-wide publication hooks

There are now two ways of registering a publication hook:

* `registerPublicationHooks`:
  Hooks are tied to the project+channel passed as first argument.
* `registerPublicationServerHooks`:
  Hooks are executed on all projects. These hooks run before channel specific ones.

#### Public API changes

* `/channels/:channelHandle?` -> `publicApi.getChannelConfig ({projectId, channelId, channelHandle}, callback)`
* `/publicationEvents/:channelHandle?` -> _see [PublicationEventsRepository](#publicationeventsrepository)_
* `/routing/:channelHandle?` -> `publicApi.getRoutesForChannel ({projectId, channelId, channelHandle, path}, callback)`
* `/menus/:channelHandle?'` -> `publicMenuApi.getMenus: ({projectId, channelId, channelHandle, menuHandle}, callback)`

`/resource/` and `/resource` are now valid routes - i.e. `/channels/` and `/channels`.

#### PublicationEventsRepository
`getByChannelId({projectId, channelId, limit, after, documentType}, callback)`

This new function works analogous to `getByChannelHandle`. It returns a list of publication events. It takes `channelId` as a parameter instead of `channelHandle`.

#### Configuration changes
There are no changes in the configuration.

#### Notes

1. The Public API controller now makes one additional call to fetch the project configuration in case the channelHandle is missing, We don't know about performance impacts yet, but this is certainly a point of interest. One way to mitigate the impact on performance is to assign the default `channelHandle` to the users' tokens.
1. The default channel id is now kept in the user's API token. This saves us one roundtrip to the database.


### Enable `publications` endpoint

The new endpoint gets a list of publications supported by the layout engine for display and selection in the editor. Previously the publication for a print article was hardcoded in the editor.

### Add publications resource to public API

We are adding a new `/documents/latestPublications` endpoint in Public API.

### Parameters
| Parameter | Type | Required | Description |
| ---------- | ----- | --------- | ------------ |
| ?fields | `string` | No | Comma-separated list of fields that each publication should represent in the response. _Default_: `systemdata,metadata,content` |
| ?limit | `int` | No | Maximum number of publications to be returned. _Default_: `100` |
| ?after | `int` | No | Return publications after this publication id (used for pagination). |

### Response

A response with the default parameters has the following structure:

``` js
[
  {
    "systemdata": { ... },
    "metadata": { ... },
    "content": [ ... ]
  },
  {
    "systemdata": { ... },
    "metadata": { ... },
    "content": [ ... ]
  },
  {
    "systemdata": { ... },
    "metadata": { ... },
    "content": [ ... ]
  }
]
```

A single publication might look like this:

``` js
{
  "systemdata": {
    "projectId": 1,
    "channelId": 1,
    "documentId": 1,
    "documentType": "article",
    "layout": "regular",
    "design": {
      "name": "timeline",
      "version": "1.1.0"
    }
  },
  "metadata": {
    "title": "a title",
    "description": "some lead",
    "dependencies": {},
    "test": {
      "callCount": 3,
      "message": "li-test called 3 times",
      "events": [
        "onUpdate",
        "onUpdate",
        "onPublish"
      ]
    },
  },
  "content": [
    {
      "id": "doc-1b8i1ksh10",
      "identifier": "timeline.head",
      "content": {
        "title": "a title",
        "text": "some lead"
      }
    },
    {
      "id": "doc-1b8i1ksh20",
      "identifier": "timeline.normal",
      "content": {
        "caption": "my caption"
      },
      "styles": {
        "position": "left"
      }
    },
    {
      "id": "doc-1b8i1ksh30",
      "identifier": "timeline.p",
      "content": {
        "text": "first paragraph"
      }
    },
    {
      "id": "doc-1b8i1me1d0",
      "identifier": "timeline.p",
      "content": {
        "text": "second"
      }
    },
    {
      "id": "doc-1b8i1mfei0",
      "identifier": "timeline.p",
      "content": {
        "text": "and third one. :)"
      }
    }
  ]
}
```

The structure of a single publication is analogous to the response of the `/documents/:documentId/latestPublication` endpoint without renditions.

### Channels

As opposed to other functions in the Public API, this one isn't aware of custom channels and always returns publications from the default channel.

### Errors
| Error | Description |
| ----- | ----------- |
| 400 - Specified Limit exceeds maximum. | Specifying a limit of more than 100 will return a HTTP 400 error | 

### Add ServerApi method destroy()

The `liServer` gets a new method `destroy()` that can be called before exiting the process. The goal of the `destroy()` method is to stop listening on ports and finish outstanding requests.

`destroy()` will be called automatically if `registerShutdownHandlers: true` is passed when creating the `liServer`.

Example of how to manually call `destroy()`:
```js
const Server = require('@livingdocs/server')
const liServer = Server(require('../conf'))

// New method
process.on('SIGTERM', function (err) {
  liServer.destroy((err) => {
    process.exit()
  })
})
```

### Map article design layout to layout engine

The print API will now receive the selected livingdocs design layout with every call and map it to the `layoutEngine` param used by huGO.

It replaces the environment based `layoutEngine` config with a `layoutEngines` config that can list a number of layout engines supported by huGO. Each layout engine is associated with a design layout so a single LD instance can support multiple layout engines.

The new config looks like this:
```
  layoutEngines: [
    id: 'ww'  # used to inform print API about which layout engine to use
    layouts: ['woodwing']  # which print design layout to associate with this setting
    label: 'Woodwing'  # label for use in UI
    stringifyLists: false  # send list components as strings or hierarchical structure
  ,
    id: 'nt'
    layouts: ['print', 'newsnt']
    label: 'NewsNT'
    stringifyLists: true
  ]
```

and replaces the previous config:

```
  layoutEngine:
    id: 'nt'
    label: 'NewsNT'
  stringifyLists: true
```

### Prometheus routes indexer metrics

New Server Config:
```js
prometheusExporter: {
  enabled: true,
  port: 9020,
  collectDefaultMetrics: true
}
```
More info and docs on metrics:
Prometheus Docs: https://prometheus.io/docs/introduction/overview/
Client library used: https://github.com/siimon/prom-client

### Metrics Examples

Examples for a Counter, Gauge and Histogram:
```js
const metrics = require('./app/modules/metrics')
const namespace = 'livingdocs_routing_indexer'

const cacheErrors = metrics.createCounter({
  name: `${namespace}_errors_total`,
  help: 'Number of fatal errors'
})

const cacheWarmed = metrics.createGauge({
  name: `${namespace}_cache_warmed`,
  help: 'Is the routing cache initialized?'
})

const eventProcessingDuration = metrics.createHistogram({
  name: `${namespace}_event_processing_duration_seconds`,
  help: 'event processing duration',
  buckets: [3, 12, 60]
})
```

## Improvements

### Logging

Create a child logger in a feature:
```js
module.exports = function (feature, server, done) {
  const log = server.log.child({ns: 'li-routing'})
})
```
Note: The `ns` is short for 'namespace' and is meant to contain the featureName.

Child loggers can receive their own log level (good during development):
```js
module.exports = function (feature, server, done) {
  const log = server.log.child({ns: 'li-routing', level: 'debug'})
})
```

### Redone Development Serializer

<img width="633" alt="screen shot 2017-10-30 at 14 44 07" src="https://user-images.githubusercontent.com/47606/32174071-26e5e54a-bd81-11e7-81b1-2f70fb514324.png">

### New server side one-time rendering (without jQuery and jsdom)

```js
const li = require('@livingdocs/framework')
const livingdoc = li.createLivingdoc(...)
// add some content to the livingdoc

// The method render() is an addition so we can test if
// it produces the same output as livingdoc.html()
livingdoc.render()
```

#### Render Example with Includes

```js
const livingdocs = require('@livingdocs/framework')

// ... create your livingdoc

// resolve includes
componentTree.each((component) => {
  if (component.componentName === 'include') {
    const includeDirective = component.directives.get('remote')
    includeDirective.resolve(`
      <article>
        External Content
      </article>
    `)
  }
})

// render the component tree with a wrapper
const result = livingdocs.rendering.render({
  wrapperHtml: '<section doc-container="content"></section>'
  componentTree: componentTree
})
```

## Performance Testing

Performance tests can be setup in `test/performance/rendering_perf` and other files suffixed with `_perf`. What is being run should be required in `test/performance/runner.js`.

Run the performance tests:
```bash
node test/performance/runner.js
```

## Include Directive

`setParams()` was added to the include directive.

```js
includeDirective.setContent({
  service: 'list',
  params: {foo: 'bar'}
})

// Retrieve the params set on a directive (this includes defaultParams
// specified in the component configuration if they have not been overwritten).
includeDirective.getParams()


// setParams overwrites all parameters of this include.
includeDirective.setParams({foo: 'fighters'})

// addParams merges the specified params with the existing ones
// (including any default params that may have been set in the component
// configuration).
includeDirective.addParams({foo: 'bar'})
```

`resolve()` was added to the include directive.
```js
includeDirective.resolve('<div>string with arbitrary HTML</div>')

// Check if an include was already resolved
includeDirective.isResolved() // true
```

The `resolve()` method does only have an impact when a component tree is rendered with the one time rendering. It is not used by the dynamic renderer.

Resolved values are not persisted. If you serialize a document with resolved includes the resolved values will not be included in the JSON you get.

## Patches

### Editor

### Server
