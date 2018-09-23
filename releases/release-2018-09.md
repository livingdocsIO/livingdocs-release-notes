

  **Attention:** If you skipped one or more release, please also check the release-notes of the skipped ones.

  # Repositories

  This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

  Package | Version
  --- | ---
  `@livingdocs/server` | `??.?.?`
  `@livingdocs/editor` | `??.?.?`


  ## Livingdocs Server

  How to require the server in your package.json:

  ```json
  "dependencies": {
    "@livingdocs/server": "??.?.?",
  }
  ```

  - Link to the release branch:
    https://github.com/livingdocsIO/livingdocs-server/tree/release-YYYY-MM


  ## Livingdocs Editor

  How to require the editor in your package.json:

  ```json
  "dependencies": {
    "@livingdocs/editor": "??.?.?",
  }
  ```

  - Link to the release branch:
    https://github.com/livingdocsIO/livingdocs-editor/tree/release-YYYY-MM



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

  For a more detailed description check the [editor PR #2143](https://github.com/livingdocsIO/livingdocs-editor/pull/2143)

  # Breaking Changes :fire:

  ## EXAMPLE !!!!!!!!!!!!!!!!!!! Registration procedure :gift: :fire:

  There are two new flags per authentication connections: `loginEnabled` and `registrationEnabled`.
  The editor won't show the respective connection option in the login screen without them.

  Server `auth` configuration:
  ```js
  auth: {
    connections: {
      // email and password authentication
      local: {
        enabled: true,
        loginEnabled: true,
        registrationEnabled: true
        //...
      },
      github: {
        enabled: true,
        loginEnabled: false,
        registrationEnabled: false
        // ...
      }
    }
  }
  ```

   For a more detailed description check the [server PR #2010](https://github.com/livingdocsIO/livingdocs-server/pull/2010) | [editor PR #2114](https://github.com/livingdocsIO/livingdocs-editor/pull/2114)

  # Other Changes
  * Features
    * ... :gift:
  * Chore
    * ... :wrench:
  * Bugfixes
    * ... :beetle:
  * Service
    * ...



### Server  
* Indexing API and index separation [livingdocs-server #2009](https://github.com/livingdocsIO/livingdocs-server/pull/2009) :gift:
* Feat: li-integer form to be liMetaIntegerForm to liMetaTextForm [livingdocs-server #2038](https://github.com/livingdocsIO/livingdocs-server/pull/2038) :gift:
* Update release-tools to 3.0.0 [livingdocs-server #2034](https://github.com/livingdocsIO/livingdocs-server/pull/2034) :gift:
* Bump minor version to v72.6.0 for release management [livingdocs-server #2033](https://github.com/livingdocsIO/livingdocs-server/pull/2033) :gift:
* Remove unused images and document_images tables and apis [livingdocs-server #2068](https://github.com/livingdocsIO/livingdocs-server/pull/2068) :gift:
* Allow to rewrite the channel config [livingdocs-server #2066](https://github.com/livingdocsIO/livingdocs-server/pull/2066) :gift:
* feat(config): allow autoSaveInterval to be configurable [livingdocs-server #2061](https://github.com/livingdocsIO/livingdocs-server/pull/2061) :gift:
* fix(package): update @livingdocs/core-server-includes to 0.0.2 [livingdocs-server #2058](https://github.com/livingdocsIO/livingdocs-server/pull/2058) :gift:
* Integrate references [livingdocs-server #2057](https://github.com/livingdocsIO/livingdocs-server/pull/2057) :gift:
* Metadata References [livingdocs-server #2030](https://github.com/livingdocsIO/livingdocs-server/pull/2030) :gift:
* Add cleanup feature to livingdocs-server cli [livingdocs-server #2051](https://github.com/livingdocsIO/livingdocs-server/pull/2051) :gift:
* update framework to 10.4.0 [livingdocs-server #2050](https://github.com/livingdocsIO/livingdocs-server/pull/2050) :gift:
* feat: li-enum metadata plugin now supports a dataProvider config [livingdocs-server #2040](https://github.com/livingdocsIO/livingdocs-server/pull/2040) :gift:
* fix(print): adds authors and editor to print export [livingdocs-server #2037](https://github.com/livingdocsIO/livingdocs-server/pull/2037) :gift:
* Support `--reporter` option in test cli [livingdocs-server #2042](https://github.com/livingdocsIO/livingdocs-server/pull/2042) :gift:
* Added channel config publish event [livingdocs-server #2029](https://github.com/livingdocsIO/livingdocs-server/pull/2029) :gift:
* Indexing API and index separation [livingdocs-server #2009](https://github.com/livingdocsIO/livingdocs-server/pull/2009) :gift:

* Split Up Document Copy Feature to Support Main Use Cases Better [livingdocs-server #2081](https://github.com/livingdocsIO/livingdocs-server/pull/2081) :gift:
* Allow for Array in Content Type Filter [livingdocs-server #2094](https://github.com/livingdocsIO/livingdocs-server/pull/2094) :gift:
* Change the default language handle [livingdocs-server #2093](https://github.com/livingdocsIO/livingdocs-server/pull/2093) :gift:
* fix(channel-configs): extend schema for contentType.editor [livingdocs-server #2091](https://github.com/livingdocsIO/livingdocs-server/pull/2091) :gift:
* re-add author for e2e tests [livingdocs-server #2090](https://github.com/livingdocsIO/livingdocs-server/pull/2090) :gift:
* Remove old author plugin in the e2e seeding [livingdocs-server #2089](https://github.com/livingdocsIO/livingdocs-server/pull/2089) :gift:
* Support partial document include renders [livingdocs-server #2086](https://github.com/livingdocsIO/livingdocs-server/pull/2086) :gift:
* feat(admin-project-details): aggregate documents by content_type [livingdocs-server #2084](https://github.com/livingdocsIO/livingdocs-server/pull/2084) :gift:
* allow default handle set by editor [livingdocs-server #2078](https://github.com/livingdocsIO/livingdocs-server/pull/2078) :gift:
* Channel config diff improvements [livingdocs-server #2080](https://github.com/livingdocsIO/livingdocs-server/pull/2080) :gift:
* Feat: Throw a MetadataValidationError during autosave [livingdocs-server #2054](https://github.com/livingdocsIO/livingdocs-server/pull/2054) :gift:
* Upgrade framework 10.4.0 -> 11.0.2 [livingdocs-server #2075](https://github.com/livingdocsIO/livingdocs-server/pull/2075) :gift:
* Fix the compatibility of the metadata plugin property 'label' between channelConfig v1 and v2 [livingdocs-server #2073](https://github.com/livingdocsIO/livingdocs-server/pull/2073) :gift:
* Support language configuration through the editor [livingdocs-server #2071](https://github.com/livingdocsIO/livingdocs-server/pull/2071) :gift:
* Fix: li-string-list / li-numeric-list metadata plugins [livingdocs-server #2063](https://github.com/livingdocsIO/livingdocs-server/pull/2063) :gift:
* Fix channel config diff [livingdocs-server #2072](https://github.com/livingdocsIO/livingdocs-server/pull/2072) :gift:

* Fix of Hugo Article Drag & Drop [livingdocs-server #2113](https://github.com/livingdocsIO/livingdocs-server/pull/2113) :gift:
* Allow a 1:1 copy of a content-type without a copy config on the server [livingdocs-server #2099](https://github.com/livingdocsIO/livingdocs-server/pull/2099) :gift:
* Update example server [livingdocs-server #2100](https://github.com/livingdocsIO/livingdocs-server/pull/2100) :gift:
* Increase content type limit [livingdocs-server #2109](https://github.com/livingdocsIO/livingdocs-server/pull/2109) :gift:
* Fix: Always enable channel configs feature [livingdocs-server #2107](https://github.com/livingdocsIO/livingdocs-server/pull/2107) :gift:
* fix magazine setup for cypress tests [livingdocs-server #2104](https://github.com/livingdocsIO/livingdocs-server/pull/2104) :gift:
* fix(print): escaping special characters in title for hugo. Added additional metadata to print section on export to hugo [livingdocs-server #2105](https://github.com/livingdocsIO/livingdocs-server/pull/2105) :gift:
* Set CI env for cypress editor tests [livingdocs-server #2103](https://github.com/livingdocsIO/livingdocs-server/pull/2103) :gift:
* Transform Document [livingdocs-server #2092](https://github.com/livingdocsIO/livingdocs-server/pull/2092) :gift:
* fix(logging): Fix crash from logging [livingdocs-server #4377](https://github.com/nzzdev/livingdocs-api/pull/4377) :gift:


### Editor
* Metadata Editor: Client side validation [livingdocs-editor #2165](https://github.com/livingdocsIO/livingdocs-editor/pull/2165) :gift:
* Design responsive home screen [livingdocs-editor #2167](https://github.com/livingdocsIO/livingdocs-editor/pull/2167) :gift:
* Fix: li-integer metadata property service / validation [livingdocs-editor #2144](https://github.com/livingdocsIO/livingdocs-editor/pull/2144) :gift:
* Feature: Add required checkbox metadata forms [livingdocs-editor #2138](https://github.com/livingdocsIO/livingdocs-editor/pull/2138) :gift:
* Quickfix Setup Section [livingdocs-editor #2162](https://github.com/livingdocsIO/livingdocs-editor/pull/2162) :gift:
* Update release-tools to 3.0.0 [livingdocs-editor #2159](https://github.com/livingdocsIO/livingdocs-editor/pull/2159) :gift:
* Fix token mask [livingdocs-editor #2147](https://github.com/livingdocsIO/livingdocs-editor/pull/2147) :gift:
* Bump minor version to v32.4.0 for release management [livingdocs-editor #2146](https://github.com/livingdocsIO/livingdocs-editor/pull/2146) :gift:


* Fix: User can not create Print Article [livingdocs-editor #2225](https://github.com/livingdocsIO/livingdocs-editor/pull/2225) :gift:
* Configure multi-language feature [livingdocs-editor #2214](https://github.com/livingdocsIO/livingdocs-editor/pull/2214) :gift:
* Fix: string-list / numeric-list metadata types [livingdocs-editor #2206](https://github.com/livingdocsIO/livingdocs-editor/pull/2206) :gift:
* Add component properties styles to styleguide  [livingdocs-editor #2219](https://github.com/livingdocsIO/livingdocs-editor/pull/2219) :gift:
* Fix scrolling and mobile metadata [livingdocs-editor #2215](https://github.com/livingdocsIO/livingdocs-editor/pull/2215) :gift:
* This is just a test for a greenkeeper trigger [livingdocs-editor #2218](https://github.com/livingdocsIO/livingdocs-editor/pull/2218) :gift:
* feat(config): allow autoSaveInterval to be configurable [livingdocs-editor #2204](https://github.com/livingdocsIO/livingdocs-editor/pull/2204) :gift:
* Add form for li-metadata-references [livingdocs-editor #2208](https://github.com/livingdocsIO/livingdocs-editor/pull/2208) :gift:
* fix(docked content): Responsiveness [livingdocs-editor #2205](https://github.com/livingdocsIO/livingdocs-editor/pull/2205) :gift:
* Feat: hide from form checkbox for metadata properties [livingdocs-editor #2200](https://github.com/livingdocsIO/livingdocs-editor/pull/2200) :gift:
* design(content type settings): Clean-up [livingdocs-editor #2189](https://github.com/livingdocsIO/livingdocs-editor/pull/2189) :gift:
* Feat: Limit content types and metadata properties [livingdocs-editor #2184](https://github.com/livingdocsIO/livingdocs-editor/pull/2184) :gift:
* Feat: li-text form supports max-length & choosing input type (text vs textarea) [livingdocs-editor #2179](https://github.com/livingdocsIO/livingdocs-editor/pull/2179) :gift:
* Metadata References [livingdocs-editor #2141](https://github.com/livingdocsIO/livingdocs-editor/pull/2141) :gift:
* Fix dependencies requirement [livingdocs-editor #2196](https://github.com/livingdocsIO/livingdocs-editor/pull/2196) :gift:
* fix(sidebar): Scrolling [livingdocs-editor #2191](https://github.com/livingdocsIO/livingdocs-editor/pull/2191) :gift:
* Fix li enum metadata type [livingdocs-editor #2169](https://github.com/livingdocsIO/livingdocs-editor/pull/2169) :gift:
* Write in html whether the device is tablet / mobile or desktop. [livingdocs-editor #2129](https://github.com/livingdocsIO/livingdocs-planning/issues/2129) :gift:
* Fix: Project settings publish screen recognised changes when there where none [livingdocs-editor #2176](https://github.com/livingdocsIO/livingdocs-editor/pull/2176) :gift:
* Fix dynamic component [livingdocs-editor #2183](https://github.com/livingdocsIO/livingdocs-editor/pull/2183) :gift:
* fix(application menu): Top group label [livingdocs-editor #2181](https://github.com/livingdocsIO/livingdocs-editor/pull/2181) :gift:
* fix(wrappers): Scroll overflow [livingdocs-editor #2177](https://github.com/livingdocsIO/livingdocs-editor/pull/2177) :gift:
* fix(floating navi): Inactive state [livingdocs-editor #2175](https://github.com/livingdocsIO/livingdocs-editor/pull/2175) :gift:
* Design Floating Navi [livingdocs-editor #2173](https://github.com/livingdocsIO/livingdocs-editor/pull/2173) :gift:
* Introduce Content Behavior [livingdocs-editor #2170](https://github.com/livingdocsIO/livingdocs-editor/pull/2170) :gift:


* Improve the build performance [livingdocs-editor #2262](https://github.com/livingdocsIO/livingdocs-editor/pull/2262) :gift:
* Lay out password reset forms horizontally [livingdocs-editor #2259](https://github.com/livingdocsIO/livingdocs-editor/pull/2259) :gift:
* Add comment card to styleguide [livingdocs-editor #2252](https://github.com/livingdocsIO/livingdocs-editor/pull/2252) :gift:
* feat: support metadata plugin configurationUi.disableSelection [livingdocs-editor #2224](https://github.com/livingdocsIO/livingdocs-editor/pull/2224) :gift:
* Remove @babel/plugin-transform-runtime module [livingdocs-editor #2250](https://github.com/livingdocsIO/livingdocs-editor/pull/2250) :gift:
* Make language handle read-only [livingdocs-editor #2249](https://github.com/livingdocsIO/livingdocs-editor/pull/2249) :gift:
* [Styleguide] Add comment icon to editable tooltip [livingdocs-editor #2247](https://github.com/livingdocsIO/livingdocs-editor/pull/2247) :gift:
* Upgrade to chromium to v68.0.3440.106 as we require at least v 63 [livingdocs-editor #2248](https://github.com/livingdocsIO/livingdocs-editor/pull/2248) :gift:
* Fix NZZ logo styles  [livingdocs-editor #2239](https://github.com/livingdocsIO/livingdocs-editor/pull/2239) :gift:
* Fix Cypress Tests [livingdocs-editor #2242](https://github.com/livingdocsIO/livingdocs-editor/pull/2242) :gift:
* Feat/admin project details [livingdocs-editor #2237](https://github.com/livingdocsIO/livingdocs-editor/pull/2237) :gift:
* Create content-types with title and teaserImage [livingdocs-editor #2230](https://github.com/livingdocsIO/livingdocs-editor/pull/2230) :gift:
* Design viewer [livingdocs-editor #2202](https://github.com/livingdocsIO/livingdocs-editor/pull/2202) :gift:
* Fix to show a pusher error again with wrong credentials [livingdocs-editor #2234](https://github.com/livingdocsIO/livingdocs-editor/pull/2234) :gift:
* Feat: Handle metadata validation errors on autosave [livingdocs-editor #2198](https://github.com/livingdocsIO/livingdocs-editor/pull/2198) :gift:
* Improve Multiselect [livingdocs-editor #2227](https://github.com/livingdocsIO/livingdocs-editor/pull/2227) :gift:
* Upgrade framework 10.4.0 -> 11.0.0 [livingdocs-editor #2228](https://github.com/livingdocsIO/livingdocs-editor/pull/2228) :gift:


* Update @livingdocs/framework to Version 11.0.4 [livingdocs-editor #2275](https://github.com/livingdocsIO/livingdocs-editor/pull/2275) :gift:
* Transform Document [livingdocs-editor #2251](https://github.com/livingdocsIO/livingdocs-editor/pull/2251) :gift:
* Search filters [livingdocs-editor #2267](https://github.com/livingdocsIO/livingdocs-editor/pull/2267) :gift:
* Title handling [livingdocs-editor #2253](https://github.com/livingdocsIO/livingdocs-editor/pull/2253) :gift:
* Improve Menu UI [livingdocs-editor #2266](https://github.com/livingdocsIO/livingdocs-editor/pull/2266) :gift:
* Re-add accidentally removed file [livingdocs-editor #2265](https://github.com/livingdocsIO/livingdocs-editor/pull/2265) :gift:
* Get rid of subclass @extend [livingdocs-editor #2261](https://github.com/livingdocsIO/livingdocs-editor/pull/2261) :gift:



  ---

  **Icon Legend**

  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
