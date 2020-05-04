------------------------------------------------------------------
LAAAAAAAAAAAAAAAAAAAAAST STATE of release notes
server - 94.9.1
editor - 49.12.1
------------------------------------------------------------------

**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Patches](#repositories)
- [Highlights](#highlights)
- [Breaking Changes](#breaking-changes-fire)
- [APIs](#apis-gift)
- [Other Changes](#other-changes)

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2020-05`
`@livingdocs/editor` | `release-2020-05`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "??.?.?",
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
  "@livingdocs/editor": "??.?.?",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-YYYY-MM

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): text



# Highlights

----------------- WEBHOOOOKS --------------------
* v94.5.0 Webhooks system [livingdocs-server #2907](https://github.com/livingdocsIO/livingdocs-server/pull/2907) :gift:
* v49.9.0 Webhooks [livingdocs-editor #3445](https://github.com/livingdocsIO/livingdocs-editor/pull/3445) :gift:


----------------- Delivery Links ----------------
* v94.7.0 deliveryLinks (publish panel links to frontend) [livingdocs-server #2924](https://github.com/livingdocsIO/livingdocs-server/pull/2924) :gift:
* v49.10.0 deliveryLinks (and custom function for NZZ) [livingdocs-editor #3453](https://github.com/livingdocsIO/livingdocs-editor/pull/3453) :gift:

---------------Custom Document Preview----------------
* v94.8.0 feat: new /documents/preview enpoint for custom previews of a document [livingdocs-server #2887](https://github.com/livingdocsIO/livingdocs-server/pull/2887) :gift:
* v49.11.0 Optional custom document previews in the sidepanel [livingdocs-editor #3410](https://github.com/livingdocsIO/livingdocs-editor/pull/3410) :gift:

------------- remote include ---------------------
* v49.12.0 remote include services on channelConfig  [livingdocs-editor #3451](https://github.com/livingdocsIO/livingdocs-editor/pull/3451) :gift:
* v94.9.0 remote include services on channelConfig [livingdocs-server #2922](https://github.com/livingdocsIO/livingdocs-server/pull/2922) :gift:





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


# APIs :gift:


# Other Changes

### Features

* Metadata: Add `li-publish-date` metadata plugin [livingdocs-server #2929](https://github.com/livingdocsIO/livingdocs-server/pull/2929) :gift:
* Images: Add `libvips` as `images.processingStrategy` which is twice as fast as `imagemagick` [livingdocs-server #2925](https://github.com/livingdocsIO/livingdocs-server/pull/2925) :gift:
* Elasticsearch: Indexes and support `numberOfReplicas` and `numberOfShards` configs [livingdocs-server #2911](https://github.com/livingdocsIO/livingdocs-server/pull/2911) :gift:
* Image: Add remove image button for an existing image on the properties panel [livingdocs-editor #3444](https://github.com/livingdocsIO/livingdocs-editor/pull/3444) :gift:

### Design

* ... :gift:

### Improvements

* ChannelConfig: Handle/validate static and dynamic channelConfig the same way [livingdocs-server #2906](https://github.com/livingdocsIO/livingdocs-server/pull/2906) :gift:
* References: Move the extraction from the editor to the server (on create / on save) [livingdocs-server #2901](https://github.com/livingdocsIO/livingdocs-server/pull/2901) :gift:
* Metadata: Add default item for `liMetaSelect` component [livingdocs-editor #3423](https://github.com/livingdocsIO/livingdocs-editor/pull/3423) :gift:
* Config: Allow to configure metadata reference search to only show published records [livingdocs-editor #3466](https://github.com/livingdocsIO/livingdocs-editor/pull/3466) :gift:

### Bugfixes

* Import: Add image service URL to imported image [livingdocs-server #2889](https://github.com/livingdocsIO/livingdocs-server/pull/2889) :beetle:
* Images: Fix image extraction bug [livingdocs-server #2896](https://github.com/livingdocsIO/livingdocs-server/pull/2896) :beetle:
* Imatrics: Config fixes [livingdocs-server #2923](https://github.com/livingdocsIO/livingdocs-server/pull/2923) :beetle:
* History: 
  * Fix history user colors [livingdocs-editor #3424](https://github.com/livingdocsIO/livingdocs-editor/pull/3424) :beetle:
  * Fix history char counter & PO-truck [livingdocs-editor #3431](https://github.com/livingdocsIO/livingdocs-editor/pull/3431) :beetle:
* Navigation: Fix spacing / scrolling [livingdocs-editor #3440](https://github.com/livingdocsIO/livingdocs-editor/pull/3440) :beetle:


  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
