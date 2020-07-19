INFO:
- editor: until 57.5.1
- server: until 103.3.2


**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Patches](#repositories)
- [Highlights](#highlights)
- [Breaking Changes](#breaking-changes-fire)
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
  https://github.com/livingdocsIO/livingdocs-server/tree/release-YYYY-MM

### Livingdocs Server Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2020-07",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-YYYY-MM

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text



# Highlights

----------- alt text prefilling -------------
https://github.com/livingdocsIO/livingdocs-editor/pull/3699
* v102.5.0 Image alt text [livingdocs-server #3043](https://github.com/livingdocsIO/livingdocs-server/pull/3043) :gift:

----------- custom text formatting -----------------
DO: meinrad - write documentation - https://github.com/livingdocsIO/livingdocs-editor/pull/3719#issuecomment-660630314
* v57.3.0 Add custom text formatting [livingdocs-editor #3719](https://github.com/livingdocsIO/livingdocs-editor/pull/3719) :gift:
* v103.3.0 Add custom text formatting [livingdocs-server #3070](https://github.com/livingdocsIO/livingdocs-server/pull/3070) :gift:


------------ Display Filter -------------------
new liDateTimeRange filter
* v56.8.0 Time Range Dashboard Filter [livingdocs-editor #3670](https://github.com/livingdocsIO/livingdocs-editor/pull/3670) :gift:
pass config to display filter
* v56.10.0 Display Filter: Pass Config Object to Filters [livingdocs-editor #3697](https://github.com/livingdocsIO/livingdocs-editor/pull/3697) :gift:
DO: isDefault Option
* v57.4.0 Feature: isDefault Option for Default Display Filter [livingdocs-editor #3716](https://github.com/livingdocsIO/livingdocs-editor/pull/3716) :gift:



---------- restore project config / diff project config history -------------
* v51.6.0 Allow to restore a project config [livingdocs-editor #3475](https://github.com/livingdocsIO/livingdocs-editor/pull/3475) :gift:
* v96.2.0 Add compare channel-config route [livingdocs-server #2952](https://github.com/livingdocsIO/livingdocs-server/pull/2952) :gift:


---------------- startpage config -----------------------
DO: Breaking Change!
* v101.4.4 Allow startPage configuration in editor settings [livingdocs-server #3031](https://github.com/livingdocsIO/livingdocs-server/pull/3031) :gift:
* v56.0.0 Ability to configure entry point dashboard [livingdocs-editor #3687](https://github.com/livingdocsIO/livingdocs-editor/pull/3687) :gift:


----------- add custom user menu --------------
* v101.1.0 Feat: Custom user menu configuration [livingdocs-server #2996](https://github.com/livingdocsIO/livingdocs-server/pull/2996) :gift:
* v53.3.0 Feat: Custom user menu configuration [livingdocs-editor #3603](https://github.com/livingdocsIO/livingdocs-editor/pull/3603) :gift:
DO: Okan add doc - https://github.com/livingdocsIO/livingdocs-server/pull/2996#issuecomment-660605503


------------ livingdocs notifications --------------------
DO: breaking changes / internal breaking changes
DO: maybe draw attention to screenshots
* v52.5.0 Feat: revamp livingdocs notifications  [livingdocs-editor #3533](https://github.com/livingdocsIO/livingdocs-editor/pull/3533) :gift:


------------- Import Log Viewer -------------------------
DO: add testrail cases
Q: to myself: cypress test?
* v52.6.0 Import log viewer [livingdocs-editor #3616](https://github.com/livingdocsIO/livingdocs-editor/pull/3616) :gift:
* v100.2.0 Import log viewer [livingdocs-server #3002](https://github.com/livingdocsIO/livingdocs-server/pull/3002) :gift:




------------------------
------------------------
media library
DO: read and compose the logs
* v57.0.1 fix(media library): disable dragging cards in media library and in media library selection modal [livingdocs-editor #3713](https://github.com/livingdocsIO/livingdocs-editor/pull/3713) :gift:
* v56.12.2 remove and add expired image indication on directive update [livingdocs-editor #3708](https://github.com/livingdocsIO/livingdocs-editor/pull/3708) :gift:
* v56.12.0 Media Library: refactor media library upload to take state from imageUploadService, remove mediaLibraryUploadService [livingdocs-editor #3703](https://github.com/livingdocsIO/livingdocs-editor/pull/3703) :gift:
* v56.11.0 Media library selection modal [livingdocs-editor #3706](https://github.com/livingdocsIO/livingdocs-editor/pull/3706) :gift:
* v56.9.0 (Media Library) set image component directives from metadata based on componentDirectivesPrefilling config [livingdocs-editor #3698](https://github.com/livingdocsIO/livingdocs-editor/pull/3698) :gift:
* v56.7.1 (Media Library) rename extractMetadata to extractExif & mediaLibrary.enabled -> mediaLibrary.showUi [livingdocs-editor #3696](https://github.com/livingdocsIO/livingdocs-editor/pull/3696) :gift:
* v56.7.0 Media library in toolbar [livingdocs-editor #3692](https://github.com/livingdocsIO/livingdocs-editor/pull/3692) :gift:
* v56.6.0 (Media Library) Extract metadata when form for required metadata properties is shown [livingdocs-editor #3690](https://github.com/livingdocsIO/livingdocs-editor/pull/3690) :gift:
* v56.4.0 Support "media library -> document" drag and drop [livingdocs-editor #3640](https://github.com/livingdocsIO/livingdocs-editor/pull/3640) :gift:
* v56.3.0 Media library validity support [livingdocs-editor #3688](https://github.com/livingdocsIO/livingdocs-editor/pull/3688) :gift:
* v56.2.0 Create MediaLibrary Config based on Project Config [livingdocs-editor #3691](https://github.com/livingdocsIO/livingdocs-editor/pull/3691) :gift:
* v56.1.0 Adapt Media Library Search to the new API [livingdocs-editor #3689](https://github.com/livingdocsIO/livingdocs-editor/pull/3689) :gift:
* v55.0.1 fix(asset proxy) add asset.url to MediaLibraryEntry in resolve value to assetProxy.postImage for compatibility reasons [livingdocs-editor #3686](https://github.com/livingdocsIO/livingdocs-editor/pull/3686) :gift:
* v55.0.0 (MediaLibrary): Introduce and use MediaLibraryEntry model [livingdocs-editor #3680](https://github.com/livingdocsIO/livingdocs-editor/pull/3680) :gift:
* v54.2.0 (Media Library) Image Upload Service / Metadata Form Validations [livingdocs-editor #3661](https://github.com/livingdocsIO/livingdocs-editor/pull/3661) :gift:
* v54.0.0 feat: media library UI can now be turned off [livingdocs-editor #3667](https://github.com/livingdocsIO/livingdocs-editor/pull/3667) :gift:
* v53.6.0 Introduce default Proofreading and Media Library Navigation Menu [livingdocs-editor #3666](https://github.com/livingdocsIO/livingdocs-editor/pull/3666) :gift:
* v53.5.0 Dashboard: Vueify MediaLibraryCard [livingdocs-editor #3628](https://github.com/livingdocsIO/livingdocs-editor/pull/3628) :gift:
* v53.4.0 Render required metadata form with form generator [livingdocs-editor #3636](https://github.com/livingdocsIO/livingdocs-editor/pull/3636) :gift:
* v53.2.0 Embed custom media library dashboard into editor sidebar [livingdocs-editor #3604](https://github.com/livingdocsIO/livingdocs-editor/pull/3604) :gift:
* v53.0.0 Migrate /documents?q=Text to /documents?search=Text [livingdocs-editor #3630](https://github.com/livingdocsIO/livingdocs-editor/pull/3630) :gift:
* v52.7.0 (Media Library) use mediaTypes for metadata configuration [livingdocs-editor #3613](https://github.com/livingdocsIO/livingdocs-editor/pull/3613) :gift:
* v52.3.0 (BC!!!!)Refactor image uploading workflow, introduce a imageUploadService [livingdocs-editor #3430](https://github.com/livingdocsIO/livingdocs-editor/pull/3430) :gift:
* v52.2.0 MediaLibrary as Custom Dashboard - Iteration 1 [livingdocs-editor #3562](https://github.com/livingdocsIO/livingdocs-editor/pull/3562) :gift:
* v51.12.2 fix: correctly set label for uploaded files [livingdocs-editor #3565](https://github.com/livingdocsIO/livingdocs-editor/pull/3565) :gift:
* v51.8.0 feat: enforce image metadata during bulk upload [livingdocs-editor #3544](https://github.com/livingdocsIO/livingdocs-editor/pull/3544) :gift:




* v103.2.2 Revert e2e media library filter back to timeRange to prevent fai… [livingdocs-server #3077](https://github.com/livingdocsIO/livingdocs-server/pull/3077) :gift:
* v103.2.0 Validate Media Library Entries Metadata Values [livingdocs-server #3074](https://github.com/livingdocsIO/livingdocs-server/pull/3074) :gift:
* v102.4.2 Make media library displayFilter schema more strict [livingdocs-server #3055](https://github.com/livingdocsIO/livingdocs-server/pull/3055) :gift:
* v102.3.1 (Media Library) rename metadataExtraction to exifExtraction & mediaLibrary.enabled to mediaLibrary.showUi [livingdocs-server #3051](https://github.com/livingdocsIO/livingdocs-server/pull/3051) :gift:
* v102.2.1 fix(e2e): fix mediaType configuration [livingdocs-server #3039](https://github.com/livingdocsIO/livingdocs-server/pull/3039) :gift:
* v102.2.0 (Media Library) metadata extraction [livingdocs-server #3035](https://github.com/livingdocsIO/livingdocs-server/pull/3035) :gift:
* v102.0.0 Media Library [livingdocs-server #3030](https://github.com/livingdocsIO/livingdocs-server/pull/3030) :gift:
* v101.2.0 feat: add projectConfig.editorSettings.mediaLibrary.enabled [livingdocs-server #3027](https://github.com/livingdocsIO/livingdocs-server/pull/3027) :gift:
* v101.0.0 (breaking CHANGE!!) Migrate /documents?q=Text to /documents?search=Text [livingdocs-server #3004](https://github.com/livingdocsIO/livingdocs-server/pull/3004) :gift:
* v100.3.0 Project Config: MediaTypes [livingdocs-server #3001](https://github.com/livingdocsIO/livingdocs-server/pull/3001) :gift:
* v99.0.0 Rename li-asset-management to li-media-library [livingdocs-server #2993](https://github.com/livingdocsIO/livingdocs-server/pull/2993) :gift:
* v96.3.2 Fix media re-indexing [livingdocs-server #2968](https://github.com/livingdocsIO/livingdocs-server/pull/2968) :gift:
------------------------
------------------------


------------------------
------------------------
imatrics/tagging (+breaking change!)

* v52.1.0 Tags / iMatrics [livingdocs-editor #3593](https://github.com/livingdocsIO/livingdocs-editor/pull/3593) :gift:
* v57.5.0 Improve iMatrics metadata updates [livingdocs-editor #3673](https://github.com/livingdocsIO/livingdocs-editor/pull/3673) :gift:
  - * v103.3.2 Metadata property update [livingdocs-server #3068](https://github.com/livingdocsIO/livingdocs-server/pull/3068) :gift:
* v54.2.3 fix(imatrics): improve error handling [livingdocs-editor #3681](https://github.com/livingdocsIO/livingdocs-editor/pull/3681) :gift:
* v54.1.0 feat(imatrics): add event and object entity types [livingdocs-editor #3629](https://github.com/livingdocsIO/livingdocs-editor/pull/3629) :gift:
* v52.2.1 fix(imatrics): do not log errors from li-taglist on publish screen [livingdocs-editor #3608](https://github.com/livingdocsIO/livingdocs-editor/pull/3608) :gift:
* v101.4.3 fix(imatrics): Allow value `0` for minchars [livingdocs-server #3033](https://github.com/livingdocsIO/livingdocs-server/pull/3033) :gift:
* v101.4.2 fix(imatrics): improve IMatricsTextTooShortError error case [livingdocs-server #3029](https://github.com/livingdocsIO/livingdocs-server/pull/3029) :gift:
* v101.1.4 fix(imatrics): make imatrics tag schema more flexibel by allowing additional properties [livingdocs-server #3017](https://github.com/livingdocsIO/livingdocs-server/pull/3017) :gift:


------------------------
------------------------









# Breaking Changes :fire:

Node 14, drop node 10
* v51.0.0 Add node 14, drop node 10 support [livingdocs-editor #3505](https://github.com/livingdocsIO/livingdocs-editor/pull/3505) :gift:

Renamed Icons for server config
* v51.0.1 Remove unsupported icons from icon list [livingdocs-editor #3506](https://github.com/livingdocsIO/livingdocs-editor/pull/3506) :gift:
https://github.com/livingdocsIO/livingdocs-server/pull/2942

Google Vision Config
* v51.12.0 Configure Google Vision as integration [livingdocs-editor #3555](https://github.com/livingdocsIO/livingdocs-editor/pull/3555) :gift:
* v97.0.0 Move google vision config [livingdocs-server #2969](https://github.com/livingdocsIO/livingdocs-server/pull/2969) :gift:

Show Schedule Publishing Dates
Q: field names - https://github.com/livingdocsIO/livingdocs-editor/pull/3662#issuecomment-660628545
* v57.0.0 Show scheduled publishing dates on the publish cards in the metadata screen [livingdocs-editor #3662](https://github.com/livingdocsIO/livingdocs-editor/pull/3662) :gift:



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


## EXAMPLE !!!!!!!!!!!!!!!!!!! Update Elasticsearch Index

We now only store the reference to a user (`userId`) instead of the whole `user` object in Elasticsearch...

### Changes
These properties were added/deprecated from the document index...
- :fire: deprecated `last_publication`
- :fire: removed `last_publication`
- :heavy_plus_sign: added `last_publication`
- :heavy_minus_sign: removed `last_publication`
- :recycle: refactored `last_publication`

### Needed Actions :fire:
- :fire: Check and update your code to not use deprecated fields
- :fire: The mapping should update automatically during server start. If indexing fails for some reason, please run grunt `search-index:documents:update-mapping`
- optionally reindex calling `livingdocs-server search-index`

**Example**

```js
// Before
const registrationApi = liServer.features.api('li-registration')
registrationApi.registerProjectBuilder({
  handle: 'awesome-project',
  builder: ({userId}, builderConfig, callback) => {
    buildMyAwesomeProject({userId}, builderConfig, callback)
  }
})

// Now
const projectBuildersApi = liServer.features.api('li-project-builders')
projectBuildersApi.registerBuilder({
  handle: 'awesome-project',
  async builder ({userId}, builderConfig) {
    const project = await buildMyAwesomeProject({userId}, builderConfig)
    return project
  }
})
```

* References
  * [server PR #2426](https://github.com/livingdocsIO/livingdocs-server/pull/2426)


# APIs :gift:

* Added Curl examples for the public API [livingdocs-editor #3549](https://github.com/livingdocsIO/livingdocs-editor/pull/3549) :gift:

Q: maybe add new section configs?
move editor settings - https://github.com/livingdocsIO/livingdocs-editor/pull/3663
* v101.3.0 New projectConfig.editorSettings properties (mainNavigation, dashboards) [livingdocs-server #3024](https://github.com/livingdocsIO/livingdocs-server/pull/3024) :gift:


# Internal Changes

## Rename ld_icon

Renames `ld_icon` to `li-icon`. If you use any icons you have to use them like this now:
  `<li-icon name="icon-name" theme=""></li-icon>`. Where `theme` can hold the previous modifier classes: `class="li-icon--warning"` becomes `theme="warning"`.

PR: [livingdocs-editor #3492](https://github.com/livingdocsIO/livingdocs-editor/pull/3492)

# Other Changes

### Features

* ... :gift:

### Design

* ... :gift:

### Improvements

* ... :gift:

### Bugfixes

* ... :beetle:






Open Questions

---------
Q: Missing Documentation: https://github.com/livingdocsIO/livingdocs-server/pull/2959#issuecomment-659931193
Q: New Testrail Testcase?
* v51.7.0 Editor: Configurable List Search Config [livingdocs-editor #3537](https://github.com/livingdocsIO/livingdocs-editor/pull/3537) :gift:
* v96.2.3 Server: Configurable List Search Config [livingdocs-server #2959](https://github.com/livingdocsIO/livingdocs-server/pull/2959) :gift:
---------
Embedded Design
Q: Gabriel test - feedback if it works - https://github.com/livingdocsIO/livingdocs-editor/pull/3441#issuecomment-659909071
DO: Add new Testrail case
* v96.0.1 Manage component groups [livingdocs-server #2926](https://github.com/livingdocsIO/livingdocs-server/pull/2926) :gift:
* v51.2.0 Manage component groups [livingdocs-editor #3441](https://github.com/livingdocsIO/livingdocs-editor/pull/3441) :gift:
---------
Form Generator
Q: doc? where is it used? what fields supported? https://github.com/livingdocsIO/livingdocs-editor/pull/3526#issuecomment-659949062
* Form Generator add `li-boolean` type form [livingdocs-editor #3526](https://github.com/livingdocsIO/livingdocs-editor/pull/3526) :gift:
--------
Preview API
Q: preview feature documented somewhere? https://github.com/livingdocsIO/livingdocs-editor/pull/3585#issuecomment-660599040
* v52.0.4 Fix: support previewUrl for custom document previews [livingdocs-editor #3585](https://github.com/livingdocsIO/livingdocs-editor/pull/3585) :gift:



Main Navigation
* (BREAKING!!!) Allow custom components in MainMenu [livingdocs-editor #3584](https://github.com/livingdocsIO/livingdocs-editor/pull/3584) :gift:
* v52.0.2 fix(main nav): recalculate isActive state after navigation success [livingdocs-editor #3597](https://github.com/livingdocsIO/livingdocs-editor/pull/3597) :gift:


Bugs
* Language: show/hide li-language metadata form based on a behavior [livingdocs-editor #3527](https://github.com/livingdocsIO/livingdocs-editor/pull/3527) :gift:
* Allow to exclude whole components from text-counter [livingdocs-editor #3329](https://github.com/livingdocsIO/livingdocs-editor/pull/3329) :gift:
* Fix create document modal and ios navi [livingdocs-editor #3567](https://github.com/livingdocsIO/livingdocs-editor/pull/3567) :gift:
* v51.12.5 fix: add uploadImage function to iFrameview [livingdocs-editor #3582](https://github.com/livingdocsIO/livingdocs-editor/pull/3582) :gift:
* v52.6.3 fix(webpack): fix style alias to work in downstreams [livingdocs-editor #3621](https://github.com/livingdocsIO/livingdocs-editor/pull/3621) :gift:
* DO: big pr, check again - v53.1.0 Fix: (vueified) document copy&embeds relation cards now correctly show as published [livingdocs-editor #3614](https://github.com/livingdocsIO/livingdocs-editor/pull/3614) :gift:
* v53.1.1 Fix multiline comment support [livingdocs-editor #3633](https://github.com/livingdocsIO/livingdocs-editor/pull/3633) :gift:
* v53.4.7 fix recover on conflicts with metadata changes on server [livingdocs-editor #3642](https://github.com/livingdocsIO/livingdocs-editor/pull/3642) :gift:


Improvement

Improvement Publish Screen Error Handling
* Publish Screen: Show an error message on error during property form rendering [livingdocs-editor #3519](https://github.com/livingdocsIO/livingdocs-editor/pull/3519) :gift:
* v51.5.0 Show multiple validation errors on the publish screen [livingdocs-editor #3513](https://github.com/livingdocsIO/livingdocs-editor/pull/3513) :gift:
* v57.1.0 liMetaReferenceForm now has the correct filters for its document types [livingdocs-editor #3711](https://github.com/livingdocsIO/livingdocs-editor/pull/3711) :gift:




Improvements
* v56.10.1 Allow to change language if no translations yet [livingdocs-editor #3700](https://github.com/livingdocsIO/livingdocs-editor/pull/3700) :gift:
* v52.6.1 fix: improve visiblity of urgent proofreading tasks and deadlines [livingdocs-editor #3618](https://github.com/livingdocsIO/livingdocs-editor/pull/3618) :gift:


live coverage
* Fix insert proposal [livingdocs-editor #3491](https://github.com/livingdocsIO/livingdocs-editor/pull/3491) :gift:
* v51.12.3 Adapt live coverage ui [livingdocs-editor #3572](https://github.com/livingdocsIO/livingdocs-editor/pull/3572) :gift:

realtime collab
* Refactor component locks and add them also for proposals [livingdocs-editor #3517](https://github.com/livingdocsIO/livingdocs-editor/pull/3517) :gift:
* Fix component locks and history overlays [livingdocs-editor #3509](https://github.com/livingdocsIO/livingdocs-editor/pull/3509) :gift:
* Fix close on include modal and remove lock on idle [livingdocs-editor #3530](https://github.com/livingdocsIO/livingdocs-editor/pull/3530) :gift:
* v51.12.6 Only blur component if focused on component lock [livingdocs-editor #3586](https://github.com/livingdocsIO/livingdocs-editor/pull/3586) :gift:
* v52.6.5 Fix conflict with self [livingdocs-editor #3605](https://github.com/livingdocsIO/livingdocs-editor/pull/3605) :gift:
* v53.5.1 show insert in format panel and register empty click for it [livingdocs-editor #3637](https://github.com/livingdocsIO/livingdocs-editor/pull/3637) :gift:
* v53.5.2 add comment and cancel btn to comment card [livingdocs-editor #3664](https://github.com/livingdocsIO/livingdocs-editor/pull/3664) :gift:
* v56.12.3 fix reopen a comment and check if objects already exists [livingdocs-editor #3714](https://github.com/livingdocsIO/livingdocs-editor/pull/3714) :gift:

webhooks
* Webhooks: Validate form and show error messages [livingdocs-editor #3507](https://github.com/livingdocsIO/livingdocs-editor/pull/3507) :gift:

Internal Changes - Vue
* Vue styleguide [livingdocs-editor #3500](https://github.com/livingdocsIO/livingdocs-editor/pull/3500) :gift:
* Support vue mixin props in the angular vue wrapper [livingdocs-editor #3511](https://github.com/livingdocsIO/livingdocs-editor/pull/3511) :gift:
* Vueify project settings screen + add new component li-multi-select [livingdocs-editor #3515](https://github.com/livingdocsIO/livingdocs-editor/pull/3515) :gift:
* v52.3.1 Refactoring: Vueify liDashboardTitle [livingdocs-editor #3607](https://github.com/livingdocsIO/livingdocs-editor/pull/3607) :gift:
* v53.2.1 Refactoring: migrate li-create-document-button from angular to vue [livingdocs-editor #3609](https://github.com/livingdocsIO/livingdocs-editor/pull/3609) :gift:
* v56.5.0 vue-form-generator: support date picker [livingdocs-editor #3671](https://github.com/livingdocsIO/livingdocs-editor/pull/3671) :gift:

Internal Changes - Cypress
* v53.4.1 Cypress logs [livingdocs-editor #3594](https://github.com/livingdocsIO/livingdocs-editor/pull/3594) :gift:
* v101.0.1 Fix cypress login tests [livingdocs-server #3010](https://github.com/livingdocsIO/livingdocs-server/pull/3010) :gift:






SERVER (until 103.3.2)
-----------------------------------------------------------

* v103.3.1 Correctly support sorting on the document title [livingdocs-server #3078](https://github.com/livingdocsIO/livingdocs-server/pull/3078) :gift:

* v103.2.3 add origin from headers to local authentication api [livingdocs-server #3056](https://github.com/livingdocsIO/livingdocs-server/pull/3056) :gift:
* v103.1.0 Document version check [livingdocs-server #3067](https://github.com/livingdocsIO/livingdocs-server/pull/3067) :gift:
* v103.0.3 Properly inject normalized configurations down into the document save transaction [livingdocs-server #3066](https://github.com/livingdocsIO/livingdocs-server/pull/3066) :gift:
* v103.0.2 fix(channel-configs): use strictObj validation for properties [livingdocs-server #3041](https://github.com/livingdocsIO/livingdocs-server/pull/3041) :gift:
* v103.0.1 Keep EXIF metadata in images processed by libvips [livingdocs-server #3065](https://github.com/livingdocsIO/livingdocs-server/pull/3065) :gift:
* v103.0.0 Switch from imagemagick to libvips for the image processing [livingdocs-server #3063](https://github.com/livingdocsIO/livingdocs-server/pull/3063) :gift:
* v102.5.1 Database query refactorings [livingdocs-server #3062](https://github.com/livingdocsIO/livingdocs-server/pull/3062) :gift:

* v102.4.1 Index language with custom handle [livingdocs-server #3060](https://github.com/livingdocsIO/livingdocs-server/pull/3060) :gift:
* v102.4.0 (exif extraction): remove recoding code [livingdocs-server #3054](https://github.com/livingdocsIO/livingdocs-server/pull/3054) :gift:
* v102.3.2 fix(exif extraction): rename the dest property to metadataPropertyName in the extraction config [livingdocs-server #3053](https://github.com/livingdocsIO/livingdocs-server/pull/3053) :gift:
* v102.3.2 add origin from headers to local authentication api [livingdocs-server #3056](https://github.com/livingdocsIO/livingdocs-server/pull/3056) :gift:

* v102.2.7 fix dashboard schema [livingdocs-server #3050](https://github.com/livingdocsIO/livingdocs-server/pull/3050) :gift:
* v102.2.6 Fix dashboard schema [livingdocs-server #3042](https://github.com/livingdocsIO/livingdocs-server/pull/3042) :gift:
* v102.2.5 fix(editorSettings): allow dashboard componentOptions to be any object [livingdocs-server #3049](https://github.com/livingdocsIO/livingdocs-server/pull/3049) :gift:
* v102.2.4 Upgrade ioredis [livingdocs-server #3046](https://github.com/livingdocsIO/livingdocs-server/pull/3046) :gift:
* v102.2.3 Project seeding fixes [livingdocs-server #3044](https://github.com/livingdocsIO/livingdocs-server/pull/3044) :gift:
* v102.2.2 Fix editor settings schema validation [livingdocs-server #3040](https://github.com/livingdocsIO/livingdocs-server/pull/3040) :gift:
* v102.1.1 Await requests in import api [livingdocs-server #3038](https://github.com/livingdocsIO/livingdocs-server/pull/3038) :gift:
* v101.4.1 add user to new login device data object [livingdocs-server #3025](https://github.com/livingdocsIO/livingdocs-server/pull/3025) :gift:
* v101.4.0 feat(images): expose storage publicUrl to the editor [livingdocs-server #3028](https://github.com/livingdocsIO/livingdocs-server/pull/3028) :gift:


* v101.1.9 fix: improve error message for stale memory cache [livingdocs-server #2953](https://github.com/livingdocsIO/livingdocs-server/pull/2953) :gift:
* v101.1.8 fix: example project should be able to copy [livingdocs-server #3019](https://github.com/livingdocsIO/livingdocs-server/pull/3019) :gift:
* v101.1.6 Do not crash the document copy feature when the framework complaints about errors [livingdocs-server #3023](https://github.com/livingdocsIO/livingdocs-server/pull/3023) :gift:
* v101.1.3 sort import jobs by started_at date [livingdocs-server #3016](https://github.com/livingdocsIO/livingdocs-server/pull/3016) :gift:
* v101.1.2 Fix database down migrations [livingdocs-server #3015](https://github.com/livingdocsIO/livingdocs-server/pull/3015) :gift:

* v101.0.2 Migrate `publicationApi.renderSelectedRenditions` to async/await [livingdocs-server #3011](https://github.com/livingdocsIO/livingdocs-server/pull/3011) :gift:


* v100.3.1 fix: design_stats_routes are working again [livingdocs-server #3005](https://github.com/livingdocsIO/livingdocs-server/pull/3005) :gift:
* v100.2.1 Fix json schemas and remove custom extends logic [livingdocs-server #3003](https://github.com/livingdocsIO/livingdocs-server/pull/3003) :gift:

* v100.1.0 Async support in the public api [livingdocs-server #3000](https://github.com/livingdocsIO/livingdocs-server/pull/3000) :gift:
* v100.0.0 Support content types that didn't declare a metadata array [livingdocs-server #2997](https://github.com/livingdocsIO/livingdocs-server/pull/2997) :gift:
* v98.0.3 Use channel config api instead of channel api [livingdocs-server #2990](https://github.com/livingdocsIO/livingdocs-server/pull/2990) :gift:
* v98.0.2 fix(google-vision): disable in tests [livingdocs-server #2978](https://github.com/livingdocsIO/livingdocs-server/pull/2978) :gift:
* v98.0.0 Upgrade the elasticsearch client [livingdocs-server #2963](https://github.com/livingdocsIO/livingdocs-server/pull/2963) :gift:
* v97.1.2 fix: update framework and unskip tests [livingdocs-server #2973](https://github.com/livingdocsIO/livingdocs-server/pull/2973) :gift:
* v97.1.0 Upgrade the dashboards to retrieve the list of queues automatically from redis [livingdocs-server #2979](https://github.com/livingdocsIO/livingdocs-server/pull/2979) :gift:
* v96.3.3 fix: only push errors if metadata is missing [livingdocs-server #2960](https://github.com/livingdocsIO/livingdocs-server/pull/2960) :gift:
* v96.3.1 fix: add getRoutePart for core li-language plugin [livingdocs-server #2954](https://github.com/livingdocsIO/livingdocs-server/pull/2954) :gift:
* v96.2.1 fix: expose pusherApi.pusherClient again [livingdocs-server #2957](https://github.com/livingdocsIO/livingdocs-server/pull/2957) :gift:
* v96.1.1 Document References: Detect an image directive based on the mediaId [livingdocs-server #2948](https://github.com/livingdocsIO/livingdocs-server/pull/2948) :gift:
* v96.0.4 Device Detection History [livingdocs-server #2949](https://github.com/livingdocsIO/livingdocs-server/pull/2949) :gift:
* v96.0.2 Copy config: make channelHandle optional [livingdocs-server #2930](https://github.com/livingdocsIO/livingdocs-server/pull/2930) :gift:
* v94.13.2 fix(deprecation): Use new channelApi.getChannel() [livingdocs-server #2720](https://github.com/livingdocsIO/livingdocs-server/pull/2720) :gift:


  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
