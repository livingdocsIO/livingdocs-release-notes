# Release Notes: `October 2017 Release`

## Repositories

A release consists of new versions of the `livingdocs-server`, the `livingdocs-editor` and the `livingdocs-framework`.

### Livingdocs Server

How to require the server in your package.json:

```json
"dependencies": {
  "@livingdocs/server": "63.2.1",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-server/tree/maintenance-v63.2.x
- Previous release: [61.2.1](https://github.com/upfrontIO/livingdocs-release-notes/blob/master/releases/release-2017-09.md#livingdocs-server)

### Livingdocs Editor

How to require the editor in your package.json:

```json
"dependencies": {
  "@livingdocs/editor": "23.0.1",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-editor/tree/maintenance-v23.0.x
- Previous release: [20.10.4](https://github.com/upfrontIO/livingdocs-release-notes/blob/master/releases/release-2017-09.md#livingdocs-editor)

### Livingdocs Framework

The framework is already integrated in the package.json of the upstream server and editor. It's **not** necessary to integrate the framework from your side.

The framework does not have a release branch.

How to require the framework in your package.json:

```json
dependencies: {
  "@livingdocs/framework": "7.14.0"
}
```

## Component changes

### Known issues

Component | Type | Description | PRs | Issues
--- | --- | --- | --- | ---
Server | BREAKING CHANGE, Feature | Upgrade to node 8 and npm > 5.5. [Read more](#upgrade-to-node-8) | [80](https://github.com/upfrontIO/livingdocs-docker/pull/80), [#2f65dfb](https://github.com/upfrontIO/livingdocs-server/commit/2f65dfb), [#1660](https://github.com/upfrontIO/livingdocs-server/pull/1660) | -
Server | BREAKING CHANGE | Remove deprecated methods. [Read more](#remove-deprecated-methods) | [#1659](https://github.com/upfrontIO/livingdocs-server/pull/1659) | -
Server | Bugfix | Content fixes for drag'n'drop huGO articles [Read more](#content-fixes-for-drag-n-drop-hugo-articles) | [#1652](https://github.com/upfrontIO/livingdocs-server/pull/1652) | [#1557](https://github.com/upfrontIO/livingdocs-planning/issues/1557)
Server | Feature | Extract routing to top-level feature | [#1667](https://github.com/upfrontIO/livingdocs-server/pull/1667) | [#1564](https://github.com/upfrontIO/livingdocs-planning/issues/1564)
Server | Bugfix | Move devDependencies used in colt helpers into dependencies | [#1671](https://github.com/upfrontIO/livingdocs-server/pull/1671) | -
Server | Bugfix | Fix render pipeline api error handling [Read more](#fix-render-pipeline-api-error-handling) | [#1669](https://github.com/upfrontIO/livingdocs-server/pull/1669) | -
Server | Feature | Expose `max_tasks_per_worker` config on worker strategy [Read more](#expose-max_tasks_per_worker-config-on-worker-strategy ) | [#4e6791c](https://github.com/upfrontIO/livingdocs-server/commit/4e6791c) | -
Server | Improvement | Remove `disableHugoUpdates` check in favor of hugo `updateConditions` [Read more](#remove-disableHugoUpdates-check-in-favor-of-hugo-updateConditions) | [#1661](https://github.com/upfrontIO/livingdocs-server/pull/1661), [#1559](https://github.com/upfrontIO/livingdocs-server/pull/1559) | [1046](https://github.com/upfrontIO/livingdocs-planning/issues/1046)
Server | Bugfix | Makes migrations 086-087 work again for older releases [Read more](#makes-migrations-086-087-work-again-for-older-releases) | [#4f334d2](https://github.com/upfrontIO/livingdocs-server/commit/4f334d2) | -
Server | Bugfix | Allow sorting on keyword filtered ES searches | [#1648](https://github.com/upfrontIO/livingdocs-server/pull/1648) | [#1518](https://github.com/upfrontIO/livingdocs-planning/issues/1518)
Server | BREAKING CHANGE | Remove newrelic support [Read more](remove-newrelic-support) | [#1651](https://github.com/upfrontIO/livingdocs-server/pull/1651) | -
Server | Bugfix | Prevent crash on undefined Elasticsearch config | [#1637](https://github.com/upfrontIO/livingdocs-server/pull/1637) | -
Server | Feature | Allow upload of SVG images (cropping is disabled in the editor) | [#1313](https://github.com/upfrontIO/livingdocs-server/pull/1313), [#1635](https://github.com/upfrontIO/livingdocs-server/pull/1635), [#1671](https://github.com/upfrontIO/livingdocs-editor/pull/1671) | [#302](https://github.com/upfrontIO/livingdocs-planning/issues/302)
Server | Bugfix | Migrate PrintController to object | [#1643](https://github.com/upfrontIO/livingdocs-server/pull/1643) | -
Server | Bugfix | Upgrade to ajv@5.0.0 compatible schemas | [#1642](https://github.com/upfrontIO/livingdocs-server/pull/1642) | -
Server | Bugfix | Log errors instead of crashing on registration | [#1632](https://github.com/upfrontIO/livingdocs-server/pull/1632) | [#](https://github.com/upfrontIO/livingdocs-planning/issues/1468)
Server | Feature | New doc include api [Read more](#new-doc-include-api) | [#1623](https://github.com/upfrontIO/livingdocs-server/pull/1623) | [Epic, #1430](https://github.com/upfrontIO/livingdocs-planning/issues/1430), [#1423](https://github.com/upfrontIO/livingdocs-planning/issues/1423), [Documentation](https://github.com/upfrontIO/livingdocs/pull/138)
Server | Bugfix | Routing fix (fixes "Key not found in database" error) | [#1609](https://github.com/upfrontIO/livingdocs-server/pull/1609) | [#1380](https://github.com/upfrontIO/livingdocs-planning/issues/1380)

## In detail

### Upgrade to node 8

- We upgraded to node 8, most likely it will not have a big impact on you if you already use docker. We can use newer features from now on. There are big changes in low level components like an improved debugger, async/await, n-api, async_hooks and v8. You can read more about it here: https://nodejs.org/en/blog/release/v8.0.0/

- There was one bigger issue we ran into. The behavior of the `Date` constructor changed in this node version. `new Date(isoString)` is now timezone agnostic. That behavior changed in ES2015 and node/chrome now respect that.

With node 6:
```
new Date('2015-05-04T00:00:00')  // 2015-05-04T00:00:00.000Z
new Date('2015-05-04T00:00:00Z') // 2015-05-04T00:00:00.000Z
```

With node 8:
```
new Date('2015-05-04T00:00:00')  // 2015-05-03T22:00:00.000Z
new Date('2015-05-04T00:00:00Z') // 2015-05-04T00:00:00.000Z
```

- We use and advice to use npm version > 5.5. `npm publish` had an issue where the `test` directory in the root of a project didn't get published in the final package tar file on npm. https://github.com/npm/npm/issues/18341

- When you switch to node 8 please also install all local modules from scratch (or npm rebuild):
  
  ```
  nvm install 8 && nvm alias default 8
  rm -Rf ./node_modules && npm install
  ```

- npm 5 which gets shipped with node 8 has a few issues with `npm link`. If you depend on them, you might want to downgrade to an older npm version using `npm install -g npm@3`.

### Remove deprecated methods

* `DocumentVersion.prototype.render` got removed. Please call `renderPipeline.renderDocumentVersion({documentVersion}, cb)` directly.
* Removes transform methods from generic_document model. Downstreams might depend on this model in tests. 
* Removes exported `renderDocument` and `renderDocumentVersion` on the render-pipeline file. Please use the renderPipeline instance using
```
liServer.features.api('li-render-pipeline').renderDocumentVersion
```
* Removes `renderPipeline.renderDocument`. Please use the `renderPipeline.renderDocumentVersion({documentVersion}, cb)` method instead.
* From now on we don't export the designLoader methods on the design feature file anymore. Please use the designLoader feature instead:
```
liServer.features.api('li-design-loader').load({name, version}, cb)
```
* Removes exports from cache api. Please use `liServer.features.api('li-cache')` instead.
* Removes `searchApi.getSearchManager` and `searchApi.getEsClient`. Please use `liServer.features.api('li-search').searchManager` if you really need it.
* Removes `require('@livingdocs/server/app/features/documents').publicationApi`. If you still depend on deep requires, please replace them with the proper api. e.g. `liServer.features.api('li-documents').publication.
* Removes ``DocumentEntitiesManager.getDocumentAndRevision`. Please use `DocumentEntitiesManager.getVersion` instead.

### Content fixes for drag'n'drop huGO articles

- `HugoArticle` class was parsing only paragraphs (`</p>`-tags). We are now parsing subtitles as well (`<h2/>`-tags).

## New `body` property in `HugoArticle`

Instances of the `HugoArticle` class now additonally have a `body` property which holds an array of objects describing the content. Given the following huGO article body:

``` html
<p>Paragraph One.</p>
<h2>Subtitle One.</p>
<p>Paragraph Two.</p>
```

after parsing the `body` property would contain:

``` js
[
  {
    content: 'Paragraph One.'
    type: 'paragraph'
  },
  {
    content: 'Subtitle One.'
    type: 'heading2'
  },
  {
    content: 'Paragraph Two.'
    type: 'paragraph'
  }
]
```

whereas the `text` property - which is kept - contains: 

``` js
[
  'Paragraph One.',
  'Paragraph Two.'
]
```

The `<h2/>`-headings have been omitted in the latter case.

## Configuration

Which tags are allowed to be parsed can be configured:

``` js
hugo: {
    // [...]
    parsedBodyTags: {
      h1: 'heading1',
      h2: 'heading2',
      p: 'paragraph'
    }
  },
```

In case the tags are not configured the default is:

``` js
{
  h2: 'heading2',
  p: 'paragraph'
}
```

### Fix render pipeline api error handling

An asynchronous function of a render_pipeline_api should call the callback with an error, not throw errors directly. Otherwise the users of the api cannot handle the error nor log additional informations to find the document which caused the problem.

### Makes migrations 086-087 work again for older releases

Removes the deprecated `group_projection` and `group_member_projection` tables. They got replaced in migration [#085](https://github.com/upfrontIO/livingdocs-server/blob/master/db/migrations/085-improve-group-projections.js) about 8 months ago. If you're using the regular apis, this doesn't have an impact on your code.

### Remove newrelic support

This removes the instrumentation library from the project. We've never used it and will most likely replace it with sth like opentracing.

### Remove `disableHugoUpdates` check in favor of hugo `updateConditions`

`import` now accepts an optional `updateCondition` parameter. This parameter can be a string referring to one of three common update strategies configured downstream and implemented upstream: `never`, `always`, `untouched` - or alternatively a function implementing custom logic can be passed.

```js
// app/features/import/import_api

import ({importJob, rawDocument, shouldCreateNew, updateCondition, userId}, callback) {
  // ...
}
```

## Patches

### Editor 

### Server
