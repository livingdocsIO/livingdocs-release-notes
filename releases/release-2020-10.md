
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


--------------SERVER----------------------
* v104.2.0 Bump minor version for release management [livingdocs-server #3174](https://github.com/livingdocsIO/livingdocs-server/pull/3174) :gift:
* v104.1.0 Improve reindex tasks [livingdocs-server #3162](https://github.com/livingdocsIO/livingdocs-server/pull/3162) :gift:
* v104.0.0 fix(dependencies): update framework 15.1.0 -> 16.0.1 [livingdocs-server #3144](https://github.com/livingdocsIO/livingdocs-server/pull/3144) :gift:
* v103.12.1 fix(print): Add `/editions` endpoint [livingdocs-server #3160](https://github.com/livingdocsIO/livingdocs-server/pull/3160) :gift:
* v103.12.0 New CLI task: livingdocs-server data-migration-run [livingdocs-server #3151](https://github.com/livingdocsIO/livingdocs-server/pull/3151) :gift:
* v103.11.1 Add redis debug logs and automatically reconnect against primary [livingdocs-server #3156](https://github.com/livingdocsIO/livingdocs-server/pull/3156) :gift:
* v103.11.0 Data Migration:  Report not applied documents [livingdocs-server #3148](https://github.com/livingdocsIO/livingdocs-server/pull/3148) :gift:
* v103.10.0 Support a client-defined document id in the import api [livingdocs-server #3145](https://github.com/livingdocsIO/livingdocs-server/pull/3145) :gift:
* v103.9.2 fix(imatrics): store slug on user added concepts [livingdocs-server #3146](https://github.com/livingdocsIO/livingdocs-server/pull/3146) :gift:
* v103.9.1 fix(imatrics): Register feature API [livingdocs-server #3141](https://github.com/livingdocsIO/livingdocs-server/pull/3141) :gift:
* v103.9.0 feat(index): index the teaserImage in example server [livingdocs-server #3140](https://github.com/livingdocsIO/livingdocs-server/pull/3140) :gift:
* v103.8.7 Expose public api internally [livingdocs-server #3138](https://github.com/livingdocsIO/livingdocs-server/pull/3138) :gift:
* v103.8.6 Fix image uploads for PDF's when using imagemagick [livingdocs-server #3134](https://github.com/livingdocsIO/livingdocs-server/pull/3134) :gift:
* v103.8.5 Fix media library entry title for existing entries [livingdocs-server #3135](https://github.com/livingdocsIO/livingdocs-server/pull/3135) :gift:
* v103.8.4 fix: add example config [livingdocs-server #3106](https://github.com/livingdocsIO/livingdocs-server/pull/3106) :gift:
* v103.8.3 Use s3 url for woodwing assets [livingdocs-server #3132](https://github.com/livingdocsIO/livingdocs-server/pull/3132) :gift:
* v103.8.2 fix(print-api): Make royaltyRecipient host configurable [livingdocs-server #3130](https://github.com/livingdocsIO/livingdocs-server/pull/3130) :gift:
* v103.8.1 Fix high CPU load during data cleanup tasks [livingdocs-server #3128](https://github.com/livingdocsIO/livingdocs-server/pull/3128) :gift:
* v103.8.0 fix(imatrics): store slugged variant of title with every concept in imatrics metadata [livingdocs-server #3125](https://github.com/livingdocsIO/livingdocs-server/pull/3125) :gift:
* v103.7.8 Don't validate image metadata in public api for import [livingdocs-server #3121](https://github.com/livingdocsIO/livingdocs-server/pull/3121) :gift:
* v103.7.7 fix: improve public api errors [livingdocs-server #3111](https://github.com/livingdocsIO/livingdocs-server/pull/3111) :gift:
* v103.7.6 Fix userApi.findByProjectId pagination [livingdocs-server #3119](https://github.com/livingdocsIO/livingdocs-server/pull/3119) :gift:
* v103.7.5 chore: remove try-catch blocks from controllers [livingdocs-server #3118](https://github.com/livingdocsIO/livingdocs-server/pull/3118) :gift:
* v103.7.4 Always log seeding errors [livingdocs-server #3115](https://github.com/livingdocsIO/livingdocs-server/pull/3115) :gift:
* v103.7.3 fix(media library): remove the media library event webhook [livingdocs-server #3114](https://github.com/livingdocsIO/livingdocs-server/pull/3114) :gift:
* v103.7.2 Fix inconsistency in publication query builder [livingdocs-server #3112](https://github.com/livingdocsIO/livingdocs-server/pull/3112) :gift:
* v103.7.1 fix(wooding): do not throw from the woodwing sync event handler but log the error [livingdocs-server #3113](https://github.com/livingdocsIO/livingdocs-server/pull/3113) :gift:
* v103.7.0 Integrate ww assets [livingdocs-server #3108](https://github.com/livingdocsIO/livingdocs-server/pull/3108) :gift:
* v103.6.0 WoodWing assets integration [livingdocs-server #3079](https://github.com/livingdocsIO/livingdocs-server/pull/3079) :gift:
* v103.5.3 Hugo image dnd does works with enforced metadata [livingdocs-server #3102](https://github.com/livingdocsIO/livingdocs-server/pull/3102) :gift:
* v103.5.2 fix(tasks): fix create project task for the embedded design case [livingdocs-server #3104](https://github.com/livingdocsIO/livingdocs-server/pull/3104) :gift:
* v103.5.1 Media Library: Public API [livingdocs-server #3099](https://github.com/livingdocsIO/livingdocs-server/pull/3099) :gift:
* v103.5.0 feat(includes): allow vue-component type for doc-includes [livingdocs-server #3098](https://github.com/livingdocsIO/livingdocs-server/pull/3098) :gift:
* v103.4.6 MediaLibrary: deprecate paginationSize [livingdocs-server #3092](https://github.com/livingdocsIO/livingdocs-server/pull/3092) :gift:
* v103.4.5 fix: add youtube include example, fix instagram [livingdocs-server #2939](https://github.com/livingdocsIO/livingdocs-server/pull/2939) :gift:
* v103.4.4 Fix user merge and also empty WHERE IN database queries [livingdocs-server #3093](https://github.com/livingdocsIO/livingdocs-server/pull/3093) :gift:
* v103.4.3 Deprecate assetManagement server config [livingdocs-server #3086](https://github.com/livingdocsIO/livingdocs-server/pull/3086) :gift:
* v103.4.2 fix: correct copy behavior for articles with langauges and translations [livingdocs-server #3087](https://github.com/livingdocsIO/livingdocs-server/pull/3087) :gift:
* v103.4.1 Update livingdocs-integration.json for Release Management [livingdocs-server #3085](https://github.com/livingdocsIO/livingdocs-server/pull/3085) :gift:
* v103.4.0 Bump minor version to 103.4.0 for release management [livingdocs-server #3084](https://github.com/livingdocsIO/livingdocs-server/pull/3084) :gift:

---------------EDITOR----------------------
* v57.19.1 Correctly handle drops from media library in all browsers [livingdocs-editor #3878](https://github.com/livingdocsIO/livingdocs-editor/pull/3878) :gift:
* v57.19.0 Bump minor version for release management [livingdocs-editor #3880](https://github.com/livingdocsIO/livingdocs-editor/pull/3880) :gift:
* v57.18.3 Improved sidepanel message of image component [livingdocs-editor #3879](https://github.com/livingdocsIO/livingdocs-editor/pull/3879) :gift:
* v57.18.2 Bug: Fix media library entry upload format for Comyan [livingdocs-editor #3876](https://github.com/livingdocsIO/livingdocs-editor/pull/3876) :gift:
* v57.18.1 Enable scrolling for project select screen [livingdocs-editor #3875](https://github.com/livingdocsIO/livingdocs-editor/pull/3875) :gift:
* v57.18.0 (Media Library) parallel upload and mass metadata editing when uploading images with required metadata [livingdocs-editor #3814](https://github.com/livingdocsIO/livingdocs-editor/pull/3814) :gift:
* v57.17.8 feat(print-proxy): Add `editions` endpoint [livingdocs-editor #3873](https://github.com/livingdocsIO/livingdocs-editor/pull/3873) :gift:
* v57.17.7 fix: do not trigger imatrics updates if imatrics is not initialized [livingdocs-editor #3870](https://github.com/livingdocsIO/livingdocs-editor/pull/3870) :gift:
* v57.17.6 Update Pull Request Template [livingdocs-editor #3869](https://github.com/livingdocsIO/livingdocs-editor/pull/3869) :gift:
* v57.17.5 fix(lists): show correct date for future publication [livingdocs-editor #3865](https://github.com/livingdocsIO/livingdocs-editor/pull/3865) :gift:
* v57.17.4 Fix public api docs [livingdocs-editor #3859](https://github.com/livingdocsIO/livingdocs-editor/pull/3859) :gift:
* v57.17.3 create URL object for ImageProxy in getOriginalUrl [livingdocs-editor #3848](https://github.com/livingdocsIO/livingdocs-editor/pull/3848) :gift:
* v57.17.2 raise events only on local comment changes [livingdocs-editor #3855](https://github.com/livingdocsIO/livingdocs-editor/pull/3855) :gift:
* v57.17.1 Framework Image Service 2.0 [livingdocs-editor #3833](https://github.com/livingdocsIO/livingdocs-editor/pull/3833) :gift:
* v57.17.0 UI Hint Additions [livingdocs-editor #3835](https://github.com/livingdocsIO/livingdocs-editor/pull/3835) :gift:
* v57.16.2 add browserSpellcheck config on livingdoc creation [livingdocs-editor #3853](https://github.com/livingdocsIO/livingdocs-editor/pull/3853) :gift:
* v57.16.1 Category Filter and Unsupported Filters on Dashboard [livingdocs-editor #3850](https://github.com/livingdocsIO/livingdocs-editor/pull/3850) :gift:
* v57.16.0 Referenced Documents [livingdocs-editor #3796](https://github.com/livingdocsIO/livingdocs-editor/pull/3796) :gift:
* v57.15.9 fix: add error message template for asset proxy [livingdocs-editor #3851](https://github.com/livingdocsIO/livingdocs-editor/pull/3851) :gift:
* v57.15.8 fix(metadata): correctly set image uploading state after image uploaded [livingdocs-editor #3845](https://github.com/livingdocsIO/livingdocs-editor/pull/3845) :gift:
* v57.15.7 Context Menu [livingdocs-editor #3843](https://github.com/livingdocsIO/livingdocs-editor/pull/3843) :gift:
* v57.15.6 fix(buttons): fix image upload button icon [livingdocs-editor #3841](https://github.com/livingdocsIO/livingdocs-editor/pull/3841) :gift:
* v57.15.5 fix: show loading button while image is uploading in metadata image form [livingdocs-editor #3839](https://github.com/livingdocsIO/livingdocs-editor/pull/3839) :gift:
* v57.15.4 Small Wording Improvements [livingdocs-editor #3824](https://github.com/livingdocsIO/livingdocs-editor/pull/3824) :gift:
* v57.15.3 Relative date range filters [livingdocs-editor #3813](https://github.com/livingdocsIO/livingdocs-editor/pull/3813) :gift:
* v57.15.2 Reference Empty State [livingdocs-editor #3826](https://github.com/livingdocsIO/livingdocs-editor/pull/3826) :gift:
* v57.15.1 fix(imatrics): store any concept properties returned from the server [livingdocs-editor #3837](https://github.com/livingdocsIO/livingdocs-editor/pull/3837) :gift:
* v57.15.0 Test – Broken Image [livingdocs-editor #3828](https://github.com/livingdocsIO/livingdocs-editor/pull/3828) :gift:
* v57.14.3 Integrations in Project Setup Menu [livingdocs-editor #3823](https://github.com/livingdocsIO/livingdocs-editor/pull/3823) :gift:
* v57.14.2 fix drop indicator for hugo and asset drop [livingdocs-editor #3831](https://github.com/livingdocsIO/livingdocs-editor/pull/3831) :gift:
* v57.14.1 import icon css to diff css [livingdocs-editor #3819](https://github.com/livingdocsIO/livingdocs-editor/pull/3819) :gift:
* v57.14.0 Fix imatrics ui [livingdocs-editor #3817](https://github.com/livingdocsIO/livingdocs-editor/pull/3817) :gift:
* v57.13.2 Adapt documentation for public-api/images/import [livingdocs-editor #3818](https://github.com/livingdocsIO/livingdocs-editor/pull/3818) :gift:
* v57.13.1 update metadata comment count only locally [livingdocs-editor #3816](https://github.com/livingdocsIO/livingdocs-editor/pull/3816) :gift:
* v57.13.0 Remove internal vue registry usage [livingdocs-editor #3815](https://github.com/livingdocsIO/livingdocs-editor/pull/3815) :gift:
* v57.12.5 Lists – Empty State and Search [livingdocs-editor #3812](https://github.com/livingdocsIO/livingdocs-editor/pull/3812) :gift:
* v57.12.4 Rich List Actions [livingdocs-editor #3811](https://github.com/livingdocsIO/livingdocs-editor/pull/3811) :gift:
* v57.12.3 Fix url getter for liImageProxy [livingdocs-editor #3809](https://github.com/livingdocsIO/livingdocs-editor/pull/3809) :gift:
* v57.12.2 fix reset filters css [livingdocs-editor #3807](https://github.com/livingdocsIO/livingdocs-editor/pull/3807) :gift:
* v57.12.1 Fix notification + imatrics issues [livingdocs-editor #3803](https://github.com/livingdocsIO/livingdocs-editor/pull/3803) :gift:
* v57.12.0 Dashboard filter wrapping [livingdocs-editor #3801](https://github.com/livingdocsIO/livingdocs-editor/pull/3801) :gift:
* v57.11.1 Fix google vision setup form [livingdocs-editor #3805](https://github.com/livingdocsIO/livingdocs-editor/pull/3805) :gift:
* v57.11.0 UI Hint [livingdocs-editor #3804](https://github.com/livingdocsIO/livingdocs-editor/pull/3804) :gift:
* v57.10.0 Add api for registering custom vue filters [livingdocs-editor #3777](https://github.com/livingdocsIO/livingdocs-editor/pull/3777) :gift:
* v57.9.6 Do not display image thumbnails in original image size [livingdocs-editor #3799](https://github.com/livingdocsIO/livingdocs-editor/pull/3799) :gift:
* v57.9.5 fix(webhooks): remove mediaLibraryEntry.added webhook from webhook form [livingdocs-editor #3800](https://github.com/livingdocsIO/livingdocs-editor/pull/3800) :gift:
* v57.9.4 Search field is cleared after an article is opened [livingdocs-editor #3795](https://github.com/livingdocsIO/livingdocs-editor/pull/3795) :gift:
* v57.9.3 fix(login-overlay): is full width again [livingdocs-editor #3791](https://github.com/livingdocsIO/livingdocs-editor/pull/3791) :gift:
* v57.9.2 Fixes offline banner refresh button behaviour [livingdocs-editor #3789](https://github.com/livingdocsIO/livingdocs-editor/pull/3789) :gift:
* v57.9.1 Dispose monaco model before instance [livingdocs-editor #3787](https://github.com/livingdocsIO/livingdocs-editor/pull/3787) :gift:
* v57.9.0 Integrate Woodwing assets [livingdocs-editor #3771](https://github.com/livingdocsIO/livingdocs-editor/pull/3771) :gift:
* v57.8.1 fix(mediaLibrary test): fix cypress metadata extraction test after metadata schema change in example project [livingdocs-editor #3786](https://github.com/livingdocsIO/livingdocs-editor/pull/3786) :gift:
* v57.8.0 feat: add character counter on metadata fields [livingdocs-editor #3769](https://github.com/livingdocsIO/livingdocs-editor/pull/3769) :gift:
* v57.7.4 fix: showListAssignment config works correctly again [livingdocs-editor #3781](https://github.com/livingdocsIO/livingdocs-editor/pull/3781) :gift:
* v57.7.3 introduces a new config to set displayfilters on the liMetaReferenceForm [livingdocs-editor #3780](https://github.com/livingdocsIO/livingdocs-editor/pull/3780) :gift:
* v57.7.2 Fix webhook settings screen [livingdocs-editor #3775](https://github.com/livingdocsIO/livingdocs-editor/pull/3775) :gift:
* v57.7.1 Fix ld notify typo [livingdocs-editor #3772](https://github.com/livingdocsIO/livingdocs-editor/pull/3772) :gift:
* v57.7.0 feat(doc-includes): allow for vue components to define include params [livingdocs-editor #3768](https://github.com/livingdocsIO/livingdocs-editor/pull/3768) :gift:
* v57.6.10 Fix Menu Sorting  [livingdocs-editor #3765](https://github.com/livingdocsIO/livingdocs-editor/pull/3765) :gift:
* v57.6.9 fix: add youtube include example, fix instagram [livingdocs-editor #3487](https://github.com/livingdocsIO/livingdocs-editor/pull/3487) :gift:
* v57.6.8 Various release bug fixes [livingdocs-editor #3763](https://github.com/livingdocsIO/livingdocs-editor/pull/3763) :gift:
* v57.6.7 fix: show scrollbar in read-only views [livingdocs-editor #3758](https://github.com/livingdocsIO/livingdocs-editor/pull/3758) :gift:
* v57.6.6 fix: correctly load older revisions for the history [livingdocs-editor #3756](https://github.com/livingdocsIO/livingdocs-editor/pull/3756) :gift:
* v57.6.5 fix: default redirect for articles [livingdocs-editor #3755](https://github.com/livingdocsIO/livingdocs-editor/pull/3755) :gift:
* v57.6.4 Fix broken setup for content types with languages [livingdocs-editor #3748](https://github.com/livingdocsIO/livingdocs-editor/pull/3748) :gift:
* v57.6.3 fix: add backwards compability for deeplinks to articles [livingdocs-editor #3750](https://github.com/livingdocsIO/livingdocs-editor/pull/3750) :gift:
* v57.6.2 Resolve issue that leads to search screens throwing errors [livingdocs-editor #3749](https://github.com/livingdocsIO/livingdocs-editor/pull/3749) :gift:
* v57.6.1 Update livingdocs-integration.json for Release Management [livingdocs-editor #3747](https://github.com/livingdocsIO/livingdocs-editor/pull/3747) :gift:
* v57.6.0 Bump minor version to 57.6.0 for release management [livingdocs-editor #3746](https://github.com/livingdocsIO/livingdocs-editor/pull/3746) :gift:
  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
