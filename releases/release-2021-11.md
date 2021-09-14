Server until: 154.2.8
Editor until: 74.1.1


**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Table of content](#table-of-content)
- [Newsletter](#newsletter)
- [Webinar](#webinar)
      - [Features](#features)
      - [Developers](#developers)
- [Highlights](#highlights)
  - [Document Inbox](#document-inbox)
  - [EXAMPLE :tada:](#example-tada)
- [Breaking Changes :fire:](#breaking-changes-fire)
  - [Migrate the database](#migrate-the-database)
- [Deprecations](#deprecations)
- [APIs :gift:](#apis-gift)
- [Internal Changes](#internal-changes)
- [Other Changes](#other-changes)
    - [Features](#features-1)
    - [Design](#design)
    - [Improvements](#improvements)
    - [Bugfixes](#bugfixes)
- [Patches](#patches)
    - [Livingdocs Server Patches](#livingdocs-server-patches)
    - [Livingdocs Editor Patches](#livingdocs-editor-patches)

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



# Highlights

## Document Inbox
* v73.1.0 Document inbox [livingdocs-editor #4661](https://github.com/livingdocsIO/livingdocs-editor/pull/4661) :gift:
* v154.2.0 Document inbox [livingdocs-server #3911](https://github.com/livingdocsIO/livingdocs-server/pull/3911) :gift:

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


* v73.0.0 Remove deprecated editor configs [livingdocs-editor #4691](https://github.com/livingdocsIO/livingdocs-editor/pull/4691) :gift:




# Deprecations




# APIs :gift:




# Internal Changes




# Other Changes

### Features

* Show login connections in server admin [livingdocs-editor #4711](https://github.com/livingdocsIO/livingdocs-editor/pull/4711) :gift:

### Design

* Button Cleanup [livingdocs-editor #4656](https://github.com/livingdocsIO/livingdocs-editor/pull/4656) :gift:
* Improve Embed and Twitter visuals [livingdocs-editor #4689](https://github.com/livingdocsIO/livingdocs-editor/pull/4689) :gift:

### Improvements

* Indexing: Get rid of `Invalid index job` logs with custom indexes [livingdocs-server #3965](https://github.com/livingdocsIO/livingdocs-server/pull/3965) :gift:
* Allow task cards to open via middle-click in new tab [livingdocs-editor #4733](https://github.com/livingdocsIO/livingdocs-editor/pull/4733) :gift:

### Bugfixes

* Billing: Request the correct time range + get the current month [livingdocs-editor #4728](https://github.com/livingdocsIO/livingdocs-editor/pull/4728) :beetle:
* Dashboards: Fix page and data record links [livingdocs-editor #4687](https://github.com/livingdocsIO/livingdocs-editor/pull/4687) :beetle:
* Media
  * Only save document when new images has been added on content load [livingdocs-editor #4697](https://github.com/livingdocsIO/livingdocs-editor/pull/4697) :beetle:
  * Select video after upload [livingdocs-editor #4715](https://github.com/livingdocsIO/livingdocs-editor/pull/4715) :beetle:
  * Able to re-trigger upload after cancelling/reset upload [livingdocs-editor #4698](https://github.com/livingdocsIO/livingdocs-editor/pull/4698) :beetle:
* Menu:
  * Fix Lost Menu Entries on save [livingdocs-editor #4703](https://github.com/livingdocsIO/livingdocs-editor/pull/4703) :beetle:
:beetle:
  * Fix Lost Menu Entries on move [livingdocs-editor #4720](https://github.com/livingdocsIO/livingdocs-editor/pull/4720) :beetle:
* Document Lists
  * Add default lister to only show published documents [livingdocs-editor #4693](https://github.com/livingdocsIO/livingdocs-editor/pull/4693)
  * Fixes multiple documents disappearing when removing a single document from a list [livingdocs-editor #4696](https://github.com/livingdocsIO/livingdocs-editor/pull/4696) :beetle:
* Editor
  * Fix line wrap behavior [livingdocs-editor #4705](https://github.com/livingdocsIO/livingdocs-editor/pull/4705) :beetle:
  * Fix newline behavior [livingdocs-editor #4726](https://github.com/livingdocsIO/livingdocs-editor/pull/4726) :beetle:
  * Change Toolbar max Offset to fix Overlapping Action Bar Issue [livingdocs-editor #4737](https://github.com/livingdocsIO/livingdocs-editor/pull/4737) :beetle:



# Patches

### Livingdocs Server Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): text

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
