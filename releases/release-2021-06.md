
editor until: 66.2.3
server until: 127.4.2

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

# System Requirements

#### Minimal
* Node 12
* NPM 7
* Postgres 9.6
* Elasticsearch 6.x
* Redis 5

#### Suggested
* Node 14
* NPM 7
* Postgres 13
* Elasticsearch 7
* Redis 6

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2021-06`
`@livingdocs/editor` | `release-2021-06`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2021-06",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2021-06

### Livingdocs Server Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2021-06",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2021-06

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

--------------------- Server -----------------------------

* v127.4.2 Queue Fixes [livingdocs-server #3607](https://github.com/livingdocsIO/livingdocs-server/pull/3607) :gift:
* v127.4.1 Notifications: Add valid empty check to `comment.add` action handler [livingdocs-server #3605](https://github.com/livingdocsIO/livingdocs-server/pull/3605) :gift:
* v127.4.0 feat(public-api): allow to set 'publicationDate' flag on import [livingdocs-server #3569](https://github.com/livingdocsIO/livingdocs-server/pull/3569) :gift:
* v127.3.2 Sso cypress tests [livingdocs-server #3552](https://github.com/livingdocsIO/livingdocs-server/pull/3552) :gift:
* v127.3.1 fix(login): Users will be able to log in even if new device emails cant be sent [livingdocs-server #3597](https://github.com/livingdocsIO/livingdocs-server/pull/3597) :gift:
* v127.3.0 Add Support for Storage Prefix [livingdocs-server #3587](https://github.com/livingdocsIO/livingdocs-server/pull/3587) :gift:
* v127.2.4 Remove File/Image/Video/Design Upload Deprecations [livingdocs-server #3577](https://github.com/livingdocsIO/livingdocs-server/pull/3577) :gift:
* v127.2.3 fix(print): fix crash on certificate errors [livingdocs-server #3590](https://github.com/livingdocsIO/livingdocs-server/pull/3590) :gift:
* v127.2.2 Do not use offensive Project Handles [livingdocs-server #3589](https://github.com/livingdocsIO/livingdocs-server/pull/3589) :gift:
* v127.2.1 Fix unsplash plugin [livingdocs-server #3588](https://github.com/livingdocsIO/livingdocs-server/pull/3588) :gift:
* v127.2.0 Add transcoding state metadata plugin [livingdocs-server #3568](https://github.com/livingdocsIO/livingdocs-server/pull/3568) :gift:
* v127.1.3 Fix typo in xtransferexit and reduce the redis calls during xcleanup [livingdocs-server #3584](https://github.com/livingdocsIO/livingdocs-server/pull/3584) :gift:
* v127.1.2 Do not delete consumers when we can't transfer the pending messages [livingdocs-server #3581](https://github.com/livingdocsIO/livingdocs-server/pull/3581) :gift:
* v127.1.1 Simplify the pagination setup in some controllers [livingdocs-server #3579](https://github.com/livingdocsIO/livingdocs-server/pull/3579) :gift:
* v127.1.0 Sync OpenId Connect user groups on login [livingdocs-server #3563](https://github.com/livingdocsIO/livingdocs-server/pull/3563) :gift:
* v127.0.6 Upgrade to the most recent rc version of `yargs` and lock the version [livingdocs-server #3575](https://github.com/livingdocsIO/livingdocs-server/pull/3575) :gift:
* v127.0.5 Update @opentelemetry packages [livingdocs-server #3570](https://github.com/livingdocsIO/livingdocs-server/pull/3570) :gift:
* v127.0.4 fix(public-api): Include version in getMediaLibraryEntry endpoint [livingdocs-server #3567](https://github.com/livingdocsIO/livingdocs-server/pull/3567) :gift:
* v127.0.3 Do not send out too many 'new device login' emails [livingdocs-server #3571](https://github.com/livingdocsIO/livingdocs-server/pull/3571) :gift:
* v127.0.2 Support Woodwing assets as a media source [livingdocs-server #3565](https://github.com/livingdocsIO/livingdocs-server/pull/3565) :gift:
* v127.0.1 Fix date format in migration scripts [livingdocs-server #3564](https://github.com/livingdocsIO/livingdocs-server/pull/3564) :gift:
* v127.0.0 Fix metadata onUpdate hooks [livingdocs-server #3541](https://github.com/livingdocsIO/livingdocs-server/pull/3541) :gift:
* v126.2.5 Fixes a bug that could lead to identities being created without a user  [livingdocs-server #3560](https://github.com/livingdocsIO/livingdocs-server/pull/3560) :gift:
* v126.2.4 Seeding: always reset project handle cache on every project seeding [livingdocs-server #3556](https://github.com/livingdocsIO/livingdocs-server/pull/3556) :gift:
* v126.2.3 fix(print): fix `filterText()` type-check [livingdocs-server #3546](https://github.com/livingdocsIO/livingdocs-server/pull/3546) :gift:
* v126.2.2 Fix Print Host [livingdocs-server #3548](https://github.com/livingdocsIO/livingdocs-server/pull/3548) :gift:
* v126.2.1 Fix Desk-Net Plugin [livingdocs-server #3547](https://github.com/livingdocsIO/livingdocs-server/pull/3547) :gift:
* v126.2.0 CLI project-truncate - truncate elasticsearch documents too [livingdocs-server #3545](https://github.com/livingdocsIO/livingdocs-server/pull/3545) :gift:
* v126.1.0 Add firstPublicationDate to documents [livingdocs-server #3505](https://github.com/livingdocsIO/livingdocs-server/pull/3505) :gift:
* v126.0.0 Add LegacyDocumentModel getters [livingdocs-server #3542](https://github.com/livingdocsIO/livingdocs-server/pull/3542) :gift:


--------------------- Editor ------------------------------
* v66.2.3 fix(test): pin vue-test-utils version to 1.1.3 [livingdocs-editor #4344](https://github.com/livingdocsIO/livingdocs-editor/pull/4344) :gift:
* v66.2.2 Render includes when dropping a component from the clipboard [livingdocs-editor #4330](https://github.com/livingdocsIO/livingdocs-editor/pull/4330) :gift:
* v66.2.1 fix(media library): Always use crossorigin=anonymous for videos [livingdocs-editor #4335](https://github.com/livingdocsIO/livingdocs-editor/pull/4335) :gift:
* v66.2.0 Add transcoding state metadata plugin [livingdocs-editor #4324](https://github.com/livingdocsIO/livingdocs-editor/pull/4324) :gift:
* v66.1.19 Multiselect: Only allow to transform available components of a content-type [livingdocs-editor #4331](https://github.com/livingdocsIO/livingdocs-editor/pull/4331) :gift:
* v66.1.18 Fix viewport buggyfill [livingdocs-editor #4323](https://github.com/livingdocsIO/livingdocs-editor/pull/4323) :gift:
* v66.1.17 Link Tool: improve delivery path pattern matching and handling of matching paths with nonexisting IDs [livingdocs-editor #4325](https://github.com/livingdocsIO/livingdocs-editor/pull/4325) :gift:
* v66.1.16 fix(link tool): make removing an existing link possible again [livingdocs-editor #4321](https://github.com/livingdocsIO/livingdocs-editor/pull/4321) :gift:
* v66.1.15 Webhooks UI: fix the form layout for the event checkboxes [livingdocs-editor #4320](https://github.com/livingdocsIO/livingdocs-editor/pull/4320) :gift:
* v66.1.14 Fix Docked Content [livingdocs-editor #4318](https://github.com/livingdocsIO/livingdocs-editor/pull/4318) :gift:
* v66.1.13 add data-tour attribute for format-panel [livingdocs-editor #4315](https://github.com/livingdocsIO/livingdocs-editor/pull/4315) :gift:
* v66.1.12 ImageServiceFilter: Don't ignore crop for LiImageProxy [livingdocs-editor #4299](https://github.com/livingdocsIO/livingdocs-editor/pull/4299) :gift:
* v66.1.11 Fix: Server Admin User List shows avatar [livingdocs-editor #4313](https://github.com/livingdocsIO/livingdocs-editor/pull/4313) :gift:
* v66.1.10 Dashboards: Load more button below results instead of footer everywhere [livingdocs-editor #4309](https://github.com/livingdocsIO/livingdocs-editor/pull/4309) :gift:
* v66.1.9 use documentPropertyName instead of metadataPropertyName for filter [livingdocs-editor #4307](https://github.com/livingdocsIO/livingdocs-editor/pull/4307) :gift:
* v66.1.8 handle undo in editable for comments [livingdocs-editor #4301](https://github.com/livingdocsIO/livingdocs-editor/pull/4301) :gift:
* v66.1.7 Media Library: fix Video download action [livingdocs-editor #4303](https://github.com/livingdocsIO/livingdocs-editor/pull/4303) :gift:
* v66.1.6 fix(login): correctly log users into specific projects [livingdocs-editor #4295](https://github.com/livingdocsIO/livingdocs-editor/pull/4295) :gift:
* v66.1.5 Add check for admin user, when no projectBehavior exists [livingdocs-editor #4297](https://github.com/livingdocsIO/livingdocs-editor/pull/4297) :gift:
* v66.1.4 Session: always setup a policy (an empty policy always returns true) [livingdocs-editor #4294](https://github.com/livingdocsIO/livingdocs-editor/pull/4294) :gift:
* v66.1.3 ENV config: top-level config property defaults for easier config access [livingdocs-editor #4292](https://github.com/livingdocsIO/livingdocs-editor/pull/4292) :gift:
* v66.1.2 chore: add signup cypress test [livingdocs-editor #4246](https://github.com/livingdocsIO/livingdocs-editor/pull/4246) :gift:
* v66.1.1 Add documentation for /v1/publicationEvents?reverse=true [livingdocs-editor #4290](https://github.com/livingdocsIO/livingdocs-editor/pull/4290) :gift:
* v66.1.0 feat(editable): Add minimum and recommended lengths [livingdocs-editor #4255](https://github.com/livingdocsIO/livingdocs-editor/pull/4255) :gift:
* v66.0.4 Fix BW service changer [livingdocs-editor #4287](https://github.com/livingdocsIO/livingdocs-editor/pull/4287) :gift:
* v66.0.3 fix(kanban): Pass searchParams to reload function [livingdocs-editor #4285](https://github.com/livingdocsIO/livingdocs-editor/pull/4285) :gift:
* v66.0.2 fix inline list refresh [livingdocs-editor #4267](https://github.com/livingdocsIO/livingdocs-editor/pull/4267) :gift:
* v66.0.1 fix(teaser-preview): render includes in teaser preview [livingdocs-editor #4276](https://github.com/livingdocsIO/livingdocs-editor/pull/4276) :gift:
* v66.0.0 User avatar: generate avatar with user name initials instead of gravatar [livingdocs-editor #4250](https://github.com/livingdocsIO/livingdocs-editor/pull/4250) :gift:
* v65.0.11 Vue Form Generator: relax schema validation [livingdocs-editor #4274](https://github.com/livingdocsIO/livingdocs-editor/pull/4274) :gift:
* v65.0.10 fix: log users in even if they dont have a default design [livingdocs-editor #4275](https://github.com/livingdocsIO/livingdocs-editor/pull/4275) :gift:
* v65.0.9 Media Library Card: gray img background for visibility of white/transparent images [livingdocs-editor #4272](https://github.com/livingdocsIO/livingdocs-editor/pull/4272) :gift:
* v65.0.8 Show correct message when server is offline and proxiedHost is enabled [livingdocs-editor #4264](https://github.com/livingdocsIO/livingdocs-editor/pull/4264) :gift:
* v65.0.7 Metadata li-text: correctly render when config.useAsTitle [livingdocs-editor #4270](https://github.com/livingdocsIO/livingdocs-editor/pull/4270) :gift:
* v65.0.6 Twitch/Instagram Include Form [livingdocs-editor #4265](https://github.com/livingdocsIO/livingdocs-editor/pull/4265) :gift:
* v65.0.5 Fix Image Directive data handling [livingdocs-editor #4268](https://github.com/livingdocsIO/livingdocs-editor/pull/4268) :gift:
* v65.0.4 fix checkboxes for twitch and instagram include [livingdocs-editor #4262](https://github.com/livingdocsIO/livingdocs-editor/pull/4262) :gift:
* v65.0.3 Fix oderding of semantic versions in design screen [livingdocs-editor #4260](https://github.com/livingdocsIO/livingdocs-editor/pull/4260) :gift:
* v65.0.2 fix multiSourceSearch to use filters [livingdocs-editor #4257](https://github.com/livingdocsIO/livingdocs-editor/pull/4257) :gift:
* v65.0.1 Fix Project Switch [livingdocs-editor #4259](https://github.com/livingdocsIO/livingdocs-editor/pull/4259) :gift:
* v65.0.0 Drop node 12 support [livingdocs-editor #4256](https://github.com/livingdocsIO/livingdocs-editor/pull/4256) :gift:
* v64.0.0 Consolidate Navigation Panel Behavior / Feature detection instead of browser User-Agent parsing [livingdocs-editor #4244](https://github.com/livingdocsIO/livingdocs-editor/pull/4244) :gift:
* v63.11.4 Fix Clipboard Drag + Drop of a Container [livingdocs-editor #4243](https://github.com/livingdocsIO/livingdocs-editor/pull/4243) :gift:
* v63.11.3 Fix MetadataForm for Media Uploads [livingdocs-editor #4252](https://github.com/livingdocsIO/livingdocs-editor/pull/4252) :gift:
* v63.11.2 Dashboards: show an '+' incase the ES limit defaults to max 10000 total documents [livingdocs-editor #4239](https://github.com/livingdocsIO/livingdocs-editor/pull/4239) :gift:
* v63.11.1 fix(signup): correctly redirect upon signup [livingdocs-editor #4232](https://github.com/livingdocsIO/livingdocs-editor/pull/4232) :gift:
* v63.11.0 Metadata Form: opt-in Vue based metadata form rendering [livingdocs-editor #4231](https://github.com/livingdocsIO/livingdocs-editor/pull/4231) :gift:
* v63.10.1 Fix fastify-webpack dependency issue [livingdocs-editor #4234](https://github.com/livingdocsIO/livingdocs-editor/pull/4234) :gift:
* v63.10.0 Content Validation Errors [livingdocs-editor #4225](https://github.com/livingdocsIO/livingdocs-editor/pull/4225) :gift:
* v63.9.2 Fix group screen errors [livingdocs-editor #4226](https://github.com/livingdocsIO/livingdocs-editor/pull/4226) :gift:
* v63.9.1 Publish Screen: don't log errors to console when MetadataValidationErrors are returned for publish request [livingdocs-editor #4222](https://github.com/livingdocsIO/livingdocs-editor/pull/4222) :gift:
* v63.9.0 Bump minor version for release management [livingdocs-editor #4221](https://github.com/livingdocsIO/livingdocs-editor/pull/4221) :gift:
  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
