**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
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

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2020-07`
`@livingdocs/editor` | `release-2020-07`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2020-07",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2020-07

### Livingdocs Server Patches
- [v103.3.3](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v103.3.3): medialibrary: guarantee order of ids in resultset



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2020-07",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2020-07

### Livingdocs Editor Patches
- [v57.5.12](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.5.12): update framework



# Highlights

## Overhauled Media Library :tada:

The Media Library got a lot of updates. Some of the highlights are:
- The media library dashboard can be configured the same way as document dashboards (filter/search)
- Image asset custom metadata use the same configuration as document contentTypes
- Visually support copyright restrictions
- Extraction of metadata on image drop
- Alt text

A full changelog and screenshots can be found [here](https://github.com/livingdocsIO/livingdocs-planning/issues/3779).

## Project Based Main Navigation + Dashboards

Until now only one editor main navigation and dashboard config was possible (because the config was living on the editor). Since the configs have been moved to the project config on the server, it's now possible to configure the main navigation and dashboards per project.

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/307)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3024)

## Show all Errors at once on Publish Screen :tada:

There are 2 improvements on the editor publish screen:
- When publishing, show all errors at once (not only one error) - [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3513)
- Show an error message when a field has an error (development) - [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3519)


## Custom Text Editing Config :tada:

It's possible to define your own custom text editing elements (see documentation reference for more info).
Another improvement is that we moved the config of the default and custom elements to the server. One can now define text editing elements for every project (project config) and even for every content-type individually.

![image](https://user-images.githubusercontent.com/4352425/87558211-2332c280-c6b9-11ea-9b16-ae4d8f84a86e.png)

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3719)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3070)


## Display Filter :tada:

Display filters are the heart for dashboards. Therefore we introduce some improvements:

- We have a new time based filter called `liDateTimeRange` - [more info](https://github.com/livingdocsIO/livingdocs-editor/pull/3670)
- When adding a filter to a dashboard, it's now possible to pass (and interprete) a config - [more info](https://github.com/livingdocsIO/livingdocs-editor/pull/3697)
- When a filter option defines `isDefault`, the filter will be applied on the first request - [more info](https://github.com/livingdocsIO/livingdocs-editor/pull/3716)

## Restore Project Config :tada:

When having a dynamic project config one can now show a diff of and older version of the project config in the history screen of the project setup.
Additionally it's possible to restore an old project.

![image](https://user-images.githubusercontent.com/181334/82370740-52121c80-9a19-11ea-9b33-f20620111a14.png)

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3475)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2952)

## Define Dashboard Entry Point :tada:

One can now define a custom entry point on login or when switching projects. For more info see [here](https://github.com/livingdocsIO/livingdocs-editor/pull/3687).

## Custom User Menu :tada:

Now it's possible to define custom entries within the livingdocs user menu.

![image](https://user-images.githubusercontent.com/39759830/87947563-cf065480-caa3-11ea-890a-8735dfaf8ebc.png)

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/307)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3603)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2996)


## Revamped Editor Notifications :tada:

We improved the design and placement of editor notifications. Warnings and errors still stay on top middle of the editor, success and info messages go to the bottom left.
Also the API of `ldNotify` changed a little bit.
Check [the pull request](https://github.com/livingdocsIO/livingdocs-editor/pull/3533) to see some screenshots and the changed API.

## Import Log Viewer :tada:

When importing documents or images, one can now see the "import jobs" via project setup.
For more info look into the [PR description](https://github.com/livingdocsIO/livingdocs-editor/pull/3616)

## Manage Component Groups for Embedded Designs :tada:

Projects with an embedded design support now the management of component groups (grouping of components in editor sidebar).
Via project setup one has the ability to move components across groups, move groups, edit label of groups, add new groups and delete (empty) groups.
For more info look into the [PR description](https://github.com/livingdocsIO/livingdocs-editor/pull/3441)

## Custom Document Preview :tada:

It's now possible to integrate a custom document preview via the server side `previewApi`. Example of custom previews are
- custom mobile preview
- a preview of a finished article living on the frontend
- anything that fits the specific customer need.

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/309)


# Breaking Changes :fire:

## Migrate the database :fire:

It's a simple migration with no expected data losses.
The expected time for the image migration is 10'000 images / second.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 136-add-tag-suggestions.js
#   create tag_suggestions table
# migration - 137-migrate-assets.js
#   create media_library_entries table + migrate old data to new table
# migration - 138-text-index-on-project-and-users.js
#   add indexes on import_jobs, cache, config_properties table
#   migrate media_type to media_type_id
livingdocs-server migrate up
```

