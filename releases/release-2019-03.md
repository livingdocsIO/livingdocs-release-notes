**Attention:** If you skipped one or more release, please also check the release-notes of the skipped ones.

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `v76.8.0`
`@livingdocs/editor` | `v35.36.0`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "v76.8.0",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2019-03

### Livingdocs Server Patches
- [v76.8.0](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v76.8.0): initial version for release



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "v35.36.0",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2019-03

### Livingdocs Editor Patches
- [v35.36.0](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v35.36.0): initial version for release



# Highlights

## Recover Document :gift:

Sometimes it's possible that the editor comes into a conflict state. This can have different reasons. The most probable scenario is, that user 1 has a bad connection or works offline while another user is updating the document. When user 1 is back online and tries to save the document, he runs into a conflict.

User 1 will now be notified that the document has a conflict and get a link to recover the local document. If user 1 clicks on the recover link, a copy of his local document will be created.

* Related
  * [editor PR #2518](https://github.com/livingdocsIO/livingdocs-editor/pull/2518)
  * [editor PR #2477](https://github.com/livingdocsIO/livingdocs-editor/pull/2477)

## Custom Document Drag + Drop :gift:

The editor has some built in Drag & Drop implementations, to handle image, file and text drops onto a document. And It is possible to register your own drag & drop handlers.
Dropping objects over a dashboard is a separate subject.

* Related
  * [editor PR #2530](https://github.com/livingdocsIO/livingdocs-editor/pull/2530)
  * [documentation](https://upfrontio.gitbook.io/livingdocs/reference-documentation/editor/document-drag-drop#add-custom-drag-and-drop-handlers)



# Breaking Changes :fire:

## Migrate the database

```sh
# run grunt migrate to update to the newest database scheme
#   112-add-event-type-content-type-view-after-document-creation-updated.js
#   113-add-event-type-content-type-document-creation-disabled-updated.js
#   114-alter-user-config-value.js
grunt migrate
```

## Removed functions

* Removed `grunt repair-teasers` task :fire:
* Removed `getExternalList` option on `registerListHooks`

* Related
  * [server PR #2250](https://github.com/livingdocsIO/livingdocs-editor/pull/2250)



# Other Changes

* UI/UX
  * Start page design rework [livingdocs-editor #2520](https://github.com/livingdocsIO/livingdocs-editor/pull/2520) :gift:
  * Updated look of delete confirmation [livingdocs-editor #2536](https://github.com/livingdocsIO/livingdocs-editor/pull/2536) :gift:
  * Improve button styles on dark backgrounds [livingdocs-editor #2496](https://github.com/livingdocsIO/livingdocs-editor/pull/2496) :gift:
  * UI improvements for Static Project Settings [livingdocs-editor #2567](https://github.com/livingdocsIO/livingdocs-editor/pull/2567) :gift:
* Features
  * Support channel config v2 for static files [livingdocs-server #2282](https://github.com/livingdocsIO/livingdocs-server/pull/2282) :gift:
  * Merge users as admin [livingdocs-editor #2555](https://github.com/livingdocsIO/livingdocs-editor/pull/2555) :gift:
  * Remove read-only redrawing [livingdocs-editor #2464](https://github.com/livingdocsIO/livingdocs-editor/pull/2464) :gift:
* Admin Tasks
  * New task to create admin user (`livingdocs-server create-admin-user`) [livingdocs-server #2288](https://github.com/livingdocsIO/livingdocs-server/pull/2288) :gift:
  * New task to create admin users (`livingdocs-server create-admin-users`) [livingdocs-server #2259](https://github.com/livingdocsIO/livingdocs-server/pull/2259) :gift:
  * New task to add a design (`livingdocs-server add-design`) [livingdocs-server #2259](https://github.com/livingdocsIO/livingdocs-server/pull/2259) :gift:
  * New task to flush redis db (`livingdocs-server redis-flushdb`) [livingdocs-server #2279](https://github.com/livingdocsIO/livingdocs-server/pull/2279) :gift:
* Improvements
  * Add density to image convert config [livingdocs-server #2303](https://github.com/livingdocsIO/livingdocs-server/pull/2303) :wrench:
  * Deep camelize ignore [livingdocs-server #2316](https://github.com/livingdocsIO/livingdocs-server/pull/2316) :wrench:
  * Improve config loading [livingdocs-server #2301](https://github.com/livingdocsIO/livingdocs-server/pull/2301) :wrench:
  * Promise support in lib cli [livingdocs-server #2249](https://github.com/livingdocsIO/livingdocs-server/pull/2249) :wrench:
  * Provide project id and channel id to list update hook [livingdocs-server #2260](https://github.com/livingdocsIO/livingdocs-server/pull/2260) :wrench:
  * Map Metadata from Default Content [livingdocs-editor #2516](https://github.com/livingdocsIO/livingdocs-editor/pull/2516) :wrench:
  * Improve cypress helpers [livingdocs-editor #2503](https://github.com/livingdocsIO/livingdocs-editor/pull/2503) :wrench:
* Bugfixes
  * fix history mode [livingdocs-editor #2544](https://github.com/livingdocsIO/livingdocs-editor/pull/2544) :beetle:
  * fix sorting after a search on the list tool [livingdocs-editor #2515](https://github.com/livingdocsIO/livingdocs-editor/pull/2515) :beetle:
  * fix soft lock for multiple tabs of same user [livingdocs-editor #2573](https://github.com/livingdocsIO/livingdocs-editor/pull/2573) :beetle:
  * fix async ranges after regaining focus [livingdocs-editor #2558](https://github.com/livingdocsIO/livingdocs-editor/pull/2558) :beetle:
  * fix request id to use a string in the logs [livingdocs-editor #2543](https://github.com/livingdocsIO/livingdocs-editor/pull/2543) :beetle:
  * fix copy modal [livingdocs-editor #2507](https://github.com/livingdocsIO/livingdocs-editor/pull/2507) :beetle:
  * fix print publication info [livingdocs-editor #2510](https://github.com/livingdocsIO/livingdocs-editor/pull/2510) :beetle:
  * fix language handle conflict [livingdocs-server #2308](https://github.com/livingdocsIO/livingdocs-server/pull/2308) :beetle:
  * fix config loading for downstreams [livingdocs-server #2311](https://github.com/livingdocsIO/livingdocs-server/pull/2311) :beetle:
  * fix revision.user.id presence in indexer [livingdocs-server #2305](https://github.com/livingdocsIO/livingdocs-server/pull/2305) :beetle:
  * fix object to pick properties [livingdocs-server #2248](https://github.com/livingdocsIO/livingdocs-server/pull/2248) :beetle:
  * remove `assert-node-version.js` from preinstall script as it's causing issues [livingdocs-server #2277](https://github.com/livingdocsIO/livingdocs-server/pull/2277) :beetle:
  * add documentId to export [livingdocs-server #2294](https://github.com/livingdocsIO/livingdocs-server/pull/2294) :beetle:
* DAM (digital asset management) for Livingdocs Service
  * DAM/Images API [livingdocs-server #2156](https://github.com/livingdocsIO/livingdocs-server/pull/2156) :gift:
  * use thumbnails for Media Index [livingdocs-editor #2550](https://github.com/livingdocsIO/livingdocs-editor/pull/2550) :gift:
  * Design Asset Management Responsiveness [livingdocs-editor #2547](https://github.com/livingdocsIO/livingdocs-editor/pull/2547) :gift:
  * hide `upload Origin` in detail view of an image [livingdocs-editor #2540](https://github.com/livingdocsIO/livingdocs-editor/pull/2540) :gift:
  * configure default required imageService when DAM is disabled   [livingdocs-editor #2534](https://github.com/livingdocsIO/livingdocs-editor/pull/2534) :gift:
  * fix: edit buttons work in FF; [livingdocs-editor #2532](https://github.com/livingdocsIO/livingdocs-editor/pull/2532) :beetle:
  * fix thumbails in DAM [livingdocs-editor #2562](https://github.com/livingdocsIO/livingdocs-editor/pull/2562) :beetle:
  * fix media library jumping when selecting image [livingdocs-editor #2527](https://github.com/livingdocsIO/livingdocs-editor/pull/2527) :beetle:
  * fix: the cross button resets the search in the image view; [livingdocs-editor #2524](https://github.com/livingdocsIO/livingdocs-editor/pull/2524) :beetle:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
