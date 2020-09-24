
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

* Recording: **TODO**
* Documentation: **TODO**

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2020-10`
`@livingdocs/editor` | `release-2020-10`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2020-10",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2020-10

### Livingdocs Server Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2020-10",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2020-10

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text





# Highlights

* Drag + drop Woodwing assets [livingdocs-editor #3771](https://github.com/livingdocsIO/livingdocs-editor/pull/3771) :gift:
* * v103.6.0 WoodWing assets integration [livingdocs-server #3079](https://github.com/livingdocsIO/livingdocs-server/pull/3079) :gift:
  * video - https://vimeo.com/444823016


Referenced Documents
* v57.16.0 Referenced Documents [livingdocs-editor #3796](https://github.com/livingdocsIO/livingdocs-editor/pull/3796) :gift:
* * v103.9.0 feat(index): index the teaserImage in example server [livingdocs-server #3140](https://github.com/livingdocsIO/livingdocs-server/pull/3140) :gift:


Parallel Image Upload
* v57.18.0 (Media Library) parallel upload and mass metadata editing when uploading images with required metadata [livingdocs-editor #3814](https://github.com/livingdocsIO/livingdocs-editor/pull/3814) :gift:


Image Service 2.0
...breaking!...
* v104.0.0 fix(dependencies): update framework 15.1.0 -> 16.0.1 [livingdocs-server #3144](https://github.com/livingdocsIO/livingdocs-server/pull/3144) :gift:
* v57.17.1 Framework Image Service 2.0 [livingdocs-editor #3833](https://github.com/livingdocsIO/livingdocs-editor/pull/3833) :gift:
* https://github.com/livingdocsIO/livingdocs-framework/pull/497

Doc Include
* Includes: Allow to implement includes via Vue [livingdocs-editor #3768](https://github.com/livingdocsIO/livingdocs-editor/pull/3768) :gift:
* https://github.com/livingdocsIO/livingdocs/pull/312

## EXAMPLE :tada:

...Description...

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/2143)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/246)




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




# Deprecations

## Deprecate asset management server config

Pull Request: [livingdocs-server #3086](https://github.com/livingdocsIO/livingdocs-server/pull/3086)

- ⏳ Deprecated static server config `assetManagement`. Rename `assetManagement` to `mediaLibrary`
- ⏳ Remove property `assetManagement.enabled` (currently it only throws a deprecation message)
- ⏳ Remove property `assetManagement.googleVision` (currently it only throws a deprecation message)

## Deprecate MediaLibrary paginationSize

Pull Request: [livingdocs-server #3092](https://github.com/livingdocsIO/livingdocs-server/pull/3092)

- ⏳ deprecate static server config `mediaLibrary.paginationSize`. The config will be removed in the next releases but has already no effect anymore. We use an internal default of 35.

## Data Migrations

Pull Request: [livingdocs-server #3151](https://github.com/livingdocsIO/livingdocs-server/pull/3151) :gift:

- ⏳ `grunt data-migration-create-and-prepare` should not be used anymore. The task has been replaced with `livingdocs-server data-migration-run`
- ⏳ `grunt data-migration-accept` should not be used anymore. The task has been replaced with `livingdocs-server data-migration-run`




# APIs :gift:

custom vue filter
* Add api for registering custom vue filters [livingdocs-editor #3777](https://github.com/livingdocsIO/livingdocs-editor/pull/3777) :gift:

media lib public api
* v103.5.1 Media Library: Public API [livingdocs-server #3099](https://github.com/livingdocsIO/livingdocs-server/pull/3099) :gift:

expose public api internally
* v103.8.7 Expose public api internally [livingdocs-server #3138](https://github.com/livingdocsIO/livingdocs-server/pull/3138) :gift:

client-defined id for import api
* v103.10.0 Support a client-defined document id in the import api [livingdocs-server #3145](https://github.com/livingdocsIO/livingdocs-server/pull/3145) :gift:

livingdocs-server CLI - data-migrration
* v103.12.0 New CLI task: livingdocs-server data-migration-run [livingdocs-server #3151](https://github.com/livingdocsIO/livingdocs-server/pull/3151) :gift:
* v103.11.0 Data Migration:  Report not applied documents [livingdocs-server #3148](https://github.com/livingdocsIO/livingdocs-server/pull/3148) :gift:

livingdocs-server CLI
* v104.1.0 Improve reindex tasks [livingdocs-server #3162](https://github.com/livingdocsIO/livingdocs-server/pull/3162) :gift:





# Internal Changes

Changes that should not affect customers.
But some customers use internal functions and can be affected by this changes.

## CSS Changes

Issue: https://github.com/livingdocsIO/livingdocs-editor/pull/3801

```
// renamed CSS classes
ld-filter-toolbar -> li-filter-toolbar
ld-filter.is-disabled renamed to li-filter-group__item--disabled
ld-filter.is-set renamed to li-filter-group__item--active

