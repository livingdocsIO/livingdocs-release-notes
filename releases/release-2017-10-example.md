# Release Notes: `October 2017 Release (EXAMPLE)`

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `63.2.1`
`@livingdocs/editor` | `23.0.3`

### Livingdocs Server

How to require the server in your package.json:

```json
"dependencies": {
  "@livingdocs/server": "63.2.1",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-server/tree/release-2017-10
- Previous release: [61.2.1](https://github.com/upfrontIO/livingdocs-release-notes/blob/master/releases/release-2017-09.md#livingdocs-server)

### Livingdocs Editor

How to require the editor in your package.json:

```json
"dependencies": {
  "@livingdocs/editor": "23.0.3",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-editor/tree/release-2017-10
- Patches
  - [23.0.3](https://github.com/upfrontIO/livingdocs-editor/releases/tag/v23.0.3) - addTask method invocation
- Previous release: [20.10.4](https://github.com/upfrontIO/livingdocs-release-notes/blob/master/releases/release-2017-09.md#livingdocs-editor)

# Breaking Changes

Component | Type | Description | PRs | Issues
--- | --- | --- | --- | ---
Server | BREAKING CHANGE, Feature | Upgrade to node 8 and npm > 5.5. | [80](https://github.com/upfrontIO/livingdocs-docker/pull/80), [#73](https://github.com/upfrontIO/livingdocs-docker/pull/73), [#2f65dfb](https://github.com/upfrontIO/livingdocs-server/commit/2f65dfb), [#1660](https://github.com/upfrontIO/livingdocs-server/pull/1660) | -
Server | BREAKING CHANGE | Remove deprecated methods. | [#1659](https://github.com/upfrontIO/livingdocs-server/pull/1659) | -
Server | BREAKING CHANGE | Remove newrelic support | [#1651](https://github.com/upfrontIO/livingdocs-server/pull/1651) | -
Editor | BREAKING CHANGE | Remove Option to Configure the Publish Panel Metadata Forms in the Editor. [Read more](#remove-option-to-configure-the-publish-panel-metadata-forms-in-the-editor) | [#1696](https://github.com/upfrontIO/livingdocs-editor/pull/1696) | -



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

- We use and advise you to use npm version > 5.5. `npm publish` had an issue where the `test` directory at the root of a project didn't get published in the final package tar file on npm. https://github.com/npm/npm/issues/18341. npm v5.1 version which gets shipped with node 8.9 fixes that issue.

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

### Remove newrelic support

This removes the instrumentation library from the project. We've never used it and will most likely replace it with sth like opentracing.


### Remove Option to Configure the Publish Panel Metadata Forms in the Editor

- Removed the option to configure the publish panel metadata forms in the editor (metadata in config/environments/all.coffee is now ignored).
- Move the metadata form configuration to the server like described here: https://github.com/upfrontIO/livingdocs/blob/master/concepts/metadata/metadata-examples.md#server.










## Highlighted Changes

Component | Type | Description | PRs | Issues
--- | --- | --- | --- | ---
Server, Editor | Feature | New doc include api [Read more](https://docs.livingdocs.io/videos/includes.html) | [#1623](https://github.com/upfrontIO/livingdocs-server/pull/1623) | [Epic, #1430](https://github.com/upfrontIO/livingdocs-planning/issues/1430), [#1423](https://github.com/upfrontIO/livingdocs-planning/issues/1423), [#1655](https://github.com/upfrontIO/livingdocs-editor/pull/1655)
Editor | Feature | Introduce card-based design on the publishing screen  | [#1453](https://github.com/upfrontIO/livingdocs-editor/pull/1453) | [#118](https://github.com/upfrontIO/livingdocs-planning/issues/118)
Server | Bugfix | Content fixes for drag'n'drop huGO articles [Read more](#content-fixes-for-drag-n-drop-hugo-articles) | [#1652](https://github.com/upfrontIO/livingdocs-server/pull/1652) | [#1557](https://github.com/upfrontIO/livingdocs-planning/issues/1557)
Server | Bugfix | Fix render pipeline api error handling | [#1669](https://github.com/upfrontIO/livingdocs-server/pull/1669) | -
Server | Bugfix | Log errors instead of crashing on registration | [#1632](https://github.com/upfrontIO/livingdocs-server/pull/1632) | [#](https://github.com/upfrontIO/livingdocs-planning/issues/1468)
Editor | Bugfix | As an editor I would like to see if I'm working on an archived article | [#1669](https://github.com/upfrontIO/livingdocs-editor/pull/1669) | [#1473](https://github.com/upfrontIO/livingdocs-planning/issues/1473)
Editor | Bugfix | Image caption isn't imported from Hugo.  | [#1714](https://github.com/upfrontIO/livingdocs-editor/pull/1714) | [#1546](https://github.com/upfrontIO/livingdocs-planning/issues/1546)










## Changes
* Extract routing to top-level feature  [#1667](https://github.com/upfrontIO/livingdocs-server/pull/1667)  [#1564](https://github.com/upfrontIO/livingdocs-planning/issues/1564)
* Move devDependencies used in colt helpers into dependencies  [#1671](https://github.com/upfrontIO/livingdocs-server/pull/1671)
* Expose `max_tasks_per_worker` config on worker strategy [#4e6791c](https://github.com/upfrontIO/livingdocs-server/commit/4e6791c)
* Allow sorting on keyword filtered ES searches [#1648](https://github.com/upfrontIO/livingdocs-server/pull/1648) [#1518](https://github.com/upfrontIO/livingdocs-planning/issues/1518)
* ...
