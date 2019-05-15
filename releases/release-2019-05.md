
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

## Media Library :gift:

We introduce a new media library in Livingdocs that allows to track and search all images uploaded to Livingdocs and to manage metadata for those images. As an option we offer auto-tagging of all uploaded images using the Google Vision API (infers costs). We also introduced a new image service `liImageProxy` which allows to track all image requests through the server, e.g. for traffic control.

* References
  * [documentation](https://docs.livingdocs.io/reference-documentation/server/config#asset-management)
  * [editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/2647)


## Improved Dashboard Search / Implement Your Own Dashboard Search :gift:

### Better Default Search

:tada: The editor dashboard search has been massively improved and now you get much better search results.
We did a lot of improvements to the default search algorithm. The most important change is, that recent edited articles have much more importance, which you can see in the following digram.



- y-axis: importance boost
- x-axis: time of editing an article
- black line: importance boost / time

![47582728-86187f00-d955-11e8-8a79-19d1aca8982c](https://user-images.githubusercontent.com/172394/57685243-cc0a0b80-7637-11e9-99cf-4e1a9ad3c961.png)

### Custom Search

:gift: You can also implement your own Dashboard search by registering a [queryBuilderPlugin](https://github.com/livingdocsIO/livingdocs-server/pull/2395).


* References
  * [server PR #2395](https://github.com/livingdocsIO/livingdocs-server/pull/2395)
  * [documentation](https://github.com/livingdocsIO/livingdocs/blob/master/reference-docs/server-configuration/config.md#querybuilderplugin)




## Predefined Filter Sets :gift:

Enables predefined Filter Sets on a dashboard.
Project admins can navigate to any dashboard, choose filters and then store the setting in a predefined filter set which is similar in kind to a bookmark.
The filter sets can be edited over a user interface in the project setup and can be nested in groups (one-level deep) for organizing.
Users (non-admins) can see and use the predefined filter sets, i.e. on a dashboard, e.g. the article dashboard, they can choose a filter set which will then apply the complete set selection of filters to the dashboard.

* References
  * [editor PR #2633](https://github.com/livingdocsIO/livingdocs-editor/pull/2633)




## Custom Workflows with Tasks v2 :gift:

With Tasks (v2) you are able to define custom workflows in the editor. It's an overhauled version which replaces Tasks (v1). You can find the migration guide from Tasks v1 to v2 [here](https://github.com/livingdocsIO/livingdocs-editor/pull/2606).

Highlights of Tasks v2:
- Tasks have 3 states (`requested`, `accepted`, `completed`)
- Define your custom metadata field for every task
- Every tasks is individually configurable, e.g.
  - labels for all states
  - request a deadline date
  - define when a task appears urgent
- Customise the deadline computation via the core API in the editor
  - Register a function to make suggestion for the deadline date
  - Register a function to provide an allowed deadline date range

* References
  * [documentation - how to add a custom proofreading task](https://docs.livingdocs.io/general-howtos/add-custom-proofreading-task)
  * [documentation - how to add a custom task](https://docs.livingdocs.io/general-howtos/add-custom-task)
  * [editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/2606)




## Google Cloud Storage support for designs/files/images :gift:

For users who want to store their images, files and design assets in a Google Cloud Storage (GCS) bucket rather than on Amazon, we provide a separate storage strategy.

Required server configuration to enable storing assets on GCS.
```
storage: {
  strategy: 'google-cloud-storage',
  config: {
    bucket: 'livingdocs-images-dev', // The bucket name
    credentials: {} // The credentials
  }
}
```


A more detailled description and an example configuration can be found in the [documentation](https://docs.livingdocs.io/reference-documentation/server/google-cloud-storage)

* References
  * [editor PR #2409](https://github.com/livingdocsIO/livingdocs-server/pull/2409)
  * [Documentation](https://docs.livingdocs.io/reference-documentation/server/google-cloud-storage)





## Improve speed of reindexing :gift:

Depending on how many documents you have stored, the re-indexing into elasticsearch needed some time. For production this has been a challenge for a long time, when you did an upgrade where data migrations were involved or even an elasticsearch mapping update.

Since the January 2019 release, we have continually improved the indexing speed. The optimisation results in a `10x - 100x` speed improvement and an average indexing speed of `1000 docs/s`. The indexing speed depends on your elasticsearch configuration and the size of your documents.




# Beta Versions

## Track Changes (Differ) :tada:

:DESCRIPTION from Meinrad:

* References
  * [documentation :link from Meinrad:]()
  * [editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/2630)


## Customisable Dashboards/Kanbanboards :tada:

:DESCRIPTION from Lukas:

* References
  * [documentation :link from Lukas:]()
  * [editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/2577)





# Breaking Changes :fire:

## Migrate the database

```sh
# run grunt migrate to update to the newest database scheme
# migrations
# - 112-add-event-type-content-type-view-after-document-creation-updated.js
# - 113-add-event-type-content-type-document-creation-disabled-updated.js
# - 114-alter-user-config-value.js
# - 115-add-filter-set-table.js
# - 116-add-assets-table.js
# - 117-add-channel-config-events.js
livingdocs-server migrate up
```


# Other Changes

* Security
  * Sanitize all user input on render to prevent script injection [livingdocs-editor #2670](https://github.com/livingdocsIO/livingdocs-editor/pull/2670) :gift:
* Features
  * Add ability to filter dashboard results by channel [livingdocs-editor #2626](https://github.com/livingdocsIO/livingdocs-editor/pull/2626) :gift:
  * Make article limit on dashboard configurable [livingdocs-server #2405](https://github.com/livingdocsIO/livingdocs-server/pull/2405) :gift:
* Improvements
  * Improve error handling for expired sessions [livingdocs-editor #2691](https://github.com/livingdocsIO/livingdocs-editor/pull/2691) :gift:
  * Signup - add ng-disabled to signup button [livingdocs-editor #2653](https://github.com/livingdocsIO/livingdocs-editor/pull/2653) :gift:
  * Load more button for revisions in the history panel [livingdocs-editor #2546](https://github.com/livingdocsIO/livingdocs-editor/pull/2546) :gift:
  * Metadata Image - image selection [livingdocs-editor #2486](https://github.com/livingdocsIO/livingdocs-editor/pull/2486) :gift:
  * Create new revision on publish for another user [livingdocs-server #2393](https://github.com/livingdocsIO/livingdocs-server/pull/2393) :gift:
  * Validate hook results on publish [livingdocs-server #2364](https://github.com/livingdocsIO/livingdocs-server/pull/2364) :gift:
  * Expose db create script to downstreams [livingdocs-server #2374](https://github.com/livingdocsIO/livingdocs-server/pull/2374) :gift:
  * Make server fully compatible with node 10 [livingdocs-server #2332](https://github.com/livingdocsIO/livingdocs-server/pull/2332) :gift:
* Bugfixes
  * Fix layouting issues on admin screen [livingdocs-editor #2669](https://github.com/livingdocsIO/livingdocs-editor/pull/2669) :beetle:
  * Keep comments when transforming a component, e.g. paragraph to subtitle [livingdocs-editor #2654](https://github.com/livingdocsIO/livingdocs-editor/pull/2654) :beetle:
  * Lists - move document instead of copying on drag and drop [livingdocs-editor #2686](https://github.com/livingdocsIO/livingdocs-editor/pull/2686) :beetle:
  * fix browser support function [livingdocs-editor #2694](https://github.com/livingdocsIO/livingdocs-editor/pull/2694) :beetle:
  * Fix session expired login [livingdocs-editor #2688](https://github.com/livingdocsIO/livingdocs-editor/pull/2688) :beetle:
  * A second user can correctly remove a locked document [livingdocs-editor #2690](https://github.com/livingdocsIO/livingdocs-editor/pull/2690) :beetle:
  * Fix to show user names on TrackJS again [livingdocs-editor #2664](https://github.com/livingdocsIO/livingdocs-editor/pull/2664) :beetle:
  * Don't disable the selection mode btn in selection mode state [livingdocs-editor #2648](https://github.com/livingdocsIO/livingdocs-editor/pull/2648) :beetle:
  * DnD from Hugo to articles resolve author correctly [livingdocs-server #2275](https://github.com/livingdocsIO/livingdocs-server/pull/2275) :beetle:
  * Fix scrolling on lists for chrome 73 and firefox [livingdocs-editor #2649](https://github.com/livingdocsIO/livingdocs-editor/pull/2649) :beetle:
  * Fix remove soft-lock [livingdocs-editor #2643](https://github.com/livingdocsIO/livingdocs-editor/pull/2643) :beetle:
  * Fix menu item move [livingdocs-editor #2634](https://github.com/livingdocsIO/livingdocs-editor/pull/2634) :beetle:
  * Fix that multiselect shortcut does exit print publish screen again [livingdocs-editor #2613](https://github.com/livingdocsIO/livingdocs-editor/pull/2613) :beetle:
  * Fix that lists are sorted alphabetically again [livingdocs-editor #2609](https://github.com/livingdocsIO/livingdocs-editor/pull/2609) :beetle:
  * Fix elasticsearch 6 support for optional date filters [livingdocs-server #2335](https://github.com/livingdocsIO/livingdocs-server/pull/2335) :beetle:
* Print
  * fix(printModal): delete keys and add remove button [livingdocs-editor #2622](https://github.com/livingdocsIO/livingdocs-editor/pull/2622) :gift:
  * Guard the access of publicationPreset if its undefined [livingdocs-editor #2619](https://github.com/livingdocsIO/livingdocs-editor/pull/2619) :gift:
  * Set a preset for a print publication [livingdocs-editor #2578](https://github.com/livingdocsIO/livingdocs-editor/pull/2578) :gift:
  * Robustify print modal and the template / layout mode [livingdocs-editor #2624](https://github.com/livingdocsIO/livingdocs-editor/pull/2624) :gift:
* Chore
  * Migrate from Travis CI to DroneCI [livingdocs-editor #2640](https://github.com/livingdocsIO/livingdocs-editor/pull/2640) :wrench:
* Service
  * Show google vision results for DAM [livingdocs-editor #2652](https://github.com/livingdocsIO/livingdocs-editor/pull/2652) :gift:
  * prefer use of base64 buffer in google vision API [livingdocs-server #2401](https://github.com/livingdocsIO/livingdocs-server/pull/2401) :gift:
  * Configurable image service in DAM [livingdocs-server #2343](https://github.com/livingdocsIO/livingdocs-server/pull/2343) :gift:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