// removed CSS classes
ld-filter
ld-filter-options
```




# Other Changes

### Features

* ... :gift:

### Design

* ... :gift:

### Improvements

* ... :gift:

### Bugfixes

* ... :beetle:



* UI/UX
  * A lot of small UI hint additions [livingdocs-editor #3835](https://github.com/livingdocsIO/livingdocs-editor/pull/3835) :gift:


Improvements:
* Redis Add Redis debug logs and automatically reconnect against primary [livingdocs-server #3156](https://github.com/livingdocsIO/livingdocs-server/pull/3156) :gift:
* Woodwing assets: Use S3 URL for Woodwing assets [livingdocs-server #3132](https://github.com/livingdocsIO/livingdocs-server/pull/3132) :gift:
* Livingdocs CLI: Add --throttle argument to fix high CPU load during data cleanup tasks [livingdocs-server #3128](https://github.com/livingdocsIO/livingdocs-server/pull/3128) :gift:
* Public API: Never return HTTP Status 500 [livingdocs-server #3111](https://github.com/livingdocsIO/livingdocs-server/pull/3111) :gift:
* Project seeding: Always log seeding errors [livingdocs-server #3115](https://github.com/livingdocsIO/livingdocs-server/pull/3115) :gift:
* Image component: Improved sidepanel message of image component [livingdocs-editor #3879](https://github.com/livingdocsIO/livingdocs-editor/pull/3879) :gift:
* Publish Screen: Show loading button while image is uploading in metadata image form [livingdocs-editor #3839](https://github.com/livingdocsIO/livingdocs-editor/pull/3839) :gift:
* Dashboards/User Profile Menu: Small Wording Improvements [livingdocs-editor #3824](https://github.com/livingdocsIO/livingdocs-editor/pull/3824) :gift:
* Display Filter: Support relative date range filters [livingdocs-editor #3813](https://github.com/livingdocsIO/livingdocs-editor/pull/3813) :gift:
* Media Library: Show message when no document has an image reference [livingdocs-editor #3826](https://github.com/livingdocsIO/livingdocs-editor/pull/3826) :gift:
* Media Library: Show proper message when image is broken [livingdocs-editor #3828](https://github.com/livingdocsIO/livingdocs-editor/pull/3828) :gift:
* Imatrics: store any concept properties returned from the server [livingdocs-editor #3837](https://github.com/livingdocsIO/livingdocs-editor/pull/3837) :gift:
* Imatrics: updates suggestion in realtime [livingdocs-editor #3817](https://github.com/livingdocsIO/livingdocs-editor/pull/3817) :gift:
* Imatrics: Do not trigger imatrics updates if imatrics is not initialized [livingdocs-editor #3870](https://github.com/livingdocsIO/livingdocs-editor/pull/3870) :gift:
* List Dashboard: Empty state and search improvements [livingdocs-editor #3812](https://github.com/livingdocsIO/livingdocs-editor/pull/3812) :gift:
* Dashboard: Display filter wrapping [livingdocs-editor #3801](https://github.com/livingdocsIO/livingdocs-editor/pull/3801) :gift:
* Publish Screen: Add character counter on metadata fields [livingdocs-editor #3769](https://github.com/livingdocsIO/livingdocs-editor/pull/3769) :gift:
* Metadata: Add config to set displayfilters on the liMetaReferenceForm [livingdocs-editor #3780](https://github.com/livingdocsIO/livingdocs-editor/pull/3780) :gift:
* Improve rich list actions CSS (e.g. list on the dashboard) [livingdocs-editor #3811](https://github.com/livingdocsIO/livingdocs-editor/pull/3811) :gift:
* Project select screen: Enable scrolling [livingdocs-editor #3875](https://github.com/livingdocsIO/livingdocs-editor/pull/3875) :gift:


Bugfixes
* Image upload: Fix image uploads for PDF's when using imagemagick [livingdocs-server #3134](https://github.com/livingdocsIO/livingdocs-server/pull/3134) :gift:
* Public API: Don't validate hardcoded image metadata of image import, use the dynamic config instead [livingdocs-server #3121](https://github.com/livingdocsIO/livingdocs-server/pull/3121) :gift:
* UserApi: Fix userApi.findByProjectId pagination [livingdocs-server #3119](https://github.com/livingdocsIO/livingdocs-server/pull/3119) :gift:
* Publication index: Fix inconsistency in publication query builder [livingdocs-server #3112](https://github.com/livingdocsIO/livingdocs-server/pull/3112) :gift:
* Hugo: Image dnd does work with enforced metadata [livingdocs-server #3102](https://github.com/livingdocsIO/livingdocs-server/pull/3102) :gift:
* Includes: fix youtube and instagram include [livingdocs-server #2939](https://github.com/livingdocsIO/livingdocs-server/pull/2939) :gift:
* User: Fix user merge and also empty WHERE IN database queries [livingdocs-server #3093](https://github.com/livingdocsIO/livingdocs-server/pull/3093) :gift:
* Publication date: Show correct date for future publication [livingdocs-editor #3865](https://github.com/livingdocsIO/livingdocs-editor/pull/3865) :gift:
* Spellcheck: Fix browser spellcheck document creation [livingdocs-editor #3853](https://github.com/livingdocsIO/livingdocs-editor/pull/3853) :gift:
* Fix Category display filter [livingdocs-editor #3850](https://github.com/livingdocsIO/livingdocs-editor/pull/3850) :gift:
* Dashboard: Fix context menu behaviour [livingdocs-editor #3843](https://github.com/livingdocsIO/livingdocs-editor/pull/3843) :gift:
* Project setup: Show Integrations only if there are some [livingdocs-editor #3823](https://github.com/livingdocsIO/livingdocs-editor/pull/3823) :gift:
* Notifications: Fix drop indicator for hugo and asset drop [livingdocs-editor #3831](https://github.com/livingdocsIO/livingdocs-editor/pull/3831) :gift:
* Comments: Update metadata comment count only locally [livingdocs-editor #3816](https://github.com/livingdocsIO/livingdocs-editor/pull/3816) :gift:
* Fix google vision setup form [livingdocs-editor #3805](https://github.com/livingdocsIO/livingdocs-editor/pull/3805) :gift:
* Do not display image thumbnails in original image size [livingdocs-editor #3799](https://github.com/livingdocsIO/livingdocs-editor/pull/3799) :gift:
* Publish Screen: List assignment works correctly again [livingdocs-editor #3781](https://github.com/livingdocsIO/livingdocs-editor/pull/3781) :gift:
* Fix webhook settings screen [livingdocs-editor #3775](https://github.com/livingdocsIO/livingdocs-editor/pull/3775) :gift:
* Menu: Fix Menu Sorting  [livingdocs-editor #3765](https://github.com/livingdocsIO/livingdocs-editor/pull/3765) :gift:
* Improves the instagram include sidebar [livingdocs-editor #3487](https://github.com/livingdocsIO/livingdocs-editor/pull/3487) :gift:
* Various release bug fixes [livingdocs-editor #3763](https://github.com/livingdocsIO/livingdocs-editor/pull/3763) :gift:
* Show scrollbar in read-only views [livingdocs-editor #3758](https://github.com/livingdocsIO/livingdocs-editor/pull/3758) :gift:
* History: Correctly load older revisions for the history [livingdocs-editor #3756](https://github.com/livingdocsIO/livingdocs-editor/pull/3756) :gift:
* Fix default redirect for articles [livingdocs-editor #3755](https://github.com/livingdocsIO/livingdocs-editor/pull/3755) :gift:
* Document copy: Correct copy behavior for articles with langauges and translations [livingdocs-server #3087](https://github.com/livingdocsIO/livingdocs-server/pull/3087)
* Document creation: Fix broken setup for content types with languages [livingdocs-editor #3748](https://github.com/livingdocsIO/livingdocs-editor/pull/3748) :beetle:
  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
