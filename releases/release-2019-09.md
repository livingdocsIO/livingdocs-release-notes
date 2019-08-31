
**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `v85.3.1`
`@livingdocs/editor` | `??.?.?`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "v85.3.1",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2019-09

### Livingdocs Server Patches
- [v85.3.1](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v85.3.1): update framework



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "??.?.?",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2019-09

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text



# Highlights

## EXAMPLE !!!!!!!!!!!!!!!!!!! Editor Multiselect :gift:
Add multiselect functionality to the editor. In multiselect mode when a component is clicked this component is added to the selection. When a component is clicked again it is removed from the selection. In the sidebar the count of selected components is shown and there is the option to delete all selected components.
Required editor configuration to enable the multiselect feature:
```js
keyboardShortcuts: {
      '↓shift': 'start multiselect mode',
      '↑shift': 'end multiselect mode'
}
```

* Related Pull Requests
  * [editor PR #2143](https://github.com/livingdocsIO/livingdocs-editor/pull/2143)


# Breaking Changes :fire:

## Migrate the database

```sh
# run grunt migrate to update to the newest database scheme
# migration - 111-add-comments-table.js
#   create comments table + add events to the stream_events_types table
livingdocs-server migrate up
```

## EXAMPLE !!!!!!!!!!!!!!!!!!! Registration procedure :gift: :fire:
There are two new flags per authentication connections: `loginEnabled` and `registrationEnabled`.
The editor won't show the respective connection option in the login screen without them.
Server `auth` configuration:
```js
auth: {
  connections: {
    // email and password authentication
    local: {
      enabled: true,
      loginEnabled: true,
      registrationEnabled: true
      //...
    },
    github: {
      enabled: true,
      loginEnabled: false,
      registrationEnabled: false
      // ...
    }
  }
}
```

* Related Pull Requests
  * [server PR #2010](https://github.com/livingdocsIO/livingdocs-server/pull/2010)
  * [editor PR #2114](https://github.com/livingdocsIO/livingdocs-editor/pull/2114)




# Other Changes

* Features
  * ... :gift:
* Chore
  * ... :wrench:
* Bugfixes
  * ... :beetle:
* Service
  * ...


EDITOR
------------------------
* v41.9.2 Add google, facebook and twitter icons to the list we load [livingdocs-editor #2948](https://github.com/livingdocsIO/livingdocs-editor/pull/2948) :gift:
* v41.9.1 fix(categories): fix typo [livingdocs-editor #2947](https://github.com/livingdocsIO/livingdocs-editor/pull/2947) :gift:
* v41.9.0 Teaser preview in publish screen [livingdocs-editor #2908](https://github.com/livingdocsIO/livingdocs-editor/pull/2908) :gift:
* v41.8.0 Update routing on category change [livingdocs-editor #2936](https://github.com/livingdocsIO/livingdocs-editor/pull/2936) :gift:
* v41.7.0 Auto Update of `doc-html` Input [livingdocs-editor #2917](https://github.com/livingdocsIO/livingdocs-editor/pull/2917) :gift:
* v41.6.0 Show channel config revisions [livingdocs-editor #2898](https://github.com/livingdocsIO/livingdocs-editor/pull/2898) :gift:
* v41.5.2 Proofreading: do not shrink priority icon on large titles [livingdocs-editor #2939](https://github.com/livingdocsIO/livingdocs-editor/pull/2939) :gift:
* v41.5.1 Allow Edit of Iframe Embeds [livingdocs-editor #2921](https://github.com/livingdocsIO/livingdocs-editor/pull/2921) :gift:
* v41.5.0 Load assets for includes and onIncludeRendered hook [livingdocs-editor #2892](https://github.com/livingdocsIO/livingdocs-editor/pull/2892) :gift:
* v41.4.3 fix(history): always display published event [livingdocs-editor #2934](https://github.com/livingdocsIO/livingdocs-editor/pull/2934) :gift:
* v41.4.2 Proofeading dashboard fix: ctrl-click opens a new tab [livingdocs-editor #2929](https://github.com/livingdocsIO/livingdocs-editor/pull/2929) :gift:
* v41.4.1 Public API documentation for categories [livingdocs-editor #2916](https://github.com/livingdocsIO/livingdocs-editor/pull/2916) :gift:
* v41.4.0 Rewrite categories feature for service [livingdocs-editor #2913](https://github.com/livingdocsIO/livingdocs-editor/pull/2913) :gift:
* v41.3.1 liPairSelection: correctly resolve a previous selection [livingdocs-editor #2910](https://github.com/livingdocsIO/livingdocs-editor/pull/2910) :gift:
* v41.3.0 Enable downstreams to register custom setup properties [livingdocs-editor #2901](https://github.com/livingdocsIO/livingdocs-editor/pull/2901) :gift:
* v41.2.0 Webpack loader upgrades and CSS Sourcemap Support [livingdocs-editor #2909](https://github.com/livingdocsIO/livingdocs-editor/pull/2909) :gift:
* v41.1.2 Asset Details [livingdocs-editor #2907](https://github.com/livingdocsIO/livingdocs-editor/pull/2907) :gift:
* v41.1.1 Fix roboto-fontface module lookup in scss files [livingdocs-editor #2904](https://github.com/livingdocsIO/livingdocs-editor/pull/2904) :gift:
* v41.1.0 Reduce bundle size, https and api proxy support [livingdocs-editor #2903](https://github.com/livingdocsIO/livingdocs-editor/pull/2903) :gift:
* v41.0.0 Breaking-change: New config options for menus  [livingdocs-editor #2871](https://github.com/livingdocsIO/livingdocs-editor/pull/2871) :gift:
* v40.4.1 Properly initiate a route change on document recover [livingdocs-editor #2896](https://github.com/livingdocsIO/livingdocs-editor/pull/2896) :gift:
* v40.4.0 Operations Screen [livingdocs-editor #2895](https://github.com/livingdocsIO/livingdocs-editor/pull/2895) :gift:
* v40.3.0 Design Editor v1 [livingdocs-editor #2676](https://github.com/livingdocsIO/livingdocs-editor/pull/2676) :gift:
* v40.2.7 Display deleted articles warning red instead of yellow [livingdocs-editor #2893](https://github.com/livingdocsIO/livingdocs-editor/pull/2893) :gift:
* v40.2.6 Comments and Properties [livingdocs-editor #2891](https://github.com/livingdocsIO/livingdocs-editor/pull/2891) :gift:
* v40.2.5 History sidebar: Prefix username with colored dots [livingdocs-editor #2890](https://github.com/livingdocsIO/livingdocs-editor/pull/2890) :gift:
* v40.2.4 Correctly set access for multiple groups (ABAC) [livingdocs-editor #2885](https://github.com/livingdocsIO/livingdocs-editor/pull/2885) :gift:
* v40.2.3 Show tasks in publish panel on the sidebar [livingdocs-editor #2879](https://github.com/livingdocsIO/livingdocs-editor/pull/2879) :gift:
* v40.2.2 Proofreading Improvements [livingdocs-editor #2857](https://github.com/livingdocsIO/livingdocs-editor/pull/2857) :gift:
* v40.2.1 Set bowser version to 2.5.2 to fix building problems [livingdocs-editor #2873](https://github.com/livingdocsIO/livingdocs-editor/pull/2873) :gift:
* v40.2.0 Integrate imatrics [livingdocs-editor #2861](https://github.com/livingdocsIO/livingdocs-editor/pull/2861) :gift:
* v40.1.2 Allow notContentType in dashboard filters to be a value or an array [livingdocs-editor #2867](https://github.com/livingdocsIO/livingdocs-editor/pull/2867) :gift:
* v40.1.1 Bug-fix: always hide the toolbar on archived documents [livingdocs-editor #2864](https://github.com/livingdocsIO/livingdocs-editor/pull/2864) :gift:
* v40.1.0 Design workflow [livingdocs-editor #2860](https://github.com/livingdocsIO/livingdocs-editor/pull/2860) :gift:
* v40.0.5 Show truck status on Proofreading Dashboard [livingdocs-editor #2855](https://github.com/livingdocsIO/livingdocs-editor/pull/2855) :gift:
* v40.0.4 Fix relative path of css files in differ [livingdocs-editor #2850](https://github.com/livingdocsIO/livingdocs-editor/pull/2850) :gift:
* v40.0.3 Handle invalid content-types on Dashboards [livingdocs-editor #2842](https://github.com/livingdocsIO/livingdocs-editor/pull/2842) :gift:
* v40.0.2 use image size as max value for crop [livingdocs-editor #2836](https://github.com/livingdocsIO/livingdocs-editor/pull/2836) :gift:
* v40.0.1 Resolve Filter Properly in a Custom Dashboard on a Refresh when Query String is set  [livingdocs-editor #2833](https://github.com/livingdocsIO/livingdocs-editor/pull/2833) :gift:
* v40.0.0 Dev & Build Setup Improvements, Browser upgrade [livingdocs-editor #2825](https://github.com/livingdocsIO/livingdocs-editor/pull/2825) :gift:
* v39.4.2 fix ‘load more articles’ computation in proofreading dashboard [livingdocs-editor #2831](https://github.com/livingdocsIO/livingdocs-editor/pull/2831) :gift:
* v39.4.1 Add default label for tasks [livingdocs-editor #2829](https://github.com/livingdocsIO/livingdocs-editor/pull/2829) :gift:
* v39.4.0 Hidden setup form for publish-webhooks [livingdocs-editor #2819](https://github.com/livingdocsIO/livingdocs-editor/pull/2819) :gift:
* v39.3.2 Backport release 2019 07 Dumont - rotate npm token [livingdocs-editor #2933](https://github.com/livingdocsIO/livingdocs-editor/pull/2933) :gift:
* v39.3.1 Some small design improvements for the tasks [livingdocs-editor #2816](https://github.com/livingdocsIO/livingdocs-editor/pull/2816) :gift:
* v39.3.0 History Sidebar: Prefix user names with colored dots. [livingdocs-editor #2888](https://github.com/livingdocsIO/livingdocs-editor/pull/2888) :gift:

SERVER
------------------------
* v85.3.0 Content Type config for Teaser preview [livingdocs-server #2499](https://github.com/livingdocsIO/livingdocs-server/pull/2499) :gift:
* v85.2.0 Support async/await in designLoader api [livingdocs-server #2523](https://github.com/livingdocsIO/livingdocs-server/pull/2523) :gift:
* v85.1.1 Add a 'Cache-Control: no-cache' header on the /status endpoint [livingdocs-server #2521](https://github.com/livingdocsIO/livingdocs-server/pull/2521) :gift:
* v85.1.0 Auto-update pages on category#path change [livingdocs-server #2511](https://github.com/livingdocsIO/livingdocs-server/pull/2511) :gift:
* v85.0.1 Fix 'path' query in documentApi.findOne [livingdocs-server #2517](https://github.com/livingdocsIO/livingdocs-server/pull/2517) :gift:
* v85.0.0 Load assets for includes and onIncludeRendered hook [livingdocs-server #2496](https://github.com/livingdocsIO/livingdocs-server/pull/2496) :gift:
* v84.5.0 Endpoints for channel config revisions [livingdocs-server #2498](https://github.com/livingdocsIO/livingdocs-server/pull/2498) :gift:
* v84.4.1 Copy-api allow transformations within the same design [livingdocs-server #2512](https://github.com/livingdocsIO/livingdocs-server/pull/2512) :gift:
* v84.4.0 Public API endpoints for categories [livingdocs-server #2506](https://github.com/livingdocsIO/livingdocs-server/pull/2506) :gift:
* v84.3.0 Rewrite categories feature for service [livingdocs-server #2502](https://github.com/livingdocsIO/livingdocs-server/pull/2502) :gift:
* v84.2.1 Refactor uiComponents to uiComponent on custom channel-config properties [livingdocs-server #2500](https://github.com/livingdocsIO/livingdocs-server/pull/2500) :gift:
* v84.2.0 Operations Screen [livingdocs-server #2497](https://github.com/livingdocsIO/livingdocs-server/pull/2497) :gift:
* v84.1.0 Skip the onPublish imatrics analysis in tests [livingdocs-server #2495](https://github.com/livingdocsIO/livingdocs-server/pull/2495) :gift:
* v84.0.0 Asset Collections  Part I [livingdocs-server #2410](https://github.com/livingdocsIO/livingdocs-server/pull/2410) :gift:
* v83.5.0 Add website to upstream seeder [livingdocs-server #2492](https://github.com/livingdocsIO/livingdocs-server/pull/2492) :gift:
* v83.4.1 Allow notContentType filters to be a value or an array [livingdocs-server #2488](https://github.com/livingdocsIO/livingdocs-server/pull/2488) :gift:
* v83.4.0 Integrate imatrics [livingdocs-server #2487](https://github.com/livingdocsIO/livingdocs-server/pull/2487) :gift:
* v83.3.3 chore(drone): remove bluewin setup [livingdocs-server #2515](https://github.com/livingdocsIO/livingdocs-server/pull/2515) :gift:
* v83.3.2 Prevent Group Membership Assignment in User Merging from Overwriting [livingdocs-server #2482](https://github.com/livingdocsIO/livingdocs-server/pull/2482) :gift:
* v83.3.1 Disable netlify feature flag [livingdocs-server #2480](https://github.com/livingdocsIO/livingdocs-server/pull/2480) :gift:
  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
