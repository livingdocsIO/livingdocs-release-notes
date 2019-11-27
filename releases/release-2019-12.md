
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

## EXAMPLE !!!!!!!!!!!!!!!!!!! Editor Multiselect :gift:
Add multiselect functionality to the editor. In multiselect mode when a component is clicked this component is added to the selection. When a component is clicked again it is removed from the selection. In the sidebar the count of selected components is shown and there is the option to delete all selected components.
Required editor configuration to enable the multiselect feature:
```js
keyboardShortcuts: {
      '↓shift': 'start multiselect mode',
      '↑shift': 'end multiselect mode'
}
```

You can read more about the feature in the references section.

* References
  * [editor PR #2143](https://github.com/livingdocsIO/livingdocs-editor/pull/2143)
  * [documentation](https://github.com/livingdocsIO/livingdocs/pull/246)


# Breaking Changes :fire:

## Migrate the database

```sh
# run grunt migrate to update to the newest database scheme
# migration - 111-add-comments-table.js
#   create comments table + add events to the stream_events_types table
livingdocs-server migrate up
```


## EXAMPLE !!!!!!!!!!!!!!!!!!! Update Elasticsearch Index

We now only store the reference to a user (`userId`) instead of the whole `user` object in Elasticsearch...

### Changes
These properties were added/deprecated from the document index...
- :fire: deprecated `last_publication`
- :fire: removed `last_publication`
- :heavy_plus_sign: added `last_publication`
- :heavy_minus_sign: removed `last_publication`
- :recycle: refactored `last_publication`

### Needed Actions :fire:
- :fire: Check and update your code to not use deprecated fields
- :fire: The mapping should update automatically during server start. If indexing fails for some reason, please run grunt `search-index:documents:update-mapping`
- optionally reindex calling `livingdocs-server search-index`

**Example**

```js
// Before
const registrationApi = liServer.features.api('li-registration')
registrationApi.registerProjectBuilder({
  handle: 'awesome-project',
  builder: ({userId}, builderConfig, callback) => {
    buildMyAwesomeProject({userId}, builderConfig, callback)
  }
})

// Now
const projectBuildersApi = liServer.features.api('li-project-builders')
projectBuildersApi.registerBuilder({
  handle: 'awesome-project',
  async builder ({userId}, builderConfig) {
    const project = await buildMyAwesomeProject({userId}, builderConfig)
    return project
  }
})
```

* References
  * [server PR #2426](https://github.com/livingdocsIO/livingdocs-server/pull/2426)




# Other Changes

* Features
  * ... :gift:
* Chore
  * ... :wrench:
* Bugfixes
  * ... :beetle:
* Service
  * ...







EDITOR
----------------------------
* v42.9.0 Realtime collab [livingdocs-editor #3018](https://github.com/livingdocsIO/livingdocs-editor/pull/3018) :gift:
* v42.8.3 Cli support [livingdocs-editor #3099](https://github.com/livingdocsIO/livingdocs-editor/pull/3099) :gift:
* v42.8.2 Print preview robustify step zooming and optional config to disable it [livingdocs-editor #3098](https://github.com/livingdocsIO/livingdocs-editor/pull/3098) :gift:
* v42.8.1 New commit to test the gh-token [livingdocs-editor #3096](https://github.com/livingdocsIO/livingdocs-editor/pull/3096) :gift:
* v42.8.0 Support groups in the metadata screen [livingdocs-editor #3087](https://github.com/livingdocsIO/livingdocs-editor/pull/3087) :gift:
* v42.7.1 Show when a design was not able to load [livingdocs-editor #3079](https://github.com/livingdocsIO/livingdocs-editor/pull/3079) :gift:
* v42.7.0 Feature: design migration via UI [livingdocs-editor #2811](https://github.com/livingdocsIO/livingdocs-editor/pull/2811) :gift:
* v42.6.3 Advanced Dropdown [livingdocs-editor #3083](https://github.com/livingdocsIO/livingdocs-editor/pull/3083) :gift:
* v42.6.2 Don't assert on document violations [livingdocs-editor #3075](https://github.com/livingdocsIO/livingdocs-editor/pull/3075) :gift:
* v42.6.1 Do not show print preview loading screen in publishing screen [livingdocs-editor #3068](https://github.com/livingdocsIO/livingdocs-editor/pull/3068) :gift:
* v42.6.0 category filter [livingdocs-editor #3074](https://github.com/livingdocsIO/livingdocs-editor/pull/3074) :gift:
* v42.5.0 feat(hugo-drag-and-drop): Map huGO text fields to image directives [livingdocs-editor #3063](https://github.com/livingdocsIO/livingdocs-editor/pull/3063) :gift:
* v42.4.8 remove .droneci.yml [livingdocs-editor #3062](https://github.com/livingdocsIO/livingdocs-editor/pull/3062) :gift:
* v42.4.7 Use new wait-for-services script [livingdocs-editor #3073](https://github.com/livingdocsIO/livingdocs-editor/pull/3073) :gift:
* v42.4.6 Improvements for filter sets [livingdocs-editor #3058](https://github.com/livingdocsIO/livingdocs-editor/pull/3058) :gift:
* v42.4.5 fix: correctly update password confirmation form [livingdocs-editor #3066](https://github.com/livingdocsIO/livingdocs-editor/pull/3066) :gift:
* v42.4.4 Metadata image cropping: guard out of bounds error [livingdocs-editor #3061](https://github.com/livingdocsIO/livingdocs-editor/pull/3061) :gift:
* v42.4.3 Add new metadata icons [livingdocs-editor #3057](https://github.com/livingdocsIO/livingdocs-editor/pull/3057) :gift:
* v42.4.2 Safeguard access to `profile` [livingdocs-editor #3056](https://github.com/livingdocsIO/livingdocs-editor/pull/3056) :gift:
* v42.4.1 Icons [livingdocs-editor #3055](https://github.com/livingdocsIO/livingdocs-editor/pull/3055) :gift:
* v42.4.0 Allow restoring archived documents [livingdocs-editor #3021](https://github.com/livingdocsIO/livingdocs-editor/pull/3021) :gift:
* v42.3.0 Fix user sorting on the admin screen [livingdocs-editor #3052](https://github.com/livingdocsIO/livingdocs-editor/pull/3052) :gift:
* v42.2.0 Make Desk-Net integration service ready [livingdocs-editor #3041](https://github.com/livingdocsIO/livingdocs-editor/pull/3041) :gift:
* v42.1.1 fix(server-admin-users-ui): correctly sort users [livingdocs-editor #3035](https://github.com/livingdocsIO/livingdocs-editor/pull/3035) :gift:
* v42.1.0 Add extra comments indicator in the toolbar [livingdocs-editor #3039](https://github.com/livingdocsIO/livingdocs-editor/pull/3039) :gift:
* v42.0.7 Fix iframely web teaser [livingdocs-editor #3044](https://github.com/livingdocsIO/livingdocs-editor/pull/3044) :gift:
* v42.0.6 Do not send a customized Accept header when api.version isn't defined [livingdocs-editor #3038](https://github.com/livingdocsIO/livingdocs-editor/pull/3038) :gift:
* v42.0.5 Add autocomplete attributes to login forms and some fixes [livingdocs-editor #3034](https://github.com/livingdocsIO/livingdocs-editor/pull/3034) :gift:
* v42.0.4 show correct components in component list [livingdocs-editor #3031](https://github.com/livingdocsIO/livingdocs-editor/pull/3031) :gift:
* v42.0.3 Bump livingdocs framework [livingdocs-editor #3029](https://github.com/livingdocsIO/livingdocs-editor/pull/3029) :gift:
* v42.0.2 Profile Dropdown [livingdocs-editor #3026](https://github.com/livingdocsIO/livingdocs-editor/pull/3026) :gift:
* v42.0.1 Setup History [livingdocs-editor #3020](https://github.com/livingdocsIO/livingdocs-editor/pull/3020) :gift:
* v42.0.0 Introduce Draft and DraftStorage to Workspace [livingdocs-editor #2927](https://github.com/livingdocsIO/livingdocs-editor/pull/2927) :gift:
* v41.15.11 Highlight proofreading components correctly after restarting [livingdocs-editor #2946](https://github.com/livingdocsIO/livingdocs-editor/pull/2946) :gift:
* v41.15.10 Fix http proxy v3 [livingdocs-editor #3019](https://github.com/livingdocsIO/livingdocs-editor/pull/3019) :gift:
* v41.15.8 Support http proxies in the proxy feature [livingdocs-editor #3016](https://github.com/livingdocsIO/livingdocs-editor/pull/3016) :gift:
* v41.15.7 Allow proper loading of multiple users [livingdocs-editor #3007](https://github.com/livingdocsIO/livingdocs-editor/pull/3007) :gift:
* v41.15.6 Categories: use endpoint with user permission [livingdocs-editor #3008](https://github.com/livingdocsIO/livingdocs-editor/pull/3008) :gift:
* v41.15.5 Fix document lock issue caused by mutations of the document on the server [livingdocs-editor #3009](https://github.com/livingdocsIO/livingdocs-editor/pull/3009) :gift:
* v41.15.4 Feat history sidebar extensions [livingdocs-editor #2862](https://github.com/livingdocsIO/livingdocs-editor/pull/2862) :gift:
* v41.15.3 Fix Editing and Cropping with Multiple Metadata Images [livingdocs-editor #3003](https://github.com/livingdocsIO/livingdocs-editor/pull/3003) :gift:
* v41.15.2 Ensure inexistent users have a UserPreview object [livingdocs-editor #2996](https://github.com/livingdocsIO/livingdocs-editor/pull/2996) :gift:
* v41.15.1 Various fixes to improve the service home screen [livingdocs-editor #2997](https://github.com/livingdocsIO/livingdocs-editor/pull/2997) :gift:
* v41.15.0 Realign not supported browsers [livingdocs-editor #2981](https://github.com/livingdocsIO/livingdocs-editor/pull/2981) :gift:
* v41.14.0 allow to impersonate users [livingdocs-editor #2983](https://github.com/livingdocsIO/livingdocs-editor/pull/2983) :gift:
* v41.13.1 Migrate to the newer dependency injection syntax [livingdocs-editor #2982](https://github.com/livingdocsIO/livingdocs-editor/pull/2982) :gift:
* v41.13.0 Server admins can now reactivate archived users [livingdocs-editor #2977](https://github.com/livingdocsIO/livingdocs-editor/pull/2977) :gift:
* v41.12.1 Update monaco-editor to the latest version 🚀 [livingdocs-editor #2961](https://github.com/livingdocsIO/livingdocs-editor/pull/2961) :gift:
* v41.12.0 Server Admins can create users with an optional lifespan  [livingdocs-editor #2967](https://github.com/livingdocsIO/livingdocs-editor/pull/2967) :gift:
* v41.11.0 Make editor settings of the channel config editable [livingdocs-editor #2972](https://github.com/livingdocsIO/livingdocs-editor/pull/2972) :gift:
* v41.10.6 Fix last publication date on search result [livingdocs-editor #2962](https://github.com/livingdocsIO/livingdocs-editor/pull/2962) :gift:
* v41.10.5 🔐Security and config fixes [livingdocs-editor #2957](https://github.com/livingdocsIO/livingdocs-editor/pull/2957) :gift:
* v41.10.4 Fix Design Modal in Component Library [livingdocs-editor #2956](https://github.com/livingdocsIO/livingdocs-editor/pull/2956) :gift:
* v41.10.3 fix(revision): Spacing [livingdocs-editor #2915](https://github.com/livingdocsIO/livingdocs-editor/pull/2915) :gift:
* v41.10.2 Fix import design config [livingdocs-editor #2951](https://github.com/livingdocsIO/livingdocs-editor/pull/2951) :gift:
* v41.10.1 Fix webpack config lookup [livingdocs-editor #2952](https://github.com/livingdocsIO/livingdocs-editor/pull/2952) :gift:
* v41.10.0 Bump minor version to 41.10.0 for release management [livingdocs-editor #2949](https://github.com/livingdocsIO/livingdocs-editor/pull/2949) :gift:



SERVER
-----------------------------------------
* v91.0.0 Improve livingdocs-server tasks (help/names/arguments) [livingdocs-server #2284](https://github.com/livingdocsIO/livingdocs-server/pull/2284) :gift:
* v90.2.1 Update @livingdocs/framework to the latest version 🚀 [livingdocs-server #2664](https://github.com/livingdocsIO/livingdocs-server/pull/2664) :gift:
* v90.2.0 Channel config drafts [livingdocs-server #2540](https://github.com/livingdocsIO/livingdocs-server/pull/2540) :gift:
* v90.1.3 fix: test fix [livingdocs-server #2662](https://github.com/livingdocsIO/livingdocs-server/pull/2662) :gift:
* v90.1.2 Allow image imports to pass metadata to DAM [livingdocs-server #2659](https://github.com/livingdocsIO/livingdocs-server/pull/2659) :gift:
* v90.1.1 Add archived flag to category channel-config schema [livingdocs-server #2658](https://github.com/livingdocsIO/livingdocs-server/pull/2658) :gift:
* v90.1.0 Migrate callback based apis to promises [livingdocs-server #2640](https://github.com/livingdocsIO/livingdocs-server/pull/2640) :gift:
* v90.0.5 Fix indexingApi.addJob promise handling when not running tests [livingdocs-server #2653](https://github.com/livingdocsIO/livingdocs-server/pull/2653) :gift:
* v90.0.4 The feature li-migration is a dependency of li-channel-configs [livingdocs-server #2652](https://github.com/livingdocsIO/livingdocs-server/pull/2652) :gift:
* v90.0.3 Increase timeout for tests [livingdocs-server #2651](https://github.com/livingdocsIO/livingdocs-server/pull/2651) :gift:
* v90.0.2 Remove invalid channel property in the e2e-seeding [livingdocs-server #2650](https://github.com/livingdocsIO/livingdocs-server/pull/2650) :gift:
* v90.0.1 Add metadata groups to service seeding [livingdocs-server #2648](https://github.com/livingdocsIO/livingdocs-server/pull/2648) :gift:
* v90.0.0 Remove functions and properties from the channelApi [livingdocs-server #2632](https://github.com/livingdocsIO/livingdocs-server/pull/2632) :gift:
* v89.5.0 Feature: design migration (automatic via config flag) [livingdocs-server #2471](https://github.com/livingdocsIO/livingdocs-server/pull/2471) :gift:
* v89.4.3 Fix create-admin-users task [livingdocs-server #2649](https://github.com/livingdocsIO/livingdocs-server/pull/2649) :gift:
* v89.4.2 Only seed e2e setup in the cypress environment [livingdocs-server #2647](https://github.com/livingdocsIO/livingdocs-server/pull/2647) :gift:
* v89.4.1 Point to the correct default branch in livingdocs-integration.json [livingdocs-server #2646](https://github.com/livingdocsIO/livingdocs-server/pull/2646) :gift:
* v89.4.0 User invites MVP [livingdocs-server #2641](https://github.com/livingdocsIO/livingdocs-server/pull/2641) :gift:
* v89.3.6 Improve the description of the database command [livingdocs-server #2642](https://github.com/livingdocsIO/livingdocs-server/pull/2642) :gift:
* v89.3.5 fix: disable hugo feature if config is missing [livingdocs-server #2636](https://github.com/livingdocsIO/livingdocs-server/pull/2636) :gift:
* v89.3.4 Use new deserialization handling [livingdocs-server #2637](https://github.com/livingdocsIO/livingdocs-server/pull/2637) :gift:
* v89.3.3 Return 410 - Gone for removed projects [livingdocs-server #2622](https://github.com/livingdocsIO/livingdocs-server/pull/2622) :gift:
* v89.3.2 Add categories to e2e seeding [livingdocs-server #2635](https://github.com/livingdocsIO/livingdocs-server/pull/2635) :gift:
* v89.3.1 get rid of wait-for-services.sh [livingdocs-server #2631](https://github.com/livingdocsIO/livingdocs-server/pull/2631) :gift:
* v89.3.0 feat(hugo): Expose hugo config [livingdocs-server #2627](https://github.com/livingdocsIO/livingdocs-server/pull/2627) :gift:
* v89.2.5 Validate scopes on update [livingdocs-server #2621](https://github.com/livingdocsIO/livingdocs-server/pull/2621) :gift:
* v89.2.4 re-add wait-for-services.sh [livingdocs-server #2626](https://github.com/livingdocsIO/livingdocs-server/pull/2626) :gift:
* v89.2.3 Fix Drone Test fails because of a timeout [livingdocs-server #2624](https://github.com/livingdocsIO/livingdocs-server/pull/2624) :gift:
* v89.2.2 fix(package): update @livingdocs/core-server-includes to version 0.0.7 [livingdocs-server #2620](https://github.com/livingdocsIO/livingdocs-server/pull/2620) :gift:
* v89.2.1 Fix merge users [livingdocs-server #2618](https://github.com/livingdocsIO/livingdocs-server/pull/2618) :gift:
* v89.2.0 Allow restoring archived documents [livingdocs-server #2585](https://github.com/livingdocsIO/livingdocs-server/pull/2585) :gift:
* v89.1.0 Fix category route building [livingdocs-server #2614](https://github.com/livingdocsIO/livingdocs-server/pull/2614) :gift:
* v89.0.1  Introduce error responses instead of just crashing the public api when a project doesn't exist [livingdocs-server #2607](https://github.com/livingdocsIO/livingdocs-server/pull/2607) :gift:
* v89.0.0 Remove the max length constraint on the scope column of the groups table [livingdocs-server #2606](https://github.com/livingdocsIO/livingdocs-server/pull/2606) :gift:
* v88.2.6 add new task group-add-user [livingdocs-server #2603](https://github.com/livingdocsIO/livingdocs-server/pull/2603) :gift:
* v88.2.5 Bump Framework & tests for new copy component match all flag [livingdocs-server #2584](https://github.com/livingdocsIO/livingdocs-server/pull/2584) :gift:
* v88.2.4 Fix category inheritance [livingdocs-server #2598](https://github.com/livingdocsIO/livingdocs-server/pull/2598) :gift:
* v88.2.3 Add cacheMaxAge config option [livingdocs-server #2596](https://github.com/livingdocsIO/livingdocs-server/pull/2596) :gift:
* v88.2.2 Allow to use a local design in project-setup [livingdocs-server #2595](https://github.com/livingdocsIO/livingdocs-server/pull/2595) :gift:
* v88.2.1 Use routing channel config cache only during warm up phase [livingdocs-server #2592](https://github.com/livingdocsIO/livingdocs-server/pull/2592) :gift:
* v88.2.0 Desk-Net integration [livingdocs-server #2532](https://github.com/livingdocsIO/livingdocs-server/pull/2532) :gift:
* v88.1.6 fix data-migration task [livingdocs-server #2582](https://github.com/livingdocsIO/livingdocs-server/pull/2582) :gift:
* v88.1.5 fix(tasks): exit process after transform channel task [livingdocs-server #2580](https://github.com/livingdocsIO/livingdocs-server/pull/2580) :gift:
* v88.1.2 Rename auth:namespace to auth:issuer [livingdocs-server #2576](https://github.com/livingdocsIO/livingdocs-server/pull/2576) :gift:
* v88.1.1 Fix redis setup in routing [livingdocs-server #2575](https://github.com/livingdocsIO/livingdocs-server/pull/2575) :gift:
* v88.1.0 Extend Request Log [livingdocs-server #2570](https://github.com/livingdocsIO/livingdocs-server/pull/2570) :gift:
* v88.0.1 Fix Project Membership Migration [livingdocs-server #2571](https://github.com/livingdocsIO/livingdocs-server/pull/2571) :gift:
* v88.0.0 Users can be assigned to a project, but not a group [livingdocs-server #2476](https://github.com/livingdocsIO/livingdocs-server/pull/2476) :gift:
* v87.3.0 GET channel-configs/properties endpoint [livingdocs-server #2568](https://github.com/livingdocsIO/livingdocs-server/pull/2568) :gift:
* v87.2.10 fix(categories): correct error handling in prepublish hook [livingdocs-server #2565](https://github.com/livingdocsIO/livingdocs-server/pull/2565) :gift:
* v87.2.9 Various fixes to improve the service home screen [livingdocs-server #2564](https://github.com/livingdocsIO/livingdocs-server/pull/2564) :gift:
* v87.2.8 Channel config cache polling [livingdocs-server #2555](https://github.com/livingdocsIO/livingdocs-server/pull/2555) :gift:
* v87.2.7 add pagination config for document-lists get endpoint [livingdocs-server #2560](https://github.com/livingdocsIO/livingdocs-server/pull/2560) :gift:
* v87.2.6 Fix include render options parameter [livingdocs-server #2556](https://github.com/livingdocsIO/livingdocs-server/pull/2556) :gift:
* v87.2.5 Add issuer to token if available [livingdocs-server #2553](https://github.com/livingdocsIO/livingdocs-server/pull/2553) :gift:
* v87.2.4 Support strings in feature toggles [livingdocs-server #2552](https://github.com/livingdocsIO/livingdocs-server/pull/2552) :gift:
* v87.2.3 add route to get access token [livingdocs-server #2551](https://github.com/livingdocsIO/livingdocs-server/pull/2551) :gift:
* v87.2.2 Router: minor improvements and debug logs [livingdocs-server #2550](https://github.com/livingdocsIO/livingdocs-server/pull/2550) :gift:
* v87.2.1 Fix include render [livingdocs-server #2544](https://github.com/livingdocsIO/livingdocs-server/pull/2544) :gift:
* v87.2.0 Server admins can now reactivate archived users  [livingdocs-server #2543](https://github.com/livingdocsIO/livingdocs-server/pull/2543) :gift:
* v87.1.2 Fix channel config v1 projection [livingdocs-server #2546](https://github.com/livingdocsIO/livingdocs-server/pull/2546) :gift:
* v87.1.1 Prevent multiple slashes in routing [livingdocs-server #2542](https://github.com/livingdocsIO/livingdocs-server/pull/2542) :gift:
* v87.1.0 Create users with an optional lifespan [livingdocs-server #2539](https://github.com/livingdocsIO/livingdocs-server/pull/2539) :gift:
* v87.0.0 Upgrade to node 12, drop Node 8 [livingdocs-server #2538](https://github.com/livingdocsIO/livingdocs-server/pull/2538) :gift:
* v86.0.0 Drop support for ES < 6.x [livingdocs-server #2535](https://github.com/livingdocsIO/livingdocs-server/pull/2535) :gift:
* v85.4.3 fix: correctly pass userId for copied articles [livingdocs-server #2534](https://github.com/livingdocsIO/livingdocs-server/pull/2534) :gift:
* v85.4.2 li-categroy getRoutePart() can handle an empty category [livingdocs-server #2533](https://github.com/livingdocsIO/livingdocs-server/pull/2533) :gift:
* v85.4.1 Fix race condition in channel config test [livingdocs-server #2529](https://github.com/livingdocsIO/livingdocs-server/pull/2529) :gift:
* v85.4.0 Bump minor version to 85.4.0 for release management [livingdocs-server #2527](https://github.com/livingdocsIO/livingdocs-server/pull/2527) :gift:
  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
