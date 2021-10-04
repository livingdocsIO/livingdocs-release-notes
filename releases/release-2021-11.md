Server until: 155.0.10
Editor until: 74.1.10


**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content <!-- omit in toc -->
- [Newsletter](#newsletter)
- [Webinar](#webinar)
- [Highlights](#highlights)
- [Breaking Changes :fire:](#breaking-changes-fire)
- [Deprecations](#deprecations)
- [APIs :gift:](#apis-gift)
- [Internal Changes](#internal-changes)
- [Other Changes](#other-changes)
- [Patches](#patches)

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

### Document Inbox
* v73.1.0 Document inbox [livingdocs-editor #4661](https://github.com/livingdocsIO/livingdocs-editor/pull/4661) :gift:
* v154.2.0 Document inbox [livingdocs-server #3911](https://github.com/livingdocsIO/livingdocs-server/pull/3911) :gift:

### EXAMPLE :tada:

...Description...

* References
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/2143)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/246)




# Breaking Changes :fire:

#### Migrate the database

- Expected duration?
- Possible data losses?
- Is it a simple migration? (fast/easy downgradable)

```sh
# run grunt migrate to update to the newest database scheme
# migration - 111-add-comments-table.js
#   create comments table + add events to the stream_events_types table
livingdocs-server migrate up
```

#### Remove Deprecated Editor Config :fire:

- 🔥 remove deprecated editor config `hugo.assetHost` - use server config `hugo.assetHost` instead
- 🔥 remove deprecated editor config `app.imageService` - use server config `documents.selectedImageService` instead

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4691)

#### Remove DocumentModel Getters :fire:

Some internal methods got removed. If you use any of the following methods, please rather use `documentWriteModel.metadata` directly.

- `documentWriteModel.metadata.setProperties(obj)` got removed. Please use `.setProperty` for now.
- `documentWriteModel.metadata.serialize()` got removed. Please use `.splittedSerialize()`
- `documentWriteModel.metadata.getEntity()` got removed. Please use `documentWriteModel.metadata.entity`

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/4024)


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
* Import: Within a reimport the design version can be updated [livingdocs-server #3957](https://github.com/livingdocsIO/livingdocs-server/pull/3957) :gift:
* Media Library: Support boolean flag=false / exists filters in metadata search [livingdocs-server #4012](https://github.com/livingdocsIO/livingdocs-server/pull/4012) :gift:
* Push Notifications: Add suport for segments in airship [livingdocs-server #3953](https://github.com/livingdocsIO/livingdocs-server/pull/3953) :gift:

### Bugfixes

* Editor
  * Fix line wrap behavior [livingdocs-editor #4705](https://github.com/livingdocsIO/livingdocs-editor/pull/4705) :beetle:
  * Fix newline behavior [livingdocs-editor #4726](https://github.com/livingdocsIO/livingdocs-editor/pull/4726) :beetle:
  * Change Toolbar max Offset to fix Overlapping Action Bar Issue [livingdocs-editor #4737](https://github.com/livingdocsIO/livingdocs-editor/pull/4737) :beetle:
  * The Vue metadata plugin `li-form-select` handles undefined values the same way as the Angular plugins [livingdocs-editor #4742](https://github.com/livingdocsIO/livingdocs-editor/pull/4742) :beetle:
  * Clipboard: Stop the clipboard drag event when deleting the last item from the clipboard [livingdocs-editor #4743](https://github.com/livingdocsIO/livingdocs-editor/pull/4743) :beetle:
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
* Document Inbox: Prevent duplicate references from being added to an inbox [livingdocs-server #3956](https://github.com/livingdocsIO/livingdocs-server/pull/3956) :beetle:
* Storage: Use correct day of the month for storage keys [livingdocs-server #3997](https://github.com/livingdocsIO/livingdocs-server/pull/3997) :beetle:



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
