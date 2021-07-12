last editor version: 70.6.1
last server version: 138.0.1

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

## Responsive Editing Toolbar :tada:

With the introduction of more an more actions in the Document Editing Toolbar, space was getting rare, especially on smaller screens. Therefore a responsive editing toolbar has been introduced which collapse actions to groups when there is not enough space.

![Screenshot 2021-07-06 at 12 51 19](https://user-images.githubusercontent.com/821875/124588351-fd1da980-de58-11eb-87b8-ec5d3e9cda02.png)
![Screenshot 2021-07-06 at 12 51 38](https://user-images.githubusercontent.com/821875/124588354-fdb64000-de58-11eb-8c7a-8fd6b68a830b.png)
![Screenshot 2021-07-06 at 12 51 57](https://user-images.githubusercontent.com/821875/124588356-fe4ed680-de58-11eb-928f-e99dbddacce7.png)
![Screenshot 2021-07-06 at 12 53 02](https://user-images.githubusercontent.com/821875/124588454-1aeb0e80-de59-11eb-8895-bbcf59ebc960.png)

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4245)




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

#### Remove support for callbacks in a few server API's :fire:

We removed Callback support in several server API's. In the next releases we will continue with the removal of callbacks in server API's. All server API's already support Promises, therefore you can prepare the downstream migration from Callbacks to Promises.

- 🔥 remove callback support for designLoaderApi (`server.features.api('li-design-loader')`) functions. Only promise based calls are supported


##### Example how to migrate

Search e.g. for `li-design-loader` and replace all your code from a callback to a promise based approach (async/await). Please also consider your tests.

```js
// from
const designLoaderApi = liServer.features.api('li-design-loader')
designLoaderApi.loadConfig({
  name: req.params.name,
  version: req.params.version,
  projectId
}, (err, designConfig) => {
  if (err) return callback(err)
  // ...
})

// to
const designLoaderApi = liServer.features.api('li-design-loader')
const designConfig = await designLoaderApi.loadConfig({
  name: req.params.name,
  version: req.params.version,
  projectId
})
```

References:
- [designLoaderApi PR](https://github.com/livingdocsIO/livingdocs-server/pull/3845)


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


#### Data-Migration: remove callback support :fire:

🔥 The callback-based function `migrate` has been removed for a file data-migration. Use the promise based function `migrateAsync` instead.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3819)


#### Fix JSON patch operation of MediaLibraryEntries :fire:

We had some invalid data structures when an asset in the media library got replaced.

### Required action for downstreams :fire:

In case you had the replaceAsset functionality enabled, you might want to fix invalid data structures. To check whether there are existing archived assets, please execute that query:

```sql
SELECT *
FROM media_library_entries
WHERE data->'archivedAssets' IS NOT NULL;
```

In case you have broken assets, please execute the following migration.
We didn't put it into a new migration as the migration could block for too long.

```sql
CREATE OR REPLACE FUNCTION li_jsonb_extract_nested_image_objects(val jsonb, obj jsonb)
RETURNS jsonb
LANGUAGE plpgsql
IMMUTABLE
AS $$
DECLARE
  key text;
BEGIN
  IF jsonb_typeof(val) != 'object' THEN RETURN obj; END IF;
  IF val->'key' IS NOT NULL THEN RETURN obj || jsonb_build_object(val->>'key', val); END IF;
  FOR key IN SELECT * FROM jsonb_object_keys(val) LOOP
    obj := li_jsonb_extract_nested_image_objects(val->key, obj);
  END LOOP;
  RETURN obj;
END;
$$;

UPDATE media_library_entries
SET data = data || jsonb_build_object('archivedAssets', li_jsonb_extract_nested_image_objects(data->'archivedAssets', '{}'))
WHERE data->'archivedAssets' IS NOT NULL;
```

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3815)



# Deprecations




# APIs :gift:

## Server CLI

### livingdocs-server add-design

- renamed `livingdocs-server add-design` to `livingdocs-server design-add` (deprecate `add-design`)

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3844)


### livingdocs-server add-design

- add task to set current/active design `livingdocs-server design-set-active --project=<project handle> --design-version=<design-version>`

References:
* [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3841)


# Internal Changes




# Other Changes

### Features

* Indexing
  * Delay media indexing and notifications [livingdocs-server #3709](https://github.com/livingdocsIO/livingdocs-server/pull/3709) :gift:
  * Support a `maxCpuFunction` to retrieve the maximum cpu threshold during indexing [livingdocs-server #3701](https://github.com/livingdocsIO/livingdocs-server/pull/3701) :gift:
  * Add indexing config for li-datetime-validity plugin [livingdocs-server #3774](https://github.com/livingdocsIO/livingdocs-server/pull/3774) :gift:
  * Prevent implicit index creation in elasticsearch [livingdocs-server #3772](https://github.com/livingdocsIO/livingdocs-server/pull/3772) :gift:
* History
  * Allow to restore metadata [livingdocs-editor #4538](https://github.com/livingdocsIO/livingdocs-editor/pull/4538) :gift:
bugs

### Design

* Redesign Collaboration toolbar [livingdocs-editor #4484](https://github.com/livingdocsIO/livingdocs-editor/pull/4484) :gift:
* Redesign Translation popup [livingdocs-editor #4443](https://github.com/livingdocsIO/livingdocs-editor/pull/4443) :gift:


### Improvements

* Editor
  * Focus Editor when out of viewport [livingdocs-editor #4496](https://github.com/livingdocsIO/livingdocs-editor/pull/4496) :gift:
  * User Profile: Show active sessions [livingdocs-editor #4494](https://github.com/livingdocsIO/livingdocs-editor/pull/4494) :gift:
  * Lists: show error message when publishing a list fails [livingdocs-editor #4514](https://github.com/livingdocsIO/livingdocs-editor/pull/4514) :gift:
  * Dashboards: show a loading indicator [livingdocs-editor #4551](https://github.com/livingdocsIO/livingdocs-editor/pull/4551) :gift:
* Includes: Improve error handling [livingdocs-editor #4432](https://github.com/livingdocsIO/livingdocs-editor/pull/4432) :gift:
* Performance:
  * Streaming of image uploads [livingdocs-server #3758](https://github.com/livingdocsIO/livingdocs-server/pull/3758) :gift:
  * Streaming of file uploads [livingdocs-server #3738](https://github.com/livingdocsIO/livingdocs-server/pull/3738) :gift:
  * Only load the document content from postgres when requested [livingdocs-server #3721](https://github.com/livingdocsIO/livingdocs-server/pull/3721) :gift:
  * Fix AJV memory leak [livingdocs-server #3803](https://github.com/livingdocsIO/livingdocs-server/pull/3803) :gift:
* AWS: Upgrade AWS SES to use signature V4 [livingdocs-server #3730](https://github.com/livingdocsIO/livingdocs-server/pull/3730) :gift:
* Fix pool allocation timeouts in imports [livingdocs-server #3788](https://github.com/livingdocsIO/livingdocs-server/pull/3788) :gift:
* Collaboration: Do not rely on a hardcoded metadata property handle [livingdocs-editor #4501](https://github.com/livingdocsIO/livingdocs-editor/pull/4501) :gift:
* Indexing: Allow to id's instead of range for `addPublicationBackgroundIndexingJobsByIds` [livingdocs-server #3812](https://github.com/livingdocsIO/livingdocs-server/pull/3812) :gift:
* Migrations: Allow `--design-version-to=latest` param and do not allow to migrate to non existend design-version  [livingdocs-server #3814](https://github.com/livingdocsIO/livingdocs-server/pull/3814) :gift:


### Bugfixes

* Media Library
  * Use locale-specific image asset on drop if available [livingdocs-editor #4428](https://github.com/livingdocsIO/livingdocs-editor/pull/4428) :beetle:
  * Handle missing/archived images [livingdocs-editor #4495](https://github.com/livingdocsIO/livingdocs-editor/pull/4495) :beetle:
  * Asset Translation: Media Library video and file translation support [livingdocs-server #3708](https://github.com/livingdocsIO/livingdocs-server/pull/3708) :beetle:
  * Rerender angular wrapped metadata forms when entities change in videos [livingdocs-editor #4511](https://github.com/livingdocsIO/livingdocs-editor/pull/4511) :beetle:
  * IPTC Extraction: Improve compatibility with different storage formats for the Keyword tag [livingdocs-server #3760](https://github.com/livingdocsIO/livingdocs-server/pull/3760) :beetle:
  * Add posterImage to video directive schema [livingdocs-server #3786](https://github.com/livingdocsIO/livingdocs-server/pull/3786) :beetle:
  * Set posterImage attribute on video directive [livingdocs-editor #4503](https://github.com/livingdocsIO/livingdocs-editor/pull/4503) :beetle:
  * Consider readOnly config for metadata [livingdocs-editor #4517](https://github.com/livingdocsIO/livingdocs-editor/pull/4517) :beetle:
  * Use correct language for a link text when inserting a file into a document [livingdocs-editor #4526](https://github.com/livingdocsIO/livingdocs-editor/pull/4526) :beetle:
  * `li-meta-transcoding-state-form` UI updates after Video replacement [livingdocs-editor #4511](https://github.com/livingdocsIO/livingdocs-editor/pull/4511) :beetle:
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
  * add `comment.resolve` action to notifications [livingdocs-server #3806](https://github.com/livingdocsIO/livingdocs-server/pull/3806) :beetle:
  * Get a list of all slack users to send notifications [livingdocs-server #3831](https://github.com/livingdocsIO/livingdocs-server/pull/3831) :beetle:
* Comments
  * Allow user selection and deleting for mentions again (for the UI) [livingdocs-editor #4471](https://github.com/livingdocsIO/livingdocs-editor/pull/4471) :beetle:
  * Disable multiselect mode while editing a comment [livingdocs-editor #4478](https://github.com/livingdocsIO/livingdocs-editor/pull/4478) :beetle:
* Other
  * Drag + Drop: Correctly replace images & videos on DnD [livingdocs-editor #4462](https://github.com/livingdocsIO/livingdocs-editor/pull/4462) :beetle:
  * Livingdocs-server: fix `project-truncate` (also delete events table) [livingdocs-server #3802](https://github.com/livingdocsIO/livingdocs-server/pull/3802) :beetle:
  * Images: Show bigger crop preview if no more than 2 crops/ratios [livingdocs-editor #4519](https://github.com/livingdocsIO/livingdocs-editor/pull/4519) :beetle:


  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
