
**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2019-12`
`@livingdocs/editor` | `release-2019-12`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2019-12",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2019-12

### Livingdocs Server Patches
- [v91.0.1](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v91.0.0): ?



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2019-12",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2019-12

### Livingdocs Editor Patches
- [v42.9.1](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v42.9.1): ?



# Highlights


## Real Time Collaboration :tada:

-------Text from Meinrad-------

References:
  * [editor PR #3018](https://github.com/livingdocsIO/livingdocs-editor/pull/3018)


## Server and Project Administrator Improvements :tada:

For the December release we worked on several improvements for Admins. Here is a summary of the changes:

* A server admin can reactivate an archived user [#2977](https://github.com/livingdocsIO/livingdocs-editor/pull/2977) :gift:.
* A server admin can create a user with an optional lifespan [#2967](https://github.com/livingdocsIO/livingdocs-editor/pull/2967) :gift:.
* A project admin can initiate a design migration (design bump) [#2811](https://github.com/livingdocsIO/livingdocs-editor/pull/2811) :gift:.
* A project admin can invite a user which already existed in another project [#2641](https://github.com/livingdocsIO/livingdocs-server/pull/2641) :beetle:. The invitation was only possible for new users and is now fixed.

## Desk-Net Integration :tada:

We previously released a [MVP](https://github.com/livingdocsIO/livingdocs-release-notes/blob/master/releases/release-2019-07.md#desk-net-integration-tada) for the Desk-Net integration. With the December release we went from MVP to fully supported feature. 

The additions:
* Feature can be fully configured in a UI for the channel-config
* The publication sync can be configured (turned on and off)
* Desk-Net types can be mapped to Livingdocs content-types to control which content-type should be created
* Simple Desk-Net metadata values can be mapped from Desk-Net to Livingdocs
* More complicated values or even content can be mapped from Desk-net to Livingdocs via our code API: https://docs.livingdocs.io/reference-documentation/server/desknet-integration#advanced-mappings-using-transform-functions
* We added full documentation for the feature: [Desk-Net Integration - Livingdocs](https://docs.livingdocs.io/reference-documentation/server/desknet-integration)

References:
  * [Documentation](https://docs.livingdocs.io/reference-documentation/server/desknet-integration)
  * Introduction Video: https://vimeo.com/368750546
  * [editor PR I #2986](https://github.com/livingdocsIO/livingdocs-editor/pull/2986)
  * [editor PR II #3041](https://github.com/livingdocsIO/livingdocs-editor/pull/3041)


# Breaking Changes :fire:

## Migrate the database :fire:

```sh
# run grunt migrate to update to the newest database scheme
# migration - 125-add-group-member-list-table.js
#   fix the migration script for the group_project_members table
# migration - 126-migrate-scope-column-to-text.js
#   migrating the scope column on the group_projection_v3 table from a varchar(255) to a text type
# migration - 127-remove-channel-disabled-design-version.js
#   remove not used 'channel.disabled_versions' and 'channel.available_versions'
livingdocs-server migrate up
```

## Drop Support for Node 8 :fire:

All our services and customers are already using node 10, but in case you're on an old version, make sure that you're either using our base images `livingdocs/server-base:12.0` for node 12 or `livingdocs/server-base:10.0` for node 10.

References:
  * [livingdocs-server #2538](https://github.com/livingdocsIO/livingdocs-server/pull/2538)


## Drop Support for Elastic Search <6.x :fire:

Drop support for Elastic Search `< v6.x`. Please upgrade your metadata mapping and configure the server config `search.apiVersion` to `6.x`.
As reference, we've introduced Elastic Search 6 in [#2017](https://github.com/livingdocsIO/livingdocs-server/pull/2017).

References:
  * [livingdocs-server #2535](https://github.com/livingdocsIO/livingdocs-server/pull/2535)

## Removed Functions and Properties from the channelApi :fire:

The following functions are removed from the channelApi:
- :fire: channelApi.removeDesignVersion()
- :fire: channelApi.addDesignVersion()
- :fire: channelApi.enableDesignVersion()
- :fire: channelApi.disableDesignVersion()
- :fire: channelApi.isDesignEnabled()
- :fire: channelApi.isDesignVersionDisabled()
- :fire: channelApi.isDesignVersionAvailable()

The following functions are removed from the channel_model:
- :fire: channelModel.isCurrentDesignVersion()

References:
  * [livingdocs-server #2632](https://github.com/livingdocsIO/livingdocs-server/pull/2632)


## Introduce Draft and DraftStorage to Workspace :fire:

-------Text from Lukas------- need breaking change description

References:
  * [livingdocs-server #2927](https://github.com/livingdocsIO/livingdocs-editor/pull/2927)


## Show correct components in component list :fire:

-------Text from Meinrad------- need breaking change description

References:
  * [livingdocs-server #3031](https://github.com/livingdocsIO/livingdocs-editor/pull/3031)


## livingdocs-server tasks :fire:
The `livingdocs-server` commands have been overhauled.
- updated all descriptions for better comprehensibility
- renamed commands where necessary
- add `-y` flag to execute a script to make a destructive command more secure

🔥 🔥 🔥  
**When you integrate this pull request, please also search and replace the commands in your scripts/documentation/wiki**
🔥 🔥 🔥 

```
livingdocs-server database delete
- 🔥require '-y' to run the script

