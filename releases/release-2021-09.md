last editor version: 70.0.4
last server version: 136.3.6

**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Newsletter](#newsletter)
- [Webinar](#webinar)
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


# Webinar

#### Features

* Recording: **TODO**
* Documentation: **TODO**

#### Developers

* Recording: **TODO**
* Slides: **TODO**

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2021-09`
`@livingdocs/editor` | `release-2021-09`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2021-09",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2021-09

### Livingdocs Server Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2021-09",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2021-09

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text





# Highlights

## Dashboard Cards Configuration for the Media Library :tada:

This feature allows you to register your own dashboard card in the Media Library. The default card `liMediaLibraryCard`, allows to be extended with additional metadata fields.

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4500)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3779)
  * [Documentation](https://github.com/livingdocsIO/documentation/pull/407)




# Breaking Changes :fire:

## Migrate the database

- Expected duration?
- Possible data losses?
- Is it a simple migration? (fast/easy downgradable)

```sh
# run grunt migrate to update to the newest database scheme
# migration - 111-add-comments-table.js
#   create comments table + add events to the stream_events_types table
livingdocs-server migrate up
```




#### Dashboard Card Configuration :fire:

:fire: Removed project config `mediaLibrary.dashboard.displayFilters`. Move `mediaLibrary.dashboard.displayFilters` config to `mediaType.editor.dashboard.displayFilters` on the relevant mediaType configs.

:fire: Media Type Dashboard configuration

If you configure both `mediaType.editor.dashboard` (the dashboard opened in modals and through the document editing toolbar) and `mediaType.editor.managementDashboard` (the dashboard opened through the main navigation), the config used for the `managementDashboard` is compiled from the `dashboard` config and the `managementDashboard` config by overwriting on a top-level property level. Before, if `managementDashboard` was configured, the `dashboard` configuration was completely ignored.

Example:

```js
// behaviour before this change: management dashboard would not contain a displayFilter
// behaviour after this change: management dashboard contains the displayFilter configured in dashboard
mediaType.editor: {
  dashboard: {
    displayFilters: [{filterName: 'myFilter'}]
  },
  managementDashboard: {
    baseFilters: [{filterName: 'myBaseFilter'}]
  }
}
```

To get the old behavior, configure like this:

```js
mediaType.editor: {
  dashboard: {
    displayFilters: [{filterName: 'myFilter'}]
  },
  managementDashboard: {
    baseFilters: [{filterName: 'myBaseFilter'}],
    displayFilters: []
  }
}
```

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4500)


#### Remove File Feature :fire:

- 🔥 Removed core feature `li-files`
- 🔥 Removed server API `liServer.features.api('li-files')`
- 🔥 Removed editing API `/files/upload`, use POST `/media-library/upload-file` instead

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3643)


#### Always activate copy component feature :fire:

🔥 Remove editor config `copy.componentCopyEnabled`. The setting has no effect anymore, component copy is always enabled.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4476)


#### Show insert component filter if there are more than 8 components :fire:

🔥 Remove editor config `app.editor.insertPanel.useAdvancedComponentGroups`. The setting has no effect anymore. The filter on the insert panel is always shown if there are more than 8 components.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4477)




# Deprecations




# APIs :gift:




# Internal Changes




# Other Changes

### Features

* Indexing
  * Delay media indexing and notifications [livingdocs-server #3709](https://github.com/livingdocsIO/livingdocs-server/pull/3709) :gift:
  * Support a `maxCpuFunction` to retrieve the maximum cpu threshold during indexing [livingdocs-server #3701](https://github.com/livingdocsIO/livingdocs-server/pull/3701) :gift:
  * Add indexing config for li-datetime-validity plugin [livingdocs-server #3774](https://github.com/livingdocsIO/livingdocs-server/pull/3774) :gift:
  * Prevent implicit index creation in elasticsearch [livingdocs-server #3772](https://github.com/livingdocsIO/livingdocs-server/pull/3772) :gift:

### Design

* Redesign Collaboration toolbar [livingdocs-editor #4484](https://github.com/livingdocsIO/livingdocs-editor/pull/4484) :gift:
* Redesign Translation popup [livingdocs-editor #4443](https://github.com/livingdocsIO/livingdocs-editor/pull/4443) :gift:


### Improvements

* Includes: Improve error handling [livingdocs-editor #4432](https://github.com/livingdocsIO/livingdocs-editor/pull/4432) :gift:
* Performance:
  * Streaming of image uploads [livingdocs-server #3758](https://github.com/livingdocsIO/livingdocs-server/pull/3758) :gift:
  * Streaming of file uploads [livingdocs-server #3738](https://github.com/livingdocsIO/livingdocs-server/pull/3738) :gift:
  * Only load the document content from postgres when requested [livingdocs-server #3721](https://github.com/livingdocsIO/livingdocs-server/pull/3721) :gift:
* AWS: Upgrade AWS SES to use signature V4 [livingdocs-server #3730](https://github.com/livingdocsIO/livingdocs-server/pull/3730) :gift:
* Fix pool allocation timeouts in imports [livingdocs-server #3788](https://github.com/livingdocsIO/livingdocs-server/pull/3788) :gift:
* Collaboration: Do not rely on a hardcoded metadata property handle [livingdocs-editor #4501](https://github.com/livingdocsIO/livingdocs-editor/pull/4501) :gift:

### Bugfixes

* Drag + Drop: Correctly replace images & videos on DnD [livingdocs-editor #4462](https://github.com/livingdocsIO/livingdocs-editor/pull/4462) :beetle:
* Media Library
  * Use locale-specific image asset on drop if available [livingdocs-editor #4428](https://github.com/livingdocsIO/livingdocs-editor/pull/4428) :beetle:
  * Handle missing/archived images [livingdocs-editor #4495](https://github.com/livingdocsIO/livingdocs-editor/pull/4495) :beetle:
  * Asset Translation: Media Library video and file translation support [livingdocs-server #3708](https://github.com/livingdocsIO/livingdocs-server/pull/3708) :beetle:
  * Rerender angular wrapped metadata forms when entities change in videos [livingdocs-editor #4511](https://github.com/livingdocsIO/livingdocs-editor/pull/4511) :beetle:
  * IPTC Extraction: Improve compatibility with different storage formats for the Keyword tag [livingdocs-server #3760](https://github.com/livingdocsIO/livingdocs-server/pull/3760) :beetle:
* Project
  * Fix project config state navigation [livingdocs-editor #4412](https://github.com/livingdocsIO/livingdocs-editor/pull/4412) :beetle:
  * Project: Respect last opened project after login / open base url [livingdocs-editor #4489](https://github.com/livingdocsIO/livingdocs-editor/pull/4489) :beetle:
* Indexing / Search
  * Retry Elasticsearch bulk requests when it reports "Too Many Requests" [livingdocs-server #3749](https://github.com/livingdocsIO/livingdocs-server/pull/3749) :beetle:
  * Fix Elasticsearch publication searches [livingdocs-server #3733](https://github.com/livingdocsIO/livingdocs-server/pull/3733) :beetle:
* Batching / Queueing
  * Batch revisions with batchSize 100 in the revision migrations [livingdocs-server #3780](https://github.com/livingdocsIO/livingdocs-server/pull/3780) :beetle:
  * Fix issue in xcleanup logic that transfers pending jobs to a new worker [livingdocs-server #3783](https://github.com/livingdocsIO/livingdocs-server/pull/3783) :beetle:
* Notification
  * Fix assign user to a task notification [livingdocs-server #3796](https://github.com/livingdocsIO/livingdocs-server/pull/3796) :beetle:
  * Fix `document.transform` notification [livingdocs-server #3791](https://github.com/livingdocsIO/livingdocs-server/pull/3791) :beetle:
* Comments
  * Allow user selection and deleting for mentions again (for the UI) [livingdocs-editor #4471](https://github.com/livingdocsIO/livingdocs-editor/pull/4471) :beetle:
  * Disable multiselect mode while editing a comment [livingdocs-editor #4478](https://github.com/livingdocsIO/livingdocs-editor/pull/4478) :beetle:


  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
