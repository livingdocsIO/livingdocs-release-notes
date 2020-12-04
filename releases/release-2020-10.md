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
- [v104.1.16](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.16): fix: validate users in the userSetupFlow
- [v104.1.15](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.15): fix(user-invite): Escape user input html
- [v104.1.14](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.14): fix(image-media-types): correctly extract the 'iptc: Credit' field from images if there is no xmp metadata on the image
- [v104.1.13](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.13): refactor: async/await with callbackify
- [v104.1.12](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.12): test(public-api): adapt fixtures
- [v104.1.11](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.11): fix(routing): use slug in :slug pattern
- [v104.1.10](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.10): fix(import): improve error logging
- [v104.1.9](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.9): fix(elasticsearch): log cpu-wait as warning
- [v104.1.8](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.8): fix(hugo): allow target without design
- [v104.1.7](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.7): fix: do not throw on unhandled rejections in the import api
- [v104.1.6](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.6): fix: fix tests and logs of import api
- [v104.1.5](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.5): chore(migrations): add tests for embedded switch
- [v104.1.4](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v104.1.4): imatrics: fix an inconsitency in slugging



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
- [v57.18.33](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.33): fix(groups): Fix the member list and add to group search and actions to properly filter users
- [v57.18.32](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.32): fix: correctly indicate total users
- [v57.18.31](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.31): fix(embeds): Avoid transforming free-html content
- [v57.18.30](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.30): fix(admin): Cap the users list to 500 entries until we have the pagination

Users are still searchable because we load all users into the search object
- [v57.18.29](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.29): chore(twitch): make chat optional
- [v57.18.28](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.28): fix(counter): only exclude from total count
- [v57.18.27](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.27): fix: use given color and add different padding
- [v57.18.26](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.26): fix: conflict highlight label height to set on overlay object
- [v57.18.25](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.25): fix: defaultSearchEntityLabel remove the s
- [v57.18.24](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.24): fix(time-range-filter): use correct key for 'Past week'
- [v57.18.23](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.23): fix(embeds): do not add padding bottom unless it's a responsive container
- [v57.18.22](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.22): fix(public-api): add documentation for document lists
- [v57.18.21](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.21): fix(iframes): pasting iframes with the addResponsiveContainer: false config works reliably again
- [v57.18.20](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.20): fix(trackjs): add empty string instead of undefined

the token is not written when the userId is set to undefined
- [v57.18.19](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.19): fix: use foreach to get task object
- [v57.18.18](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.18): fix(date-range): allow strings for dateRange query
- [v57.18.17](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.17): fix: improve import error log
- [v57.18.16](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.16): chore: do not allowUnrecognizedEmbeds by default in our setup unless env = local
- [v57.18.15](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.15): chore: adapt tests
- [v57.18.14](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.14): chore(migrations): add cypress tests
- [v57.18.13](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.18.13): fix styling of conflict handling buttons




# Highlights

## New APIs :tada:

