
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

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
