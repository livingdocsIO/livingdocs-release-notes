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

* `DocumentVersion.prototype.render` got removed. Please call renderPipeline.renderDocumentVersion({documentVersion}, cb) directly.
* Removes transform methods from generic_document model. Downstreams might depend on this model in tests. 
* Removes exported renderDocument and renderDocumentVersion on the render-pipeline file. Please use the renderPipeline instance using
```
liServer.features.api('li-render-pipeline').renderDocumentVersion
```
* Removes renderPipeline.renderDocument. Please use the `renderPipeline.renderDocumentVersion({documentVersion}, cb)` method instead.
* From now on we don't export the designLoader methods on the design feature file anymore. Please use the designLoader feature instead:
```
liServer.features.api('li-design-loader').load({name, version}, cb)
```
* Removes exports from cache api. Please use `liServer.features.api('li-cache')` instead.
* Removes searchApi.getSearchManager and searchApi.getEsClient. Please use `liServer.features.api('li-search').searchManager` if you really need it.
* Removes `require('@livingdocs/server/app/features/documents').publicationApi`. If you still depend on deep requires, please replace them with the proper api. e.g. `liServer.features.api('li-documents').publication.
* Removes DocumentEntitiesManager.getDocumentAndRevision. Please use `DocumentEntitiesManager.getVersion` instead.

## Patches

### Editor 

### Server