livingdocs-server database create
- 🔥require '-y' to run the script

livingdocs-server database create
- 🔥require '-y' to run the script

livingdocs-server search-index
- 🔥renamed from 'search-index' to 'es-search-reindex'
- 🔥require '-y' to run the script

livingdocs-server delete-document-index
- 🔥renamed from 'delete-document-index' to 'es-search-delete-index'
- 🔥require '-y' to run the script

livingdocs-server reindex-asset-index
- 🔥renamed from 'reindex-asset-index' to 'es-media-reindex'
- 🔥require '-y' to run the script

livingdocs-server delete-asset-index
- 🔥renamed from 'delete-asset-index' to 'es-media-delete-index'
- 🔥require '-y' to run the script

livingdocs-server cleanup-documents
- 🔥require '-y' to run the script
- 🔥removed '--before' parameter

livingdocs-server cleanup-migrations
- 🔥require '-y' to run the script
- 🔥removed '--before' parameter

livingdocs-server cleanup-metadata
- 🔥require '-y' to run the script

livingdocs-server setup-projects
- 🔥renamed from 'setup-projects' to 'project-seed'
- 🔥require '-y' to run the script

livingdocs-server project-delete
- 🔥require '-y' to run the script

livingdocs-server create-admin-user
- 🔥renamed from 'create-admin-user' to 'user-create-admin'
- 🔥require '-y' to run the script

livingdocs-server create-admin-users
- 🔥renamed from 'create-admin-users' to 'user-create-admins'
- 🔥renamed parameter --source to --file
- 🔥require '-y' to run the script

livingdocs-server redis-flushdb
- 🔥require '-y' to run the script

livingdocs-server project-reset
- 🔥renamed from 'project-reset' to 'project-truncate'
- 🔥require '-y' to run the script

livingdocs-server group-add-user
- 🔥renamed from 'group-add-user' to 'user-assign-group'
- 🔥require '-y' to run the script

livingdocs-server add-design
- 🔥require '-y' to run the script

livingdocs-server transform-to-configurable-channel
- 🔥require '-y' to run the script

