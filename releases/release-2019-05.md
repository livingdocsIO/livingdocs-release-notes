
**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `v76.26.1`
`@livingdocs/editor` | `v36.9.0`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "v76.26.1",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2019-05

### Livingdocs Server Patches
- [v76.26.1](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v76.26.1): update framework version to 11.7.0 for release management
- [v76.26.0](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v76.26.0): support google cloud storage



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "v36.9.0",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2019-05

### Livingdocs Editor Patches
- [v36.9.0](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v36.9.0): autosave: cover promises for multiple saveNow() calls when saving



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


* EDITOR
* Bump minor version to 36.10.0 for release management [livingdocs-editor #2702](https://github.com/livingdocsIO/livingdocs-editor/pull/2702) :gift:
* diff-revisions [livingdocs-editor #2630](https://github.com/livingdocsIO/livingdocs-editor/pull/2630) :gift:
* Implement paging for proofreading [livingdocs-editor #2689](https://github.com/livingdocsIO/livingdocs-editor/pull/2689) :gift:
* update the current text on the browser not supported page [livingdocs-editor #2696](https://github.com/livingdocsIO/livingdocs-editor/pull/2696) :gift:
* fix the browser support function [livingdocs-editor #2694](https://github.com/livingdocsIO/livingdocs-editor/pull/2694) :gift:
* Fix session expired login [livingdocs-editor #2688](https://github.com/livingdocsIO/livingdocs-editor/pull/2688) :gift:
* Improve error handling for expired sessions [livingdocs-editor #2691](https://github.com/livingdocsIO/livingdocs-editor/pull/2691) :gift:
* fix(lock): correctly remove the lock [livingdocs-editor #2690](https://github.com/livingdocsIO/livingdocs-editor/pull/2690) :gift:
* Fixed the component prefill and metadata initial extraction [livingdocs-editor #2599](https://github.com/livingdocsIO/livingdocs-editor/pull/2599) :gift:
* Feat: Update directive name on comment context after transform [livingdocs-editor #2654](https://github.com/livingdocsIO/livingdocs-editor/pull/2654) :gift:
* Lists - move document instead of copying on drag and drop [livingdocs-editor #2686](https://github.com/livingdocsIO/livingdocs-editor/pull/2686) :gift:
* Urgency Config/Visualisation of a Task [livingdocs-editor #2677](https://github.com/livingdocsIO/livingdocs-editor/pull/2677) :gift:
* Fix image service tests and clean up angular injects [livingdocs-editor #2683](https://github.com/livingdocsIO/livingdocs-editor/pull/2683) :gift:
* Design kanbanboard and fixes [livingdocs-editor #2680](https://github.com/livingdocsIO/livingdocs-editor/pull/2680) :gift:
* Fix the generation of the shrinkwrap [livingdocs-editor #2681](https://github.com/livingdocsIO/livingdocs-editor/pull/2681) :gift:
* Design filters [livingdocs-editor #2673](https://github.com/livingdocsIO/livingdocs-editor/pull/2673) :gift:
* Show google vision results for DAM [livingdocs-editor #2652](https://github.com/livingdocsIO/livingdocs-editor/pull/2652) :gift:
* Proofreading li-task UI/UX integration [livingdocs-editor #2632](https://github.com/livingdocsIO/livingdocs-editor/pull/2632) :gift:
* Sanitize all user input on render to prevent script injection [livingdocs-editor #2670](https://github.com/livingdocsIO/livingdocs-editor/pull/2670) :gift:
* Improve user admin screen layout [livingdocs-editor #2669](https://github.com/livingdocsIO/livingdocs-editor/pull/2669) :gift:
* fix(document-query): add new filter type channel handle [livingdocs-editor #2626](https://github.com/livingdocsIO/livingdocs-editor/pull/2626) :gift:
* Fix TrackJS [livingdocs-editor #2664](https://github.com/livingdocsIO/livingdocs-editor/pull/2664) :gift:
* Proofreading dashboard [livingdocs-editor #2577](https://github.com/livingdocsIO/livingdocs-editor/pull/2577) :gift:
* Robustify print modal and the template / layout mode [livingdocs-editor #2624](https://github.com/livingdocsIO/livingdocs-editor/pull/2624) :gift:
* Don't disable the selection mode btn in selection mode state [livingdocs-editor #2648](https://github.com/livingdocsIO/livingdocs-editor/pull/2648) :gift:
* add ng-disabled to signup button [livingdocs-editor #2653](https://github.com/livingdocsIO/livingdocs-editor/pull/2653) :gift:
* Asset management ui [livingdocs-editor #2647](https://github.com/livingdocsIO/livingdocs-editor/pull/2647) :gift:
* The scrolling on the lists view doesn't work for chrome 73 and firefox [livingdocs-editor #2649](https://github.com/livingdocsIO/livingdocs-editor/pull/2649) :gift:
* Predefined Filter Sets [livingdocs-editor #2633](https://github.com/livingdocsIO/livingdocs-editor/pull/2633) :gift:
* fix remove lock behavior [livingdocs-editor #2643](https://github.com/livingdocsIO/livingdocs-editor/pull/2643) :gift:
* Use the correct label for the finished task [livingdocs-editor #2645](https://github.com/livingdocsIO/livingdocs-editor/pull/2645) :gift:
* Completely Migrate to DroneCI [livingdocs-editor #2640](https://github.com/livingdocsIO/livingdocs-editor/pull/2640) :gift:
* Metadata Image - image selection [livingdocs-editor #2486](https://github.com/livingdocsIO/livingdocs-editor/pull/2486) :gift:
* Fix menu item move operation [livingdocs-editor #2634](https://github.com/livingdocsIO/livingdocs-editor/pull/2634) :gift:
* Read selected image service from server [livingdocs-editor #2607](https://github.com/livingdocsIO/livingdocs-editor/pull/2607) :gift:
* Proofreading li-task metadata plugin [livingdocs-editor #2606](https://github.com/livingdocsIO/livingdocs-editor/pull/2606) :gift:
* fix(printModal): delete keys and add remove button [livingdocs-editor #2622](https://github.com/livingdocsIO/livingdocs-editor/pull/2622) :gift:
* fix(print): guard the access of publicationPreset if its undefined [livingdocs-editor #2619](https://github.com/livingdocsIO/livingdocs-editor/pull/2619) :gift:
* Fix: Multiselect shortcut does not exit print publish screen anymore [livingdocs-editor #2613](https://github.com/livingdocsIO/livingdocs-editor/pull/2613) :gift:
* fix(lists-sorted-alphabetically): Fixed that the lists sorted alphabetically [livingdocs-editor #2609](https://github.com/livingdocsIO/livingdocs-editor/pull/2609) :gift:
* use stable chrome version [livingdocs-editor #2604](https://github.com/livingdocsIO/livingdocs-editor/pull/2604) :gift:
* Load more button for revisions in the history panel [livingdocs-editor #2546](https://github.com/livingdocsIO/livingdocs-editor/pull/2546) :gift:
* fix(print): set a preset for a print publication [livingdocs-editor #2578](https://github.com/livingdocsIO/livingdocs-editor/pull/2578) :gift:
* add cypress qa strings for DAM [livingdocs-editor #2602](https://github.com/livingdocsIO/livingdocs-editor/pull/2602) :gift:
* Fixed the component prefill and metadata initial extraction [livingdocs-editor #2600](https://github.com/livingdocsIO/livingdocs-editor/pull/2600) :gift:




* SERVER
* Bump minor version to 76.27.0 for release management [livingdocs-server #2417](https://github.com/livingdocsIO/livingdocs-server/pull/2417) :gift:
* Update livingdocs-framework for release-management [livingdocs-server #2416](https://github.com/livingdocsIO/livingdocs-server/pull/2416) :gift:
* feat(storage): support google cloud storage [livingdocs-server #2409](https://github.com/livingdocsIO/livingdocs-server/pull/2409) :gift:
* Document version fetcher get latest publications [livingdocs-server #2408](https://github.com/livingdocsIO/livingdocs-server/pull/2408) :gift:
* Better document search results & search customisation [livingdocs-server #2395](https://github.com/livingdocsIO/livingdocs-server/pull/2395) :gift:
* Remove not available properties in document routes search [livingdocs-server #2407](https://github.com/livingdocsIO/livingdocs-server/pull/2407) :gift:
* Urgency config for tasks [livingdocs-server #2402](https://github.com/livingdocsIO/livingdocs-server/pull/2402) :gift:
* Make article limit on dashboard configurable [livingdocs-server #2405](https://github.com/livingdocsIO/livingdocs-server/pull/2405) :gift:
* Create new revision on publish [livingdocs-server #2393](https://github.com/livingdocsIO/livingdocs-server/pull/2393) :gift:
* Provide knex transaction to downstreams in `updateListHooks` [livingdocs-server #2404](https://github.com/livingdocsIO/livingdocs-server/pull/2404) :gift:
* Support document indexing queries by project and published docs [livingdocs-server #2403](https://github.com/livingdocsIO/livingdocs-server/pull/2403) :gift:
* prefer use of base64 buffer in google vision API [livingdocs-server #2401](https://github.com/livingdocsIO/livingdocs-server/pull/2401) :gift:
* Handle Google Vision API errors [livingdocs-server #2400](https://github.com/livingdocsIO/livingdocs-server/pull/2400) :gift:
* Update leven to the latest version 🚀 [livingdocs-server #2394](https://github.com/livingdocsIO/livingdocs-server/pull/2394) :gift:
* Fix google vision config [livingdocs-server #2397](https://github.com/livingdocsIO/livingdocs-server/pull/2397) :gift:
* Auto Tagging with Google Vision API [livingdocs-server #2377](https://github.com/livingdocsIO/livingdocs-server/pull/2377) :gift:
* Proofreading li-task UI/UX integration [livingdocs-server #2378](https://github.com/livingdocsIO/livingdocs-server/pull/2378) :gift:
* Coerce config values using ajv instead of a custom function [livingdocs-server #2391](https://github.com/livingdocsIO/livingdocs-server/pull/2391) :gift:
* Add new document search filter by channel handle [livingdocs-server #2354](https://github.com/livingdocsIO/livingdocs-server/pull/2354) :gift:
* Enable synchronous indexing for cypress [livingdocs-server #2383](https://github.com/livingdocsIO/livingdocs-server/pull/2383) :gift:
* feat: validate hook results on publish [livingdocs-server #2364](https://github.com/livingdocsIO/livingdocs-server/pull/2364) :gift:
* Fix grunt setup [livingdocs-server #2379](https://github.com/livingdocsIO/livingdocs-server/pull/2379) :gift:
* Fix cypress setup [livingdocs-server #2375](https://github.com/livingdocsIO/livingdocs-server/pull/2375) :gift:
* Implement Asset Management and ImageProxy Features [livingdocs-server #2339](https://github.com/livingdocsIO/livingdocs-server/pull/2339) :gift:
* Expose db create script to downstreams [livingdocs-server #2374](https://github.com/livingdocsIO/livingdocs-server/pull/2374) :gift:
* fix(tasks): Fix grunt data-migration:accept [livingdocs-server #2371](https://github.com/livingdocsIO/livingdocs-server/pull/2371) :gift:
* Fix Filter Set error message [livingdocs-server #2370](https://github.com/livingdocsIO/livingdocs-server/pull/2370) :gift:
* Update concat-arrays to the latest version 🚀 [livingdocs-server #2367](https://github.com/livingdocsIO/livingdocs-server/pull/2367) :gift:
* Predefined Filter Sets [livingdocs-server #2365](https://github.com/livingdocsIO/livingdocs-server/pull/2365) :gift:
* Configurable image service in DAM [livingdocs-server #2343](https://github.com/livingdocsIO/livingdocs-server/pull/2343) :gift:
* Proofreading li-task metadata plugin [livingdocs-server #2350](https://github.com/livingdocsIO/livingdocs-server/pull/2350) :gift:
* Transform example-server channel config v1 to v2 [livingdocs-server #2360](https://github.com/livingdocsIO/livingdocs-server/pull/2360) :gift:
* Fix Hugo-DnD Articles, resolve the correct author instead of "importer" [livingdocs-server #2275](https://github.com/livingdocsIO/livingdocs-server/pull/2275) :gift:
* fix(hugo): add print to layouts [livingdocs-server #2344](https://github.com/livingdocsIO/livingdocs-server/pull/2344) :gift:
* Fix elasticsearch 6 support for optional date filters [livingdocs-server #2335](https://github.com/livingdocsIO/livingdocs-server/pull/2335) :gift:
* Fix example list-include to work with node 10 [livingdocs-server #2332](https://github.com/livingdocsIO/livingdocs-server/pull/2332) :gift:
* Bump minor version to 76.9.0 for release management [livingdocs-server #2331](https://github.com/livingdocsIO/livingdocs-server/pull/2331) :gift:


  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench: