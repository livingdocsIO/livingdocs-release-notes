
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
`@livingdocs/server` | `release-2020-02`
`@livingdocs/editor` | `release-2020-02`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2020-02",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2020-02

### Livingdocs Server Patches
- [v93.2.0](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v93.2.0): create new release-2020-02



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2020-02",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2020-02

### Livingdocs Editor Patches
- [v44.4.7](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v44.4.7): pusher: don't emit pusher event during init



# Highlights

## Search API for Publications :tada:

------------> TODO: Gabriel - add a nice description of the feature <----------------

References:
  * [Public API Documentation (under "search Publications")](https://edit.livingdocs.io/public-api)
  * [Documentation](https://docs.livingdocs.io/reference-documentation/server/publication-index)
  * [server PR #2695](https://github.com/livingdocsIO/livingdocs-server/pull/2695)

## Real Time Activity Log on Publish Screen :tada:

The sidebar of the publish screen now receives realtime updates of the document (work status of other users).

![someone-else-editing-while-in-publish](https://user-images.githubusercontent.com/39759830/72153230-9a576900-33ad-11ea-99e2-6fc772c37288.gif)

References:
  * [editor PR #3174](https://github.com/livingdocsIO/livingdocs-editor/pull/3174)


## Login into a Specific Project :tada:

There are 2 new improvements:
- After a login the editor routes the user to the last opened project.
- It's now possible to login into a specific project with `<your-editor-url>/login/:projectHandle`

References:
  * [editor PR #3085](https://github.com/livingdocsIO/livingdocs-editor/pull/3085)


# Breaking Changes :fire:

## Migrate the database

The migration is simple, the duration is short and there are no datalosses expected on up-/downgrade.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 128-add-user-agent-access-tokens.js
#   add field access_tokens.user_agent
# migration - 129-add-index-user-id-created-at-access-tokens.js
#   add index to access_tokens.user_id | access_tokens.created_at
# migration - 129-add-index-user-id-created-at-access-tokens.js
#   add index to access_tokens.user_id | access_tokens.created_at

livingdocs-server migrate up
```

## Minimum node and npm version updated :fire:

Due to security reasons, we are bumping node and npm minimum requirements

- minimum node requirement: >= `node@10.13.0`
- minimum NPM requirement: >= `npm@6.13.4`

References:
  * [livingdocs-editor #3134](https://github.com/livingdocsIO/livingdocs-editor/pull/3134)


## Context Object for include API :fire:

-------------> TODO Gabriel/Ralph/Marc: overhaul implementation/documentation <----------------------------------------------------------------------

References:
  * [server PR #2783](https://github.com/livingdocsIO/livingdocs-server/pull/2783) :gift:


# APIs :gift:

## Public API - fetch a design - `api/v1/design/:designVersion`

It's now possible to fetch a design configuration via Public API.

References: 
  * [Public API Documentation](https://edit.livingdocs.io/public-api)
  * [server PR #2617](https://github.com/livingdocsIO/livingdocs-server/pull/2617)

## CoreAPI - Dashboard List Filter :tada:

We introduced a Dashboard List Filter named `List Filter v2`. 

This filter has 2 advantages over `List Filter`:
- Fetch the data asynchronous (instead of synchronous)
- Be able to compose the filter with injected data like `project`, `user`, `server`

References:
  * [Dashboard List Filter (deprecated)](https://docs.livingdocs.io/reference-documentation/editor/menu-and-dashboards#register-custom-list-filter)
  * [Dashboard List Filter v2](https://docs.livingdocs.io/reference-documentation/editor/menu-and-dashboards#register-custom-list-v2-filter)
  * [editor PR #3213](https://github.com/livingdocsIO/livingdocs-editor/pull/3213)


# Other Changes

### Features
* Login: New device detection on login [livingdocs-server #2663](https://github.com/livingdocsIO/livingdocs-server/pull/2663) :gift:
* Design: Make defaultContent editable in a design v2 [livingdocs-editor #3192](https://github.com/livingdocsIO/livingdocs-editor/pull/3192) :gift:

### Design
* Dashboards: Overhaul design dashboards [livingdocs-editor #3124](https://github.com/livingdocsIO/livingdocs-editor/pull/3124) :gift:
* Design Bump: Correctly collapse for mobile and tablet [livingdocs-editor #3175](https://github.com/livingdocsIO/livingdocs-editor/pull/3175) :gift:

### Improvements
* Data Migration: Fix the behaviour of the date filter [livingdocs-server #2730](https://github.com/livingdocsIO/livingdocs-server/pull/2730) :beetle:
* Images: Improve error message on image upload when `imagemagick` is missing [livingdocs-server #2667](https://github.com/livingdocsIO/livingdocs-server/pull/2667) :gift:
* Reindexing
  * Add delay when elastic CPU passes threshold [livingdocs-server #2702](https://github.com/livingdocsIO/livingdocs-server/pull/2702) :gift:
  * Allow to reindex by `contentType` or `documentType` [livingdocs-server #2738](https://github.com/livingdocsIO/livingdocs-server/pull/2738) :gift:
* Collaboration
  * Hide collaboration top-bar without another user [livingdocs-editor #3105](https://github.com/livingdocsIO/livingdocs-editor/pull/3105) :gift:
  * Improve save state, messages and more [livingdocs-editor #3109](https://github.com/livingdocsIO/livingdocs-editor/pull/3109) :gift:
  * Improve logs and messages [livingdocs-editor #3144](https://github.com/livingdocsIO/livingdocs-editor/pull/3144) :gift:
  * Lock image component when another user is on the crop screen [livingdocs-editor #3176](https://github.com/livingdocsIO/livingdocs-editor/pull/3176) :gift:
  * Disable soft-lock during editing [livingdocs-editor #3191](https://github.com/livingdocsIO/livingdocs-editor/pull/3191) :gift:
  * Always update metadata on publish screen [livingdocs-editor #3204](https://github.com/livingdocsIO/livingdocs-editor/pull/3204) :gift:
  * On document update errors, show sticky message and go into read-only [livingdocs-editor #3234](https://github.com/livingdocsIO/livingdocs-editor/pull/3234) :gift:
* Login: Allow redirects to outside angular app if on the same origin [livingdocs-editor #3141](https://github.com/livingdocsIO/livingdocs-editor/pull/3141) :gift:
* Document: don't emit pusher event during init[livingdocs-editor #3252](https://github.com/livingdocsIO/livingdocs-editor/pull/3252) :gift:

### Bugfixes

* Project Setup: Always use the downstream server (as intended) [livingdocs-server #2681](https://github.com/livingdocsIO/livingdocs-server/pull/2681) :beetle:
* User: Allow users to correctly change their data [livingdocs-server #2683](https://github.com/livingdocsIO/livingdocs-server/pull/2683) :beetle:
* Data Migration: Validate `livingdoc` after and not before a file migration [livingdocs-server #2740](https://github.com/livingdocsIO/livingdocs-server/pull/2740) :beetle:
* Channel Config: Always reject an empty `channelConfig` [livingdocs-server #2767](https://github.com/livingdocsIO/livingdocs-server/pull/2767) :beetle:
* History: Restore revisions to work again [livingdocs-editor #3108](https://github.com/livingdocsIO/livingdocs-editor/pull/3108) :beetle:
* Metadata
  * Fix ResultOutdated errors for `reference-lists` [livingdocs-editor #3185](https://github.com/livingdocsIO/livingdocs-editor/pull/3185) :beetle:
  * Update `ldPrintMetadata` correctly [livingdocs-editor #3183](https://github.com/livingdocsIO/livingdocs-editor/pull/3183) :beetle:
  * Add mimeType to metadata images [livingdocs-editor #3198](https://github.com/livingdocsIO/livingdocs-editor/pull/3198) :beetle:
* Embeds: Remove and load all embeds on setup interactive view [livingdocs-editor #3188](https://github.com/livingdocsIO/livingdocs-editor/pull/3188) :beetle:
* Print Preview
  * Do show print preview correct again [livingdocs-editor #3203](https://github.com/livingdocsIO/livingdocs-editor/pull/3203) :beetle:
  * Various fixes for the print preview [livingdocs-editor #3224](https://github.com/livingdocsIO/livingdocs-editor/pull/3224) :beetle:
* Editing: on read-only don't show insert side-panel [livingdocs-editor #3226](https://github.com/livingdocsIO/livingdocs-editor/pull/3226) :beetle:
* Document update: after a design bump reload the editor [livingdocs-editor #3242](https://github.com/livingdocsIO/livingdocs-editor/pull/3242) :beetle:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
