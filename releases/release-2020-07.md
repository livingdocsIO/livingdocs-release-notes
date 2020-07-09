
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

## EXAMPLE !!!!!!!!!!!!!!!!!!! Editor Multiselect :gift:
Add multiselect functionality to the editor. In multiselect mode when a component is clicked this component is added to the selection. When a component is clicked again it is removed from the selection. In the sidebar the count of selected components is shown and there is the option to delete all selected components.
Required editor configuration to enable the multiselect feature:
```js
keyboardShortcuts: {
      '↓shift': 'start multiselect mode',
      '↑shift': 'end multiselect mode'
}
```

You can read more about the feature in the references section.

* References
  * [editor PR #2143](https://github.com/livingdocsIO/livingdocs-editor/pull/2143)
  * [documentation](https://github.com/livingdocsIO/livingdocs/pull/246)


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

# Internal Changes

# Other Changes

### Features

* ... :gift:

### Design

* ... :gift:

### Improvements

* ... :gift:

### Bugfixes

* ... :beetle:






EDITOR (until 56.6.0)
-----------------------------------------------------------
* v56.6.0 (Media Library) Extract metadata when form for required metadata properties is shown [livingdocs-editor #3690](https://github.com/livingdocsIO/livingdocs-editor/pull/3690) :gift:
* v56.5.0 vue-form-generator: support date picker [livingdocs-editor #3671](https://github.com/livingdocsIO/livingdocs-editor/pull/3671) :gift:
* v56.4.0 Support "media library -> document" drag and drop [livingdocs-editor #3640](https://github.com/livingdocsIO/livingdocs-editor/pull/3640) :gift:
* v56.3.0 Media library validity support [livingdocs-editor #3688](https://github.com/livingdocsIO/livingdocs-editor/pull/3688) :gift:
* v56.2.0 Create MediaLibrary Config based on Project Config [livingdocs-editor #3691](https://github.com/livingdocsIO/livingdocs-editor/pull/3691) :gift:
* v56.1.0 Adapt Media Library Search to the new API [livingdocs-editor #3689](https://github.com/livingdocsIO/livingdocs-editor/pull/3689) :gift:
* v56.0.0 Ability to configure entry point dashboard [livingdocs-editor #3687](https://github.com/livingdocsIO/livingdocs-editor/pull/3687) :gift:
* v55.0.2 Fix Language Selection Service [livingdocs-editor #3685](https://github.com/livingdocsIO/livingdocs-editor/pull/3685) :gift:
* v55.0.1 fix(asset proxy) add asset.url to MediaLibraryEntry in resolve value to assetProxy.postImage for compatibility reasons [livingdocs-editor #3686](https://github.com/livingdocsIO/livingdocs-editor/pull/3686) :gift:
* v55.0.0 (MediaLibrary): Introduce and use MediaLibraryEntry model [livingdocs-editor #3680](https://github.com/livingdocsIO/livingdocs-editor/pull/3680) :gift:
* v54.2.4 Set default language depending on existing of li-language type plugin [livingdocs-editor #3682](https://github.com/livingdocsIO/livingdocs-editor/pull/3682) :gift:
* v54.2.3 fix(imatrics): improve error handling [livingdocs-editor #3681](https://github.com/livingdocsIO/livingdocs-editor/pull/3681) :gift:
* v54.2.2 fix: small fixes for the required metadata modal [livingdocs-editor #3678](https://github.com/livingdocsIO/livingdocs-editor/pull/3678) :gift:
* v54.2.1 deleted article message should be red with white color [livingdocs-editor #3675](https://github.com/livingdocsIO/livingdocs-editor/pull/3675) :gift:
* v54.2.0 (Media Library) Image Upload Service / Metadata Form Validations [livingdocs-editor #3661](https://github.com/livingdocsIO/livingdocs-editor/pull/3661) :gift:
* v54.1.0 feat(imatrics): add event and object entity types [livingdocs-editor #3629](https://github.com/livingdocsIO/livingdocs-editor/pull/3629) :gift:
* v54.0.0 feat: media library UI can now be turned off [livingdocs-editor #3667](https://github.com/livingdocsIO/livingdocs-editor/pull/3667) :gift:
* v53.6.0 Introduce default Proofreading and Media Library Navigation Menu [livingdocs-editor #3666](https://github.com/livingdocsIO/livingdocs-editor/pull/3666) :gift:
* v53.5.3 only activate the insert toolbar action on the canvas route [livingdocs-editor #3668](https://github.com/livingdocsIO/livingdocs-editor/pull/3668) :gift:
* v53.5.2 add comment and cancel btn to comment card [livingdocs-editor #3664](https://github.com/livingdocsIO/livingdocs-editor/pull/3664) :gift:
* v53.5.1 show insert in format panel and register empty click for it [livingdocs-editor #3637](https://github.com/livingdocsIO/livingdocs-editor/pull/3637) :gift:
* v53.5.0 Dashboard: Vueify MediaLibraryCard [livingdocs-editor #3628](https://github.com/livingdocsIO/livingdocs-editor/pull/3628) :gift:
* v53.4.11 Use type `li-language` in translations instead of handle `language` [livingdocs-editor #3656](https://github.com/livingdocsIO/livingdocs-editor/pull/3656) :gift:
* v53.4.10 Fix live update of a kanban board card [livingdocs-editor #3659](https://github.com/livingdocsIO/livingdocs-editor/pull/3659) :gift:
* v53.4.9 Bug fixes for the nzz [livingdocs-editor #3644](https://github.com/livingdocsIO/livingdocs-editor/pull/3644) :gift:
* v53.4.8 fix(navigation): allow enough listeners on the navigation emitter provided to vue components [livingdocs-editor #3655](https://github.com/livingdocsIO/livingdocs-editor/pull/3655) :gift:
* v53.4.7 fix recover on conflicts with metadata changes on server [livingdocs-editor #3642](https://github.com/livingdocsIO/livingdocs-editor/pull/3642) :gift:
* v53.4.6 use li-language instead of handle to identify metadata plugin [livingdocs-editor #3647](https://github.com/livingdocsIO/livingdocs-editor/pull/3647) :gift:
* v53.4.5 fix(deliveryLinks): recompile delivery links when publish state changes [livingdocs-editor #3645](https://github.com/livingdocsIO/livingdocs-editor/pull/3645) :gift:
* v53.4.4 fix: move language groupId copy config to the server [livingdocs-editor #3643](https://github.com/livingdocsIO/livingdocs-editor/pull/3643) :gift:
* v53.4.3 Add vue and @livingdocs/framework aliases to webpack [livingdocs-editor #3639](https://github.com/livingdocsIO/livingdocs-editor/pull/3639) :gift:
* v53.4.2 fix: no js errors for li-document-copy&reference [livingdocs-editor #3641](https://github.com/livingdocsIO/livingdocs-editor/pull/3641) :gift:
* v53.4.1 Cypress logs [livingdocs-editor #3594](https://github.com/livingdocsIO/livingdocs-editor/pull/3594) :gift:
* v53.4.0 Render required metadata form with form generator [livingdocs-editor #3636](https://github.com/livingdocsIO/livingdocs-editor/pull/3636) :gift:
* v53.3.1 Fix import jobs dashboard [livingdocs-editor #3635](https://github.com/livingdocsIO/livingdocs-editor/pull/3635) :gift:
* v53.3.0 Feat: Custom user menu configuration [livingdocs-editor #3603](https://github.com/livingdocsIO/livingdocs-editor/pull/3603) :gift:
* v53.2.1 Refactoring: migrate li-create-document-button from angular to vue [livingdocs-editor #3609](https://github.com/livingdocsIO/livingdocs-editor/pull/3609) :gift:
* v53.2.0 Embed custom media library dashboard into editor sidebar [livingdocs-editor #3604](https://github.com/livingdocsIO/livingdocs-editor/pull/3604) :gift:
* v53.1.1 Fix multiline comment support [livingdocs-editor #3633](https://github.com/livingdocsIO/livingdocs-editor/pull/3633) :gift:
* v53.1.0 Fix: (vueified) document copy&embeds relation cards now correctly show as published [livingdocs-editor #3614](https://github.com/livingdocsIO/livingdocs-editor/pull/3614) :gift:
* v53.0.0 Migrate /documents?q=Text to /documents?search=Text [livingdocs-editor #3630](https://github.com/livingdocsIO/livingdocs-editor/pull/3630) :gift:
* v52.7.2 chore: disable downstream tests to proceed with release [livingdocs-editor #3684](https://github.com/livingdocsIO/livingdocs-editor/pull/3684) :gift:
* v52.7.1 fix: move language groupId copy config to the server [release-blz-2020-06]  [livingdocs-editor #3648](https://github.com/livingdocsIO/livingdocs-editor/pull/3648) :gift:
* v52.7.0 (Media Library) use mediaTypes for metadata configuration [livingdocs-editor #3613](https://github.com/livingdocsIO/livingdocs-editor/pull/3613) :gift:
* v52.6.6 fix: do not register the same component twice [livingdocs-editor #3631](https://github.com/livingdocsIO/livingdocs-editor/pull/3631) :gift:
* v52.6.5 Fix conflict with self [livingdocs-editor #3605](https://github.com/livingdocsIO/livingdocs-editor/pull/3605) :gift:
* v52.6.4 fix: bump some dependencies [livingdocs-editor #3425](https://github.com/livingdocsIO/livingdocs-editor/pull/3425) :gift:
* v52.6.3 fix(webpack): fix style alias to work in downstreams [livingdocs-editor #3621](https://github.com/livingdocsIO/livingdocs-editor/pull/3621) :gift:
* v52.6.2 chore(main nav): use CustomEvent instead of Event [livingdocs-editor #3617](https://github.com/livingdocsIO/livingdocs-editor/pull/3617) :gift:
* v52.6.1 fix: improve visiblity of urgent proofreading tasks and deadlines [livingdocs-editor #3618](https://github.com/livingdocsIO/livingdocs-editor/pull/3618) :gift:
* v52.6.0 Import log viewer [livingdocs-editor #3616](https://github.com/livingdocsIO/livingdocs-editor/pull/3616) :gift:
* v52.5.0 Feat: revamp livingdocs notifications  [livingdocs-editor #3533](https://github.com/livingdocsIO/livingdocs-editor/pull/3533) :gift:
* v52.4.0 fix: hide button that is not used [livingdocs-editor #3611](https://github.com/livingdocsIO/livingdocs-editor/pull/3611) :gift:
* v52.3.1 Refactoring: Vueify liDashboardTitle [livingdocs-editor #3607](https://github.com/livingdocsIO/livingdocs-editor/pull/3607) :gift:
* v52.3.0 Refactor image uploading workflow, introduce a imageUploadService [livingdocs-editor #3430](https://github.com/livingdocsIO/livingdocs-editor/pull/3430) :gift:
* v52.2.1 fix(imatrics): do not log errors from li-taglist on publish screen [livingdocs-editor #3608](https://github.com/livingdocsIO/livingdocs-editor/pull/3608) :gift:
* v52.2.0 MediaLibrary as Custom Dashboard - Iteration 1 [livingdocs-editor #3562](https://github.com/livingdocsIO/livingdocs-editor/pull/3562) :gift:
* v52.1.0 Tags / iMatrics [livingdocs-editor #3593](https://github.com/livingdocsIO/livingdocs-editor/pull/3593) :gift:
* v52.0.4 Fix: support previewUrl for custom document previews [livingdocs-editor #3585](https://github.com/livingdocsIO/livingdocs-editor/pull/3585) :gift:
* v52.0.3 fix: allow iFrame modals to download content [livingdocs-editor #3590](https://github.com/livingdocsIO/livingdocs-editor/pull/3590) :gift:
* v52.0.2 fix(main nav): recalculate isActive state after navigation success [livingdocs-editor #3597](https://github.com/livingdocsIO/livingdocs-editor/pull/3597) :gift:
* v52.0.1 fix(locale): fix default moment locale to 'en-li' [livingdocs-editor #3595](https://github.com/livingdocsIO/livingdocs-editor/pull/3595) :gift:
* v52.0.0 Allow custom components in MainMenu [livingdocs-editor #3584](https://github.com/livingdocsIO/livingdocs-editor/pull/3584) :gift:
* v51.12.6 Only blur component if focused on component lock [livingdocs-editor #3586](https://github.com/livingdocsIO/livingdocs-editor/pull/3586) :gift:
* v51.12.5 fix: add uploadImage function to iFrameview [livingdocs-editor #3582](https://github.com/livingdocsIO/livingdocs-editor/pull/3582) :gift:
* v51.12.4 Fix Include Modal [livingdocs-editor #3577](https://github.com/livingdocsIO/livingdocs-editor/pull/3577) :gift:
* v51.12.3 Adapt live coverage ui [livingdocs-editor #3572](https://github.com/livingdocsIO/livingdocs-editor/pull/3572) :gift:
* v51.12.2 fix: correctly set label for uploaded files [livingdocs-editor #3565](https://github.com/livingdocsIO/livingdocs-editor/pull/3565) :gift:
* v51.12.1 Fix modal and ios navi [livingdocs-editor #3567](https://github.com/livingdocsIO/livingdocs-editor/pull/3567) :gift:
* v51.12.0 Configure Google Vision as integration [livingdocs-editor #3555](https://github.com/livingdocsIO/livingdocs-editor/pull/3555) :gift:
* v51.11.2 fix: only show a task card title once [livingdocs-editor #3557](https://github.com/livingdocsIO/livingdocs-editor/pull/3557) :gift:
* v51.11.1 Fix magnify icons in print layout selector [livingdocs-editor #3559](https://github.com/livingdocsIO/livingdocs-editor/pull/3559) :gift:
* v51.11.0 Vue multi select + vueify project settings screen [livingdocs-editor #3515](https://github.com/livingdocsIO/livingdocs-editor/pull/3515) :gift:
* v51.10.1 Support Query State Params on Login [livingdocs-editor #3550](https://github.com/livingdocsIO/livingdocs-editor/pull/3550) :gift:
* v51.10.0 Curl Examples for Public API [livingdocs-editor #3549](https://github.com/livingdocsIO/livingdocs-editor/pull/3549) :gift:
* v51.9.1 fix(icons): load li-icon styles in iframe to render editable toolbar correctly [livingdocs-editor #3548](https://github.com/livingdocsIO/livingdocs-editor/pull/3548) :gift:
* v51.9.0 feat(schema-form): add li-boolean type form [livingdocs-editor #3526](https://github.com/livingdocsIO/livingdocs-editor/pull/3526) :gift:
* v51.8.1 Improve Comyan Drag+Drop Error Handling [livingdocs-editor #3545](https://github.com/livingdocsIO/livingdocs-editor/pull/3545) :gift:
* v51.8.0 feat: enforce image metadata during bulk upload [livingdocs-editor #3544](https://github.com/livingdocsIO/livingdocs-editor/pull/3544) :gift:
* v51.7.0 Editor: Configurable List Search Config [livingdocs-editor #3537](https://github.com/livingdocsIO/livingdocs-editor/pull/3537) :gift:
* v51.6.6 Allow to exclude whole components from text-counter [livingdocs-editor #3329](https://github.com/livingdocsIO/livingdocs-editor/pull/3329) :gift:
* v51.6.5 fix: sanitize html for the li-json-viewer [livingdocs-editor #3542](https://github.com/livingdocsIO/livingdocs-editor/pull/3542) :gift:
* v51.6.4 Fix close on include modal and remove lock on idle [livingdocs-editor #3530](https://github.com/livingdocsIO/livingdocs-editor/pull/3530) :gift:
* v51.6.3 fix: edge support >=18 again [livingdocs-editor #3536](https://github.com/livingdocsIO/livingdocs-editor/pull/3536) :gift:
* v51.6.2 Support vue mixin props in the angular vue wrapper [livingdocs-editor #3511](https://github.com/livingdocsIO/livingdocs-editor/pull/3511) :gift:
* v51.6.1 fix: upgrade cypress [livingdocs-editor #3534](https://github.com/livingdocsIO/livingdocs-editor/pull/3534) :gift:
* v51.6.0 Allow to restore a channel-config [livingdocs-editor #3475](https://github.com/livingdocsIO/livingdocs-editor/pull/3475) :gift:
* v51.5.0 Show multiple validation errors on the publish screen [livingdocs-editor #3513](https://github.com/livingdocsIO/livingdocs-editor/pull/3513) :gift:
* v51.4.2 fix(language): show/hide li-language metadata form based on a behavior [livingdocs-editor #3527](https://github.com/livingdocsIO/livingdocs-editor/pull/3527) :gift:
* v51.4.1 Comyan Drag + Drop Fix  to not throw on storageBaseUrl computation [livingdocs-editor #3523](https://github.com/livingdocsIO/livingdocs-editor/pull/3523) :gift:
* v51.4.0 feat(metadata form): show an error message on error during property form rendering [livingdocs-editor #3519](https://github.com/livingdocsIO/livingdocs-editor/pull/3519) :gift:
* v51.3.0 feat(webhooks): validate form and show error messages [livingdocs-editor #3507](https://github.com/livingdocsIO/livingdocs-editor/pull/3507) :gift:
* v51.2.4 Refactor component locks and add them also for proposals [livingdocs-editor #3517](https://github.com/livingdocsIO/livingdocs-editor/pull/3517) :gift:
* v51.2.3 Bug: Correctly set the Image Directive on Comyan Drag + Drop [livingdocs-editor #3518](https://github.com/livingdocsIO/livingdocs-editor/pull/3518) :gift:
* v51.2.3 Refactor component locks and add them also for proposals [livingdocs-editor #3517](https://github.com/livingdocsIO/livingdocs-editor/pull/3517) :gift:
* v51.2.2 fix(comyan): allow config and use additionalApiQueryString to sent request to comyan API [livingdocs-editor #3514](https://github.com/livingdocsIO/livingdocs-editor/pull/3514) :gift:
* v51.2.1 fix component locks and history overlays [livingdocs-editor #3509](https://github.com/livingdocsIO/livingdocs-editor/pull/3509) :gift:
* v51.2.0 Manage component groups [livingdocs-editor #3441](https://github.com/livingdocsIO/livingdocs-editor/pull/3441) :gift:
* v51.1.0 Vue styleguide [livingdocs-editor #3500](https://github.com/livingdocsIO/livingdocs-editor/pull/3500) :gift:
* v51.0.1 Remove unsupported icons from icon list [livingdocs-editor #3506](https://github.com/livingdocsIO/livingdocs-editor/pull/3506) :gift:
* v51.0.0 Add node 14, drop node 10 support [livingdocs-editor #3505](https://github.com/livingdocsIO/livingdocs-editor/pull/3505) :gift:
* v50.4.4 fix(includeServices): adds includeServices to project channel [livingdocs-editor #3502](https://github.com/livingdocsIO/livingdocs-editor/pull/3502) :gift:
* v50.4.3 font resolve in the downstreams doesn't work [livingdocs-editor #3501](https://github.com/livingdocsIO/livingdocs-editor/pull/3501) :gift:
* v50.4.2 Fix insert proposal [livingdocs-editor #3491](https://github.com/livingdocsIO/livingdocs-editor/pull/3491) :gift:
* v50.4.1 Fix icons [livingdocs-editor #3493](https://github.com/livingdocsIO/livingdocs-editor/pull/3493) :gift:
* v50.4.0 li-icon [livingdocs-editor #3492](https://github.com/livingdocsIO/livingdocs-editor/pull/3492) :gift:
* v50.3.4 fix(comyan): replace existing image if dropped on existing image component [livingdocs-editor #3486](https://github.com/livingdocsIO/livingdocs-editor/pull/3486) :gift:
* v50.3.3 Comyan: fixes [livingdocs-editor #3484](https://github.com/livingdocsIO/livingdocs-editor/pull/3484) :gift:
* v50.3.2 Notification and Loading Button Quickfixes [livingdocs-editor #3480](https://github.com/livingdocsIO/livingdocs-editor/pull/3480) :gift:




SERVER (until 102.2.6)
-----------------------------------------------------------
* v102.2.6 Fix dashboard schema [livingdocs-server #3042](https://github.com/livingdocsIO/livingdocs-server/pull/3042) :gift:
* v102.2.5 fix(editorSettings): allow dashboard componentOptions to be any object [livingdocs-server #3049](https://github.com/livingdocsIO/livingdocs-server/pull/3049) :gift:
* v102.2.4 Upgrade ioredis [livingdocs-server #3046](https://github.com/livingdocsIO/livingdocs-server/pull/3046) :gift:
* v102.2.3 Project seeding fixes [livingdocs-server #3044](https://github.com/livingdocsIO/livingdocs-server/pull/3044) :gift:
* v102.2.2 Fix editor settings schema validation [livingdocs-server #3040](https://github.com/livingdocsIO/livingdocs-server/pull/3040) :gift:
* v102.2.1 fix(e2e): fix mediaType configuration [livingdocs-server #3039](https://github.com/livingdocsIO/livingdocs-server/pull/3039) :gift:
* v102.2.0 (Media Library) metadata extraction [livingdocs-server #3035](https://github.com/livingdocsIO/livingdocs-server/pull/3035) :gift:
* v102.1.1 Await requests in import api [livingdocs-server #3038](https://github.com/livingdocsIO/livingdocs-server/pull/3038) :gift:
* v102.1.0 feat: add li-date-range plugin [livingdocs-server #3032](https://github.com/livingdocsIO/livingdocs-server/pull/3032) :gift:
* v102.0.0 Media Library [livingdocs-server #3030](https://github.com/livingdocsIO/livingdocs-server/pull/3030) :gift:
* v101.4.4 Allow startPage configuration in editor settings [livingdocs-server #3031](https://github.com/livingdocsIO/livingdocs-server/pull/3031) :gift:
* v101.4.3 fix(imatrics): Allow value `0` for minchars [livingdocs-server #3033](https://github.com/livingdocsIO/livingdocs-server/pull/3033) :gift:
* v101.4.2 fix(imatrics): improve IMatricsTextTooShortError error case [livingdocs-server #3029](https://github.com/livingdocsIO/livingdocs-server/pull/3029) :gift:
* v101.4.1 add user to new login device data object [livingdocs-server #3025](https://github.com/livingdocsIO/livingdocs-server/pull/3025) :gift:
* v101.4.0 feat(images): expose storage publicUrl to the editor [livingdocs-server #3028](https://github.com/livingdocsIO/livingdocs-server/pull/3028) :gift:
* v101.3.0 New projectConfig.editorSettings properties (mainNavigation, dashboards) [livingdocs-server #3024](https://github.com/livingdocsIO/livingdocs-server/pull/3024) :gift:
* v101.2.0 feat: add projectConfig.editorSettings.mediaLibrary.enabled [livingdocs-server #3027](https://github.com/livingdocsIO/livingdocs-server/pull/3027) :gift:
* v101.1.9 fix: improve error message for stale memory cache [livingdocs-server #2953](https://github.com/livingdocsIO/livingdocs-server/pull/2953) :gift:
* v101.1.8 fix: example project should be able to copy [livingdocs-server #3019](https://github.com/livingdocsIO/livingdocs-server/pull/3019) :gift:
* v101.1.7 consider swisscom custom language handle in references [livingdocs-server #3022](https://github.com/livingdocsIO/livingdocs-server/pull/3022) :gift:
* v101.1.6 Do not crash the document copy feature when the framework complaints about errors [livingdocs-server #3023](https://github.com/livingdocsIO/livingdocs-server/pull/3023) :gift:
* v101.1.5 fix: move language groupId copy config to the server [livingdocs-server #3020](https://github.com/livingdocsIO/livingdocs-server/pull/3020) :gift:
* v101.1.4 fix(imatrics): make imatrics tag schema more flexibel by allowing additional properties [livingdocs-server #3017](https://github.com/livingdocsIO/livingdocs-server/pull/3017) :gift:
* v101.1.3 sort import jobs by started_at date [livingdocs-server #3016](https://github.com/livingdocsIO/livingdocs-server/pull/3016) :gift:
* v101.1.2 Fix database down migrations [livingdocs-server #3015](https://github.com/livingdocsIO/livingdocs-server/pull/3015) :gift:
* v101.1.1 Cypress logs [livingdocs-server #3014](https://github.com/livingdocsIO/livingdocs-server/pull/3014) :gift:
* v101.1.0 Feat: Custom user menu configuration [livingdocs-server #2996](https://github.com/livingdocsIO/livingdocs-server/pull/2996) :gift:
* v101.0.2 Migrate `publicationApi.renderSelectedRenditions` to async/await [livingdocs-server #3011](https://github.com/livingdocsIO/livingdocs-server/pull/3011) :gift:
* v101.0.1 Fix cypress login tests [livingdocs-server #3010](https://github.com/livingdocsIO/livingdocs-server/pull/3010) :gift:
* v101.0.0 Migrate /documents?q=Text to /documents?search=Text [livingdocs-server #3004](https://github.com/livingdocsIO/livingdocs-server/pull/3004) :gift:
* v100.3.2 fix: move language groupId copy config to the server [release-blz-2020-06]  [livingdocs-server #3021](https://github.com/livingdocsIO/livingdocs-server/pull/3021) :gift:
* v100.3.1 fix: design_stats_routes are working again [livingdocs-server #3005](https://github.com/livingdocsIO/livingdocs-server/pull/3005) :gift:
* v100.3.0 Project Config: MediaTypes [livingdocs-server #3001](https://github.com/livingdocsIO/livingdocs-server/pull/3001) :gift:
* v100.2.1 Fix json schemas and remove custom extends logic [livingdocs-server #3003](https://github.com/livingdocsIO/livingdocs-server/pull/3003) :gift:
* v100.2.0 Import log viewer [livingdocs-server #3002](https://github.com/livingdocsIO/livingdocs-server/pull/3002) :gift:
* v100.1.0 Async support in the public api [livingdocs-server #3000](https://github.com/livingdocsIO/livingdocs-server/pull/3000) :gift:
* v100.0.0 Support content types that didn't declare a metadata array [livingdocs-server #2997](https://github.com/livingdocsIO/livingdocs-server/pull/2997) :gift:
* v99.0.0 Rename li-asset-management to li-media-library [livingdocs-server #2993](https://github.com/livingdocsIO/livingdocs-server/pull/2993) :gift:
* v98.0.3 Use channel config api instead of channel api [livingdocs-server #2990](https://github.com/livingdocsIO/livingdocs-server/pull/2990) :gift:
* v98.0.2 fix(google-vision): disable in tests [livingdocs-server #2978](https://github.com/livingdocsIO/livingdocs-server/pull/2978) :gift:
* v98.0.1 feat: previewApi supports a previewUrl now [livingdocs-server #2986](https://github.com/livingdocsIO/livingdocs-server/pull/2986) :gift:
* v98.0.0 Upgrade the elasticsearch client [livingdocs-server #2963](https://github.com/livingdocsIO/livingdocs-server/pull/2963) :gift:
* v97.1.2 fix: update framework and unskip tests [livingdocs-server #2973](https://github.com/livingdocsIO/livingdocs-server/pull/2973) :gift:
* v97.1.0 Upgrade the dashboards to retrieve the list of queues automatically from redis [livingdocs-server #2979](https://github.com/livingdocsIO/livingdocs-server/pull/2979) :gift:
* v97.0.1 fix: correctly upload files [livingdocs-server #2970](https://github.com/livingdocsIO/livingdocs-server/pull/2970) :gift:
* v97.0.0 Move google vision config [livingdocs-server #2969](https://github.com/livingdocsIO/livingdocs-server/pull/2969) :gift:
* v96.3.3 fix: only push errors if metadata is missing [livingdocs-server #2960](https://github.com/livingdocsIO/livingdocs-server/pull/2960) :gift:
* v96.3.2 Fix media re-indexing [livingdocs-server #2968](https://github.com/livingdocsIO/livingdocs-server/pull/2968) :gift:
* v96.3.1 fix: add getRoutePart for core li-language plugin [livingdocs-server #2954](https://github.com/livingdocsIO/livingdocs-server/pull/2954) :gift:
* v96.3.0 feat(include services): allow li-boolean type in paramsSchema [livingdocs-server #2950](https://github.com/livingdocsIO/livingdocs-server/pull/2950) :gift:
* v96.2.3 Server: Configurable List Search Config [livingdocs-server #2959](https://github.com/livingdocsIO/livingdocs-server/pull/2959) :gift:
* v96.2.2 fix(channel-configs): add excludeFromTextCount to components json schema [livingdocs-server #2961](https://github.com/livingdocsIO/livingdocs-server/pull/2961) :gift:
* v96.2.1 fix: expose pusherApi.pusherClient again [livingdocs-server #2957](https://github.com/livingdocsIO/livingdocs-server/pull/2957) :gift:
* v96.2.0 Add compare channel-config route [livingdocs-server #2952](https://github.com/livingdocsIO/livingdocs-server/pull/2952) :gift:
* v96.1.1 Document References: Detect an image directive based on the mediaId [livingdocs-server #2948](https://github.com/livingdocsIO/livingdocs-server/pull/2948) :gift:
* v96.1.0 Handle multiple metadata validation errors at once. [livingdocs-server #2943](https://github.com/livingdocsIO/livingdocs-server/pull/2943) :gift:
* v96.0.4 Device Detection History [livingdocs-server #2949](https://github.com/livingdocsIO/livingdocs-server/pull/2949) :gift:
* v96.0.3 fix(comyan): allow additionalApiQueryString config [livingdocs-server #2945](https://github.com/livingdocsIO/livingdocs-server/pull/2945) :gift:
* v96.0.2 Copy config: make channelHandle optional [livingdocs-server #2930](https://github.com/livingdocsIO/livingdocs-server/pull/2930) :gift:
* v96.0.1 Manage component groups [livingdocs-server #2926](https://github.com/livingdocsIO/livingdocs-server/pull/2926) :gift:
* v94.13.2 fix(deprecation): Use new channelApi.getChannel() [livingdocs-server #2720](https://github.com/livingdocsIO/livingdocs-server/pull/2720) :gift:


  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