## Elasticsearch Client Upgrade

- :fire: `liServer.api('li-search').esClient` is now an instance of `@elastic/elasticsearch').Client`, so please migrate to that [api](https://www.elastic.co/guide/en/elasticsearch/client/javascript-api/current/api-reference.html).
- :fire: removed `liServer.api('li-search').IndexManager`. Use the elasticsearc client instead.
- :fire: removed `liServer.api('li-search').indexManager`. Use the elasticsearc client instead.
- :fire: removed `liServer.api('li-search').typeManager`. Use the elasticsearc client instead.
- :fire: removed `grunt search-index` and the file `task/util/search-index-configuration`. Use `livingdocs-server es-search-index` instead.
- :fire: `liServer.api('li-search').searchManager({}, {onlyId: true})` doesn't return an array of internal identifiers anymore. Instead the `documentId` is returned.
- :fire: static server config `search.elasticsearchClient` configuration supports now the [official](https://www.elastic.co/guide/en/elasticsearch/client/javascript-api/current/client-configuration.html) `@elastic/elasticsearch` client configuration

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2963)

## Use libvips as Default for Image Processing

- :fire: set `libvips` as default for image processing (because it's much faster and more secure).

If you want to fall back to `imagemagick`, you can add a config on the static server config `images.processingStrategy: 'imagemagick'`.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3063)

## Media Library

:fire: **The MediaLibrary is now active by default**
Both on the editor and server side.
The editor UI can be disabled but the server side feature is always active storing data in postgres and indexing into elasticsearch.

Disable the MediLibrary UI:
```js
// server project config
editorSettings: {
  mediaLibrary: {
    showUi: false
  }
}
```
Configure an elasticsearch index name for the `mediaLibraryIndex` (otherwise a default name will be used):
```js
// static server config
search: {
  // ...
  articleDocumentIndex: 'li-local-documents',
  articlePublicationIndex: 'li-local-publications',
  mediaLibraryIndex: 'li-local-media-library' // -> add this config

}
```

:fire: Server Media Library API

- The server API `li-asset-management` got renamed to `li-media-library`. Please update your code in case you're accessing it using `server.features.api('li-asset-management')` somewhere.

## Vue Components

:fire: Vue components that injected `navigateTo` need to inject `router` and call `router.navigateTo({name: routeName, params: { a: 1, b: 2}})` instead of `navigateTo(routeName, { a: 1, b: 2}})`. See [livingdocs-editor #3584](https://github.com/livingdocsIO/livingdocs-editor/pull/3584) for more info

## Editor Entry Point
:fire: `app.ui.welcome` in the static editor config does not support Angular routes anymore. Change them to a path, e.g. from `app.home` to `/home` ([read more here](https://github.com/livingdocsIO/livingdocs-editor/pull/3687))

## Editor ldNotify API Change

- :fire: removed `ldNotify.error` in favor of `ldNotify.alert`
- :fire: removed `ldNotify.sections` (the position will be derived from the log level)
- :fire: removed `ldNotify.appWarning`, use `ldNotify.banner` instead
- :fire: removed `ldNotify.appAlert`, use `ldNotify.alert` instead
- :fire: removed `ldNotify.appStatus`, use `ldNotify.info({ephemeral: false})` instead. 'ephemeral: false' set a sticky behavior.
- :fire: removed `ldNotify.notification.appearanceMode`. To keep the sticky behavior of a notification use 'ephemeral: false'

See [editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3533) for more info

## Drop Node 10 Support

- :fire: removed support for `Node 10`. Move to `Node 12` or `Node 14` ([read more here](https://github.com/livingdocsIO/livingdocs-editor/pull/3505))

## Renamed Icons

- :fire: renamed icon from `settings` to `cog`
- :fire: renamed icon from `github-circle` to `github`

Read [here](https://github.com/livingdocsIO/livingdocs-editor/pull/3505) for a more detailled description.

## Removed Global GoogleVision Config

:fire: You can't globally configure google vision anymore and have to move the config to the integrations project config. A migration guide can be found [here](https://github.com/livingdocsIO/livingdocs-server/pull/2969)


# Deprecations

### Main Navigation (static editor config)
- `app.sidePanelItems` in the static editor config should contain `route: {name: "routeName"}` instead of `sref: "routeName"`. sref is still valid but deprecated.
- `app.sidePanelItems` in the static editor config is deprecated. Configura the main navigation via project config `editorSettings.mainNavigation: [{'liItem': 'articles'}]` - [PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3663)

### Editor Entry Point (static editor config)
- `app.ui.welcome` in the static editor config is deprecated. Configure your editor entry point via `startPage` in the project config - [howto](https://github.com/livingdocsIO/livingdocs-editor/pull/3687)

### Dashboard Config (static editor config)

- `dashboards` in the static editor config is deprecated. Configure a dashboard via project config `editorSettings.dashboards: [{}]` - [PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3663)

### documentAPI (server API)

- `server.features.api('li-documents).document.find()`
  The methods parameters have changed and there is a new response structure. The old queries and properties will still work, but will log deprecation messages on every call.
  - The `q` attribute in the query parameter changed to `search`
  - In the return value the property `documents` got renamed to `results`
  ```js
  // change
  const {total, documents} = await documentApi.find({project_id: 1, q: 'Some text'})
  // to this
  const {total, results} = await documentApi.find({project_id: 1, search: 'Some text'})
  ```

- `server.features.api('li-documents).document.getReferences()` the response format changed
  ```js
  // and change
  const {total, documents} = await documentApi.getReferences({projectId, reference: 'image:1234'})
  // to this
  const {total, results} = await documentApi.getReferences({projectId, reference: 'image:1234'})
  ```

Reference: [Server PR #3004](https://github.com/livingdocsIO/livingdocs-server/pull/3004)

### Media Library (static server config)

- `assetManagement.enabled` in the static server config is deprecated. It has no effect anymore and will be removed in the [next release](https://github.com/livingdocsIO/livingdocs-server/pull/3086).

# APIs :gift:

* Public API: Added Curl examples [livingdocs-editor #3549](https://github.com/livingdocsIO/livingdocs-editor/pull/3549) :gift:
* Public API: Introduce Async support [livingdocs-server #3000](https://github.com/livingdocsIO/livingdocs-server/pull/3000) :gift:
* Publication API: Support async/await for `publicationApi.renderSelectedRenditions` [livingdocs-server #3011](https://github.com/livingdocsIO/livingdocs-server/pull/3011) :gift:


# Internal Changes

## Rename ld_icon

Renames `ld_icon` to `li-icon`. If you use any icons you have to use them like this now:
  `<li-icon name="icon-name" theme=""></li-icon>`. Where `theme` can hold the previous modifier classes: `class="li-icon--warning"` becomes `theme="warning"`.

PR: [livingdocs-editor #3492](https://github.com/livingdocsIO/livingdocs-editor/pull/3492)

## Internal PR's

**Vue**
* Vue styleguide [Editor #3500](https://github.com/livingdocsIO/livingdocs-editor/pull/3500)
* Support Vue mixin props in the Angular-Vue wrapper [Editor #3511](https://github.com/livingdocsIO/livingdocs-editor/pull/3511)
* Vueify project settings screen + add new component li-multi-select [Editor #3515](https://github.com/livingdocsIO/livingdocs-editor/pull/3515)
* Vueify liDashboardTitle [Editor #3607](https://github.com/livingdocsIO/livingdocs-editor/pull/3607)
* Vueify liCreateDocumentButton [Editor #3609](https://github.com/livingdocsIO/livingdocs-editor/pull/3609)
* Vueify document copy [Editor #3614](https://github.com/livingdocsIO/livingdocs-editor/pull/3614) :beetle:
* vue-form-generator: support date picker [Editor #3671](https://github.com/livingdocsIO/livingdocs-editor/pull/3671)

**Cypress**
* Add Cypress logs for Drone CI runs [Editor #3594](https://github.com/livingdocsIO/livingdocs-editor/pull/3594)
* Fix cypress login tests [Server #3010](https://github.com/livingdocsIO/livingdocs-server/pull/3010)

**Images**
* Image upload workflow [Editor #3430](https://github.com/livingdocsIO/livingdocs-editor/pull/3430)
* AssetProxy and mediaLibraryProxy [Editor #3680](https://github.com/livingdocsIO/livingdocs-editor/pull/3680)

**Editing API**
 * Document search parameters + response [Server #3004](https://github.com/livingdocsIO/livingdocs-server/pull/3004)


# Other Changes

### Improvements

**UI**
* Publish Screen: Show scheduled publishing dates when `document.customPublicationDateField` in static editor config [livingdocs-editor #3662](https://github.com/livingdocsIO/livingdocs-editor/pull/3662) :gift:
* Translation: Allow to change language if no translation is set yet [livingdocs-editor #3700](https://github.com/livingdocsIO/livingdocs-editor/pull/3700) :gift:
* Proofreading: Improve visiblity of urgent proofreading tasks and deadlines [livingdocs-editor #3618](https://github.com/livingdocsIO/livingdocs-editor/pull/3618) :gift:
* Metadata form: `liMetaReferenceForm` provides the same filter as its referenced document type [livingdocs-editor #3711](https://github.com/livingdocsIO/livingdocs-editor/pull/3711) :gift:
* Dashboard: Correctly support sorting on the document title [livingdocs-server #3078](https://github.com/livingdocsIO/livingdocs-server/pull/3078) :gift:
* Webhooks: Validate form and show editor side error messages [livingdocs-editor #3507](https://github.com/livingdocsIO/livingdocs-editor/pull/3507) :gift:
* Redis dashboard: Dashboards retrieve the list of queues automatically from Redis [livingdocs-server #2979](https://github.com/livingdocsIO/livingdocs-server/pull/2979) :gift:
* Project setup: Form generator add `li-boolean` type form [livingdocs-editor #3526](https://github.com/livingdocsIO/livingdocs-editor/pull/3526) :gift:
* Authentication:
  * Add user to login object to support email templates with more info [livingdocs-server #3025](https://github.com/livingdocsIO/livingdocs-server/pull/3025) :gift:
  * Add origin from headers to login object [livingdocs-server #3056](https://github.com/livingdocsIO/livingdocs-server/pull/3056) :gift:
* Live Coverage
  * Fix insert proposal [livingdocs-editor #3491](https://github.com/livingdocsIO/livingdocs-editor/pull/3491) :beetle:
  * Adapt live coverage UI [livingdocs-editor #3572](https://github.com/livingdocsIO/livingdocs-editor/pull/3572) :gift:

**Technical**
* Copy config: Make channelHandle optional [livingdocs-server #2930](https://github.com/livingdocsIO/livingdocs-server/pull/2930) :gift:
* Device detection: Improve sensitivity of device detection [livingdocs-server #2949](https://github.com/livingdocsIO/livingdocs-server/pull/2949) :gift:
* Schema validation
  * Server schemas: Strictly verify JSON schemas [livingdocs-server #3003](https://github.com/livingdocsIO/livingdocs-server/pull/3003) :gift:
  * Project config: Use `strictObj` validation for properties [livingdocs-server #3041](https://github.com/livingdocsIO/livingdocs-server/pull/3041) :gift:
* Document copy: Do not crash when the framework throws errors [livingdocs-server #3023](https://github.com/livingdocsIO/livingdocs-server/pull/3023) :gift:
* Metadata: Safely update metadata with a document version check [livingdocs-server #3067](https://github.com/livingdocsIO/livingdocs-server/pull/3067) :gift:

### Bugfixes

* Publish screen: Fix showing correct state of document relations (copy of, embedded in) [livingdocs-editor #3614](https://github.com/livingdocsIO/livingdocs-editor/pull/3614) :beetle:
* Language: show/hide li-language metadata form based on a behavior [livingdocs-editor #3527](https://github.com/livingdocsIO/livingdocs-editor/pull/3527) :beetle:
* Text counter: Allow to exclude whole components from text-counter [livingdocs-editor #3329](https://github.com/livingdocsIO/livingdocs-editor/pull/3329) :beetle:
* Create document modal: Fix create document modal and ios navi [livingdocs-editor #3567](https://github.com/livingdocsIO/livingdocs-editor/pull/3567) :beetle:
* Images: Fix add uploadImage function to iFrameview [livingdocs-editor #3582](https://github.com/livingdocsIO/livingdocs-editor/pull/3582) :beetle:
* Styles: Fix style alias to work in downstreams [livingdocs-editor #3621](https://github.com/livingdocsIO/livingdocs-editor/pull/3621) :beetle:
* Comments: Fix multiline comment support [livingdocs-editor #3633](https://github.com/livingdocsIO/livingdocs-editor/pull/3633) :beetle:
* Conflict management: Fix recover on conflicts with metadata changes on server [livingdocs-editor #3642](https://github.com/livingdocsIO/livingdocs-editor/pull/3642) :beetle:
* Content Types: Support content types that didn't declare a metadata array [livingdocs-server #2997](https://github.com/livingdocsIO/livingdocs-server/pull/2997) :beetle:
* Project seeding: Fix transaction issues and add error log for reliability and traceability [livingdocs-server #3044](https://github.com/livingdocsIO/livingdocs-server/pull/3044) :beetle:
  * Indexing: Normalize configurations for a proper indexing [livingdocs-server #3066](https://github.com/livingdocsIO/livingdocs-server/pull/3066) :beetle:
* Realtime Collab
  * Refactor: Refactor component locks and add them also for proposals [livingdocs-editor #3517](https://github.com/livingdocsIO/livingdocs-editor/pull/3517) :beetle:
  * Only blur component if focused on component lock [livingdocs-editor #3586](https://github.com/livingdocsIO/livingdocs-editor/pull/3586) :beetle:
  * Show insert in format panel and register empty click for it [livingdocs-editor #3637](https://github.com/livingdocsIO/livingdocs-editor/pull/3637) :beetle:
  * Add comment and cancel btn to comment card [livingdocs-editor #3664](https://github.com/livingdocsIO/livingdocs-editor/pull/3664) :beetle:
  * Fix component locks and history overlays [livingdocs-editor #3509](https://github.com/livingdocsIO/livingdocs-editor/pull/3509) :beetle:
  * Fix close on include modal and remove lock on idle [livingdocs-editor #3530](https://github.com/livingdocsIO/livingdocs-editor/pull/3530) :beetle:
  * Fix conflict handling with self [livingdocs-editor #3605](https://github.com/livingdocsIO/livingdocs-editor/pull/3605) :beetle:
  * Fix reopen a comment and check if objects already exists [livingdocs-editor #3714](https://github.com/livingdocsIO/livingdocs-editor/pull/3714) :beetle:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