We added numerous APIs for the 'public API', 'livingdocs-server CLI' and we have good progress with the Angular to Vue
transition. Find more in the [APIs](#apis-gift) section of the release notes.

## WoodWing Assets Integration :tada:

Adds a basic WoodWing integration into Livingdocs:
- Support drag+drop from WoodWing assets to Livingdocs
- Whenever an image is uploaded to Livingdocs, it's also uploaded to WoodWing assets with some basic metadata.

References:
  * [Video](https://vimeo.com/444823016)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3771)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3079)

Related: We also implemented an open-source boilerplate for a [Livingdocs to WoodWing Studio transformer](https://github.com/livingdocsIO/livingdocs-to-woodwing-exporter) as an AWS serverless app.


## Referenced Documents :tada:

We harmonized the visual appearance for document references in the editor e.g.
- media library document references
- 'copy of' / 'embedded in' on the publish screen
- ...more will follow in the next releases

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3796)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3140)


## Parallel Image Upload :tada:

We improved the image uploading process for cases when the user needs to provide image metadata before an image can be uploaded.

The improvements are:
- Upload multiple images in parallel
- Edit metadata for multiple images at once
- Cancel single uploads

![image](https://user-images.githubusercontent.com/821875/92760343-da357c80-f390-11ea-878e-d29b44285db2.png)

Look at this [PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3814) for some impressions.



## Image Service 2.0 :tada:

Livingdocs supports mechanisms to crop images and serve images in an optimised way to browsers and devices. This is done by uploading an original image and then cropping or resizing it on the fly through a SaaS image service.
We improved this process, e.g.
- integrate your own image service by registering a url building function
- improved the possibilities to configure the image rendering process

For more details read the [image service evaluation guide](https://docs.livingdocs.io/evaluation-guide/image-services) or the [documentation diff](https://github.com/livingdocsIO/livingdocs/pull/330).

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/330)
  * [Framework PR](https://github.com/livingdocsIO/livingdocs-framework/pull/497)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3833)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3144)



# Breaking Changes :fire:

## Migrate the database

It's a simple/fast migration with no expected data losses.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 139-fix-title-on-media-library-entries.js
#   set title on media_library_entries table
# migration - 140-migration-log.js
#   create table document_migration_log
# migration - 141-drop-document_migrations_field.js
#   drop NOT NULL condition on document_migrations.legacy_design_version
livingdocs-server migrate up
```

## Resrc.it Image Service

When using `resrc.it` as image service, one needs to set its render strategy in the server configuration:

```js
'resrc.it': {
  quality: 75,
  host: 'https://app.resrc.it',

  // new options
  imgTagRenderStrategy: 'resrcit',
  anyTagRenderStrategy: 'resrcit'
}
```

References: [Framework PR](https://github.com/livingdocsIO/livingdocs-framework/pull/497)


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

## Register Custom Vue Display Filter :gift:

One can register a Vue component as a custom display filter (e.g. on a dashboard).

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/317)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3777)

## Customise Editor UI with Vue for Doc Includes :gift:

Implement a [custom Editor UI](https://docs.livingdocs.io/reference-docs/includes/editor_customization) for doc-includes with Vue.

References:
  * [Documentation (custom Editor UI)](https://docs.livingdocs.io/reference-docs/includes/editor_customization)
  * [Documentation (Twitter Example)](https://github.com/livingdocsIO/livingdocs/pull/312)
  * [Documentation (doc-include)](https://docs.livingdocs.io/evaluation-guide/intro#summary-of-a-doc-include)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3768)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3098)


## Public API - Media Library Endpoints :gift:

The public API contains new endpoints for the media library.

Examples:
- `GET /api/v1/mediaLibrary/:id`
- `GET /api/v1/mediaLibrary?ids=1,2,3` or `GET /api/v1/mediaLibrary?externalId=foo&systemName=comyan`

References:
  * Documentation - 'https://your-editor.com/public-api'
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3895)

## Public API - Expose Public API via the server API :gift:

Get access to the public API via server API
- `const publicApi = liServer.features.api('li-public-api')`

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3138)


## Public API - Support client defined documentId in the import API :gift:

During a migration of an existing system, it's best practice to migrate all entries of the old system into livingdocs.
To ease the migration, we want to support user-defined identifiers, so a custom import script can reuse existing identifiers.

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3145)
  * [Documentation](TODO Marc)


## Livingdocs-server CLI - Simplify data migrations :gift:

Added a new CLI task `livingdocs-server data-migration-run`. `data-migration-run` combines `grunt data-migration-create-and-prepare` and `grunt data-migration-accept` into one step.
Improvements:
- migrate multiple design versions in one step to a target design version (e.g. 1.0.0 + 1.0.1 to 2.0.0)
- add `--filter-by-content-type` filter to migrations
- Get a manual and examples when executing `livingdocs-server data-migration-run` on the terminal
- Show a specific migration report for either a version bump or a data migration

References:
  * [Server PR - data-migration-run](https://github.com/livingdocsIO/livingdocs-server/pull/3151)
  * [Server PR - report](https://github.com/livingdocsIO/livingdocs-server/pull/3148)

## Livingdocs-server CLI - Improve reindex tasks :gift:

New options are supported
- `livingdocs-server es-search-reindex` supports a project filter, e.g. `--project=magazine`
- `livingdocs-server es-publication-reindex` supports a project filter, e.g. `--project=magazine`
- `livingdocs-server es-publication-reindex` supports a contentType filter, e.g. `--content-type=regular`

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3162)





# Internal Changes

Changes that should not affect customers.
But some customers use internal functions and can be affected by this changes.

## CSS Changes

```
// renamed CSS classes
ld-filter-toolbar -> li-filter-toolbar
ld-filter.is-disabled renamed to li-filter-group__item--disabled
ld-filter.is-set renamed to li-filter-group__item--active

// removed CSS classes
ld-filter
ld-filter-options
```

PR: [livingdocs-editor #3801](https://github.com/livingdocsIO/livingdocs-editor/pull/3801)




# Other Changes

### Design

* A lot of small UI hint additions [livingdocs-editor #3835](https://github.com/livingdocsIO/livingdocs-editor/pull/3835) :gift:

### Improvements

* Media Library
  * Show message when an image is not used in any document [livingdocs-editor #3826](https://github.com/livingdocsIO/livingdocs-editor/pull/3826) :gift:
  * Show proper message when image is broken [livingdocs-editor #3828](https://github.com/livingdocsIO/livingdocs-editor/pull/3828) :gift:
* Imatrics
  * Store any concept properties returned from the server [livingdocs-editor #3837](https://github.com/livingdocsIO/livingdocs-editor/pull/3837) :gift:
  * Update suggestion in realtime in the dashboard [livingdocs-editor #3817](https://github.com/livingdocsIO/livingdocs-editor/pull/3817) :gift:
  * Do not trigger imatrics updates if imatrics is not initialized [livingdocs-editor #3870](https://github.com/livingdocsIO/livingdocs-editor/pull/3870) :gift:
* Dashboards
  * Support relative date range in display filters [livingdocs-editor #3813](https://github.com/livingdocsIO/livingdocs-editor/pull/3813) :gift:
  * Small Wording Improvements [livingdocs-editor #3824](https://github.com/livingdocsIO/livingdocs-editor/pull/3824) :gift:
  * Empty state and search improvements on list dashboard [livingdocs-editor #3812](https://github.com/livingdocsIO/livingdocs-editor/pull/3812) :gift:
  * Wrap display filter (UI) [livingdocs-editor #3801](https://github.com/livingdocsIO/livingdocs-editor/pull/3801) :gift:
  * Improve rich list actions CSS (e.g. list on the dashboard) [livingdocs-editor #3811](https://github.com/livingdocsIO/livingdocs-editor/pull/3811) :gift:
* Publish Screen
  * Add character counter on metadata fields [livingdocs-editor #3769](https://github.com/livingdocsIO/livingdocs-editor/pull/3769) :gift:
  * Show loading button while image is uploading in metadata image form [livingdocs-editor #3839](https://github.com/livingdocsIO/livingdocs-editor/pull/3839) :gift:
* Metadata: Add config to set displayfilters on the liMetaReferenceForm [livingdocs-editor #3780](https://github.com/livingdocsIO/livingdocs-editor/pull/3780) :gift:
* Project select screen: Enable scrolling [livingdocs-editor #3875](https://github.com/livingdocsIO/livingdocs-editor/pull/3875) :gift:
* Redis: Add Redis debug logs and automatically reconnect against primary [livingdocs-server #3156](https://github.com/livingdocsIO/livingdocs-server/pull/3156) :gift:
* Woodwing assets: Use S3 URL for Woodwing assets [livingdocs-server #3132](https://github.com/livingdocsIO/livingdocs-server/pull/3132) :gift:
* Livingdocs CLI: Add --throttle argument to fix high CPU load during data cleanup tasks [livingdocs-server #3128](https://github.com/livingdocsIO/livingdocs-server/pull/3128) :gift:
* Public API: Never return HTTP Status 500 [livingdocs-server #3111](https://github.com/livingdocsIO/livingdocs-server/pull/3111) :gift:
* Project seeding: Always log seeding errors [livingdocs-server #3115](https://github.com/livingdocsIO/livingdocs-server/pull/3115) :gift:
* Image component: Improved sidepanel message of image component [livingdocs-editor #3879](https://github.com/livingdocsIO/livingdocs-editor/pull/3879) :gift:

### Bugfixes

* Dashboard:
  * Fix context menu behaviour [livingdocs-editor #3843](https://github.com/livingdocsIO/livingdocs-editor/pull/3843) :beetle:
  * Fix Category display filter [livingdocs-editor #3850](https://github.com/livingdocsIO/livingdocs-editor/pull/3850) :beetle:
* Image upload: Fix image uploads for PDF's when using imagemagick [livingdocs-server #3134](https://github.com/livingdocsIO/livingdocs-server/pull/3134) :beetle:
* Public API: Don't validate hardcoded image metadata of image import, use the dynamic config instead [livingdocs-server #3121](https://github.com/livingdocsIO/livingdocs-server/pull/3121) :beetle:
* UserApi: Fix userApi.findByProjectId pagination [livingdocs-server #3119](https://github.com/livingdocsIO/livingdocs-server/pull/3119) :beetle:
* Publication index: Fix inconsistency in publication query builder [livingdocs-server #3112](https://github.com/livingdocsIO/livingdocs-server/pull/3112) :beetle:
* Hugo: Image dnd does work with enforced metadata [livingdocs-server #3102](https://github.com/livingdocsIO/livingdocs-server/pull/3102) :beetle:
* Includes: fix youtube and instagram include [livingdocs-server #2939](https://github.com/livingdocsIO/livingdocs-server/pull/2939) :beetle:
* User: Fix user merge and also empty WHERE IN database queries [livingdocs-server #3093](https://github.com/livingdocsIO/livingdocs-server/pull/3093) :beetle:
* Publication date: Show correct date for future publication [livingdocs-editor #3865](https://github.com/livingdocsIO/livingdocs-editor/pull/3865) :beetle:
* Spellcheck: Fix browser spellcheck document creation [livingdocs-editor #3853](https://github.com/livingdocsIO/livingdocs-editor/pull/3853) :beetle:
* Project setup: Show Integrations only if there are some [livingdocs-editor #3823](https://github.com/livingdocsIO/livingdocs-editor/pull/3823) :beetle:
* Notifications: Fix drop indicator for hugo and asset drop [livingdocs-editor #3831](https://github.com/livingdocsIO/livingdocs-editor/pull/3831) :beetle:
* Comments: Update metadata comment count only locally [livingdocs-editor #3816](https://github.com/livingdocsIO/livingdocs-editor/pull/3816) :beetle:
* Fix google vision setup form [livingdocs-editor #3805](https://github.com/livingdocsIO/livingdocs-editor/pull/3805) :beetle:
* Do not display image thumbnails in original image size [livingdocs-editor #3799](https://github.com/livingdocsIO/livingdocs-editor/pull/3799) :beetle:
* Publish Screen: List assignment works correctly again [livingdocs-editor #3781](https://github.com/livingdocsIO/livingdocs-editor/pull/3781) :beetle:
* Fix webhook settings screen [livingdocs-editor #3775](https://github.com/livingdocsIO/livingdocs-editor/pull/3775) :beetle:
* Menu: Fix Menu Sorting  [livingdocs-editor #3765](https://github.com/livingdocsIO/livingdocs-editor/pull/3765) :beetle:
* Improves the instagram include sidebar [livingdocs-editor #3487](https://github.com/livingdocsIO/livingdocs-editor/pull/3487) :beetle:
* Various release bug fixes [livingdocs-editor #3763](https://github.com/livingdocsIO/livingdocs-editor/pull/3763) :beetle:
* Show scrollbar in read-only views [livingdocs-editor #3758](https://github.com/livingdocsIO/livingdocs-editor/pull/3758) :beetle:
* History: Correctly load older revisions for the history [livingdocs-editor #3756](https://github.com/livingdocsIO/livingdocs-editor/pull/3756) :beetle:
* Fix default redirect for articles [livingdocs-editor #3755](https://github.com/livingdocsIO/livingdocs-editor/pull/3755) :beetle:
* Document copy: Correct copy behavior for articles with langauges and translations [livingdocs-server #3087](https://github.com/livingdocsIO/livingdocs-server/pull/3087) :beetle:
* Document creation: Fix broken setup for content types with languages [livingdocs-editor #3748](https://github.com/livingdocsIO/livingdocs-editor/pull/3748) :beetle:


---

**Icon Legend**
* Breaking changes: :fire:
* Feature: :gift:
* Bugfix: :beetle:
* Chore: :wrench: