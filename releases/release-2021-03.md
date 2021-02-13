LATEST:
- server: 118.0.1
- editor: 60.1.0


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
`@livingdocs/server` | `release-2021-03`
`@livingdocs/editor` | `release-2021-03`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2021-03",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2021-03

### Livingdocs Server Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2021-03",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2021-03

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text





# Highlights

## EXAMPLE :tada:

MULTICLUSTER
* v114.1.6 Elasticsearch multi cluster indexing preparation [livingdocs-server #3299](https://github.com/livingdocsIO/livingdocs-server/pull/3299) :gift:
* * v57.34.6 Adopt server indexing api changes in indexing dashboard [livingdocs-editor #4050](https://github.com/livingdocsIO/livingdocs-editor/pull/4050) :gift:
* * v114.6.0 The next step for multi cluster indexing [livingdocs-server #3348](https://github.com/livingdocsIO/livingdocs-server/pull/3348) :gift:
* * v117.0.0 Multi Cluster Indexing [livingdocs-server #3361](https://github.com/livingdocsIO/livingdocs-server/pull/3361) :gift:
* ------> BREAKING!!!!!!
* * v117.0.2 Improve the livingdocs-server elasticsearch-index help [livingdocs-server #3371](https://github.com/livingdocsIO/livingdocs-server/pull/3371) :gift:
* * v117.1.0 Fix the indexing context in addBackgroundIndexingJobsByBatches [livingdocs-server #3373](https://github.com/livingdocsIO/livingdocs-server/pull/3373) :gift:



VIDEO
* v114.2.0 add storage config for video [livingdocs-server #3296](https://github.com/livingdocsIO/livingdocs-server/pull/3296) :gift:
* * v114.3.2 Video import: allow any url [livingdocs-server #3332](https://github.com/livingdocsIO/livingdocs-server/pull/3332) :gift:
* * v58.1.2 fix(media library): fix infinite digest cycle on video edit [livingdocs-editor #4105](https://github.com/livingdocsIO/livingdocs-editor/pull/4105) :gift:



NAMED CROPS
* v114.4.0 Named Crops [livingdocs-server #3261](https://github.com/livingdocsIO/livingdocs-server/pull/3261) :gift:
* * v58.0.0 Named crops [livingdocs-editor #4051](https://github.com/livingdocsIO/livingdocs-editor/pull/4051) :gift:
* https://github.com/livingdocsIO/livingdocs-framework/pull/511
* * v58.1.3 Improvements Named Crops [livingdocs-editor #4101](https://github.com/livingdocsIO/livingdocs-editor/pull/4101) :gift:




DOCUMENT NOTIFICATIONS
* v114.5.0 document notifications for the document author [livingdocs-server #3251](https://github.com/livingdocsIO/livingdocs-server/pull/3251) :gift:


SSO for Azure AD OPEN ID CONNECT
* v116.1.0 feat(sso): support openid connect [livingdocs-server #3355](https://github.com/livingdocsIO/livingdocs-server/pull/3355) :gift:
* @okan, where is the doc?
* @okan, where are the tests?


REFERENCES
* v116.2.0 Extract References [livingdocs-server #3341](https://github.com/livingdocsIO/livingdocs-server/pull/3341) :gift:
* * v117.4.0 References: extract videos [livingdocs-server #3383](https://github.com/livingdocsIO/livingdocs-server/pull/3383) :gift:
* not merged - public api - https://github.com/livingdocsIO/livingdocs-server/pull/3365


MEDIA SOURCES
* v117.3.0 Media Sources API [livingdocs-server #3266](https://github.com/livingdocsIO/livingdocs-server/pull/3266) :gift:
* DOC https://github.com/livingdocsIO/livingdocs/pull/357
* editor * v60.0.0 Media Sources [livingdocs-editor #4106](https://github.com/livingdocsIO/livingdocs-editor/pull/4106) :gift:


TRACING
* v117.2.0 Tracing support [livingdocs-server #3205](https://github.com/livingdocsIO/livingdocs-server/pull/3205) :gift:

PUBLIC API import context parameters
* v58.1.0 feat(publicApi docs): add docs for /import context parameter [livingdocs-editor #4100](https://github.com/livingdocsIO/livingdocs-editor/pull/4100) :gift:
* https://github.com/livingdocsIO/livingdocs-server/pull/3353










...Description...

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/2143)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/246)




# Breaking Changes :fire:


* v118.0.0 Remove legacy postgres tables [livingdocs-server #3386](https://github.com/livingdocsIO/livingdocs-server/pull/3386) :gift:
* --> remove db tables

* v115.0.0 refactor(documentApi): improve save() and udpate() [livingdocs-server #3352](https://github.com/livingdocsIO/livingdocs-server/pull/3352) :gift:
* * v116.0.0 Remove netlify webhook feature [livingdocs-server #3362](https://github.com/livingdocsIO/livingdocs-server/pull/3362) :gift:

DOC LINK DOC HTML
* v117.4.1 Update framework v18: change doc-link and doc-html to objects [livingdocs-server #3242](https://github.com/livingdocsIO/livingdocs-server/pull/3242) :gift:
* what we have to do here, why is it a breaking change and how can I update to the new version?
* https://github.com/livingdocsIO/livingdocs-framework/pull/509
* * v60.0.5 Fix doc-link and doc-html directive use [livingdocs-editor #3981](https://github.com/livingdocsIO/livingdocs-editor/pull/3981) :gift:


* v59.0.0 Fix close tags [livingdocs-editor #4107](https://github.com/livingdocsIO/livingdocs-editor/pull/4107) :gift:
-> update jquery to 3.5 -> mention that?

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
* * v57.34.4 add video and image library dashboard [livingdocs-editor #4046](https://github.com/livingdocsIO/livingdocs-editor/pull/4046) :gift:

### Design

* ... :gift:
* * v58.1.4 Priority Truck Polish [livingdocs-editor #4091](https://github.com/livingdocsIO/livingdocs-editor/pull/4091) :gift:

### Improvements

* Import: Support files with no file ending of mimeType image [livingdocs-server #3380](https://github.com/livingdocsIO/livingdocs-server/pull/3380) :gift:
* v114.3.0 feat: add extended description to error declaration class [livingdocs-server #3214](https://github.com/livingdocsIO/livingdocs-server/pull/3214) :gift:
* * v114.4.2 Add newerThan argument for CLI task cleanup-documents [livingdocs-server #3333](https://github.com/livingdocsIO/livingdocs-server/pull/3333) :gift:
* List Dashboard: Hide go to article button in list UI when dragging [livingdocs-editor #4094](https://github.com/livingdocsIO/livingdocs-editor/pull/4094) :gift:
* Editing: Add Iframe height watcher (guard) [livingdocs-editor #4108](https://github.com/livingdocsIO/livingdocs-editor/pull/4108) :gift:
* Style Guide: Clean up the style guide [livingdocs-editor #4149](https://github.com/livingdocsIO/livingdocs-editor/pull/4149) :gift:
* Image Cropping: Use downscaled image size for very large images [livingdocs-editor #4141](https://github.com/livingdocsIO/livingdocs-editor/pull/4141) :gift:
* Dashboards: properly handle pagination for a resultList [livingdocs-editor #4153](https://github.com/livingdocsIO/livingdocs-editor/pull/4153) :gift:

### Bugfixes

* ... :beetle:
* * v117.3.3 fix(media library): rename pusher topic to media and allow - in mediaId [livingdocs-server #3382](https://github.com/livingdocsIO/livingdocs-server/pull/3382) :gift:
* * v57.34.7 use video public Url and not Image public url [livingdocs-editor #4048](https://github.com/livingdocsIO/livingdocs-editor/pull/4048) :gift:
* * v57.34.13 Access Management - Groups - hide iMatrics for projects that don't use it [livingdocs-editor #4062](https://github.com/livingdocsIO/livingdocs-editor/pull/4062) :gift:
* Metadata: Correctly handle image urls when picking from article [livingdocs-editor #4132](https://github.com/livingdocsIO/livingdocs-editor/pull/4132) :gift:
* Editor Link Tool: fix link validation / update link info / no reload on enter [livingdocs-editor #4142](https://github.com/livingdocsIO/livingdocs-editor/pull/4142) :gift:
* Comments: Fix comment highlight when paging through comment cards [livingdocs-editor #4147](https://github.com/livingdocsIO/livingdocs-editor/pull/4147) :gift:










  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