livingdocs-server  parse-channel-config-v1-to-v2
- 🔥require '-y' to run the script
```

References:
  * Overhaul of existing commands [#2284](https://github.com/livingdocsIO/livingdocs-server/pull/2284) 
  * Add new command `npx livingdocs-server group-add-user` [#2603](https://github.com/livingdocsIO/livingdocs-server/pull/2603) :gift:

# Other Changes

### Features
* Editor: Allow restoring of archived documents [livingdocs-server #2585](https://github.com/livingdocsIO/livingdocs-server/pull/2585) :gift:
* Add category filter [livingdocs-editor #3074](https://github.com/livingdocsIO/livingdocs-editor/pull/3074) :gift:
* Feature API: Support async/await (most of the APIs) [livingdocs-server #2640](https://github.com/livingdocsIO/livingdocs-server/pull/2640) :gift:
* DevOps: Graceful shutdown of the server [livingdocs-server #2640](https://github.com/livingdocsIO/livingdocs-server/pull/2640) :gift:

### Design
* Document History: Sidebar extensions [livingdocs-editor #2862](https://github.com/livingdocsIO/livingdocs-editor/pull/2862) :gift:
* Project Setup: Improved design of channel config history [livingdocs-editor #3020](https://github.com/livingdocsIO/livingdocs-editor/pull/3020) :gift:
* Profile Dropdown: Improved design [livingdocs-editor #3026](https://github.com/livingdocsIO/livingdocs-editor/pull/3026) :gift:
* Project Setup: Advanced Channel Config Version Dropdown [livingdocs-editor #3083](https://github.com/livingdocsIO/livingdocs-editor/pull/3083) :gift:
* Toolbar: Add comments indicator [livingdocs-editor #3039](https://github.com/livingdocsIO/livingdocs-editor/pull/3039) :gift:
* Styleguide: Added new icons to the styleguide [livingdocs-editor #3055](https://github.com/livingdocsIO/livingdocs-editor/pull/3055) :gift:

### APIs
* Channel Config Drafts: add new endpoints [livingdocs-server #2540](https://github.com/livingdocsIO/livingdocs-server/pull/2540) :gift:
* Channel Config: Add 'GET channel-configs/properties' endpoint [livingdocs-server #2568](https://github.com/livingdocsIO/livingdocs-server/pull/2568) :gift:

### Improvements
* Channel Config
  * Make editor settings editable [livingdocs-editor #2972](https://github.com/livingdocsIO/livingdocs-editor/pull/2972) :gift:
  * Manage metadata groups in the metadata screen [livingdocs-editor #3087](https://github.com/livingdocsIO/livingdocs-editor/pull/3087) :gift:
  * Add cache polling options [livingdocs-server #2555](https://github.com/livingdocsIO/livingdocs-server/pull/2555) :gift:
* DAM: Allow image imports to pass metadata to DAM [livingdocs-server #2659](https://github.com/livingdocsIO/livingdocs-server/pull/2659) :gift:
* Filter Set improvements [livingdocs-editor #3058](https://github.com/livingdocsIO/livingdocs-editor/pull/3058) :gift:
* Document Copy: Copy component match all flag [livingdocs-server #2584](https://github.com/livingdocsIO/livingdocs-server/pull/2584) :gift:
* Configuration
  * Server Config: Support strings in feature toggles [livingdocs-server #2552](https://github.com/livingdocsIO/livingdocs-server/pull/2552) :gift:
  * Document Lists: Add pagination config [livingdocs-server #2560](https://github.com/livingdocsIO/livingdocs-server/pull/2560) :gift:
  * Design Loader: Add cacheMaxAge config option [livingdocs-server #2596](https://github.com/livingdocsIO/livingdocs-server/pull/2596) :gift:
* Technical
  * Tokens: Add 'issuer' to token if available [livingdocs-server #2553](https://github.com/livingdocsIO/livingdocs-server/pull/2553) :gift:
  * Browser Support: Realign not supported browsers [livingdocs-editor #2981](https://github.com/livingdocsIO/livingdocs-editor/pull/2981) :gift:
  * HTTP Proxy: Support http proxies in the proxy feature [livingdocs-editor #3016](https://github.com/livingdocsIO/livingdocs-editor/pull/3016) :gift:
  * Design: Show when a design was not able to load [livingdocs-editor #3079](https://github.com/livingdocsIO/livingdocs-editor/pull/3079) :gift:
* Public API
  * Introduce error responses instead of just crashing the public api when a project doesn't exist [livingdocs-server #2607](https://github.com/livingdocsIO/livingdocs-server/pull/2607) :gift:
  * Return '410 - Gone' for removed projects [livingdocs-server #2622](https://github.com/livingdocsIO/livingdocs-server/pull/2622) :gift:
* Routing
  * Use routing channel config cache only during warm up phase [livingdocs-server #2592](https://github.com/livingdocsIO/livingdocs-server/pull/2592) :gift:
  * Prevent multiple slashes in routing [livingdocs-server #2542](https://github.com/livingdocsIO/livingdocs-server/pull/2542) :beetle:
  * Fix redis setup [livingdocs-server #2575](https://github.com/livingdocsIO/livingdocs-server/pull/2575) :beetle:
  * Debug logs [livingdocs-server #2550](https://github.com/livingdocsIO/livingdocs-server/pull/2550) :wrench:
* Hugo
  * Expose hugo config to the editor [livingdocs-server #2627](https://github.com/livingdocsIO/livingdocs-server/pull/2627) :gift:
  * v89.3.5 fix: disable hugo feature if config is missing [livingdocs-server #2636](https://github.com/livingdocsIO/livingdocs-server/pull/2636) :beetle:
  * Map huGO text fields to image directives [livingdocs-editor #3063](https://github.com/livingdocsIO/livingdocs-editor/pull/3063) :gift:

### Bugfixes
* Categories
  * GetRoutePart() can handle an empty category [livingdocs-server #2533](https://github.com/livingdocsIO/livingdocs-server/pull/2533) :beetle:
  * Correct error handling in prepublish hook [livingdocs-server #2565](https://github.com/livingdocsIO/livingdocs-server/pull/2565) :beetle:
  * Fix category inheritance [livingdocs-server #2598](https://github.com/livingdocsIO/livingdocs-server/pull/2598) :beetle:
  * Add archived flag to category channel-config schema [livingdocs-server #2658](https://github.com/livingdocsIO/livingdocs-server/pull/2658) :beetle:
* Users
  * Project Admin: Fix merge users [livingdocs-server #2618](https://github.com/livingdocsIO/livingdocs-server/pull/2618) :beetle:
  * Server Admin: Correctly sort users [livingdocs-editor #3052](https://github.com/livingdocsIO/livingdocs-editor/pull/3052) :beetle:
  * Allow proper loading of multiple users [livingdocs-editor #3007](https://github.com/livingdocsIO/livingdocs-editor/pull/3007) :beetle:
  * Ensure inexistent users have a UserPreview object [livingdocs-editor #2996](https://github.com/livingdocsIO/livingdocs-editor/pull/2996) :beetle:
* Metadata image
  * Fix editing and cropping with multiple metadata images [livingdocs-editor #3003](https://github.com/livingdocsIO/livingdocs-editor/pull/3003) :beetle:
  * Cropping: guard out of bounds error [livingdocs-editor #3061](https://github.com/livingdocsIO/livingdocs-editor/pull/3061) :beetle:
* Iframely: Fix iframely web teaser [livingdocs-editor #3044](https://github.com/livingdocsIO/livingdocs-editor/pull/3044) :beetle:
* Document
  * Fix document lock issue caused by mutations of the document on the server [livingdocs-editor #3009](https://github.com/livingdocsIO/livingdocs-editor/pull/3009) :beetle:
* Technical
  * Fix http proxy v3 [livingdocs-editor #3019](https://github.com/livingdocsIO/livingdocs-editor/pull/3019) :beetle:
  * Safeguard access to `profile` [livingdocs-editor #3056](https://github.com/livingdocsIO/livingdocs-editor/pull/3056) :beetle:
* Registration/Login
  * Correctly update password confirmation form [livingdocs-editor #3066](https://github.com/livingdocsIO/livingdocs-editor/pull/3066) :beetle:
* Proofreading: Highlight proofreading components correctly after restarting [livingdocs-editor #2946](https://github.com/livingdocsIO/livingdocs-editor/pull/2946) :beetle:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
