
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
------------ EDITOR ---------------

UX
* Add titles to most pages [livingdocs-editor #2400](https://github.com/livingdocsIO/livingdocs-editor/pull/2400) :gift:
* Reorganize toolbar action css to fix paddings [livingdocs-editor #2395](https://github.com/livingdocsIO/livingdocs-editor/pull/2395) :gift:

Doc
* Brush up our public documentation [livingdocs-editor #2392](https://github.com/livingdocsIO/livingdocs-editor/pull/2392) :gift:

Features
* Copy Component - MVP [livingdocs-editor #2312](https://github.com/livingdocsIO/livingdocs-editor/pull/2312) :gift:

Comment
* Fix comment replies after deleting a comment [livingdocs-editor #2398](https://github.com/livingdocsIO/livingdocs-editor/pull/2398) :gift:
* Highlight comments [livingdocs-editor #2301](https://github.com/livingdocsIO/livingdocs-editor/pull/2301) :gift:


* add qa for metadata plugins [livingdocs-editor #2393](https://github.com/livingdocsIO/livingdocs-editor/pull/2393) :gift:
* Create new article and page types with the same components as the example ones [livingdocs-editor #2389](https://github.com/livingdocsIO/livingdocs-editor/pull/2389) :gift:
* Update living-times design to 0.0.14 [livingdocs-editor #2388](https://github.com/livingdocsIO/livingdocs-editor/pull/2388) :gift:
* feat: add delete button to content type menu in project settings [livingdocs-editor #2216](https://github.com/livingdocsIO/livingdocs-editor/pull/2216) :gift:
* Support Usersnap [livingdocs-editor #2387](https://github.com/livingdocsIO/livingdocs-editor/pull/2387) :gift:
* Redirect on email signup [livingdocs-editor #2384](https://github.com/livingdocsIO/livingdocs-editor/pull/2384) :gift:
* Update trackjs to the latest version 🚀 [livingdocs-editor #2380](https://github.com/livingdocsIO/livingdocs-editor/pull/2380) :gift:
* Update fastify-webpack-hmr to the latest version 🚀 [livingdocs-editor #2373](https://github.com/livingdocsIO/livingdocs-editor/pull/2373) :gift:
* Show links to kibana usage statistics [livingdocs-editor #2382](https://github.com/livingdocsIO/livingdocs-editor/pull/2382) :gift:
* pass terms acceptance to server [livingdocs-editor #2379](https://github.com/livingdocsIO/livingdocs-editor/pull/2379) :gift:
* don’t show filtered users [livingdocs-editor #2378](https://github.com/livingdocsIO/livingdocs-editor/pull/2378) :gift:
* fix handle conflict of seeding [livingdocs-editor #2377](https://github.com/livingdocsIO/livingdocs-editor/pull/2377) :gift:
* Remove request for title when useAsTitle is set to a metadata property [livingdocs-editor #2375](https://github.com/livingdocsIO/livingdocs-editor/pull/2375) :gift:
* Improve server admin screens [livingdocs-editor #2372](https://github.com/livingdocsIO/livingdocs-editor/pull/2372) :gift:
* Add flag to disable editing the document title at the toolbar [livingdocs-editor #2370](https://github.com/livingdocsIO/livingdocs-editor/pull/2370) :gift:
* Show content type of an old revision in history [livingdocs-editor #2366](https://github.com/livingdocsIO/livingdocs-editor/pull/2366) :gift:
* Make sign-up responsive [livingdocs-editor #2360](https://github.com/livingdocsIO/livingdocs-editor/pull/2360) :gift:
* Fix of create print article [livingdocs-editor #2363](https://github.com/livingdocsIO/livingdocs-editor/pull/2363) :gift:
* No check for id for an active filter [livingdocs-editor #2364](https://github.com/livingdocsIO/livingdocs-editor/pull/2364) :gift:
* Fix multiselect [livingdocs-editor #2362](https://github.com/livingdocsIO/livingdocs-editor/pull/2362) :gift:
* Configure imageRatios in li-image metadata form [livingdocs-editor #2238](https://github.com/livingdocsIO/livingdocs-editor/pull/2238) :gift:
* Fix service signup [livingdocs-editor #2328](https://github.com/livingdocsIO/livingdocs-editor/pull/2328) :gift:


* Integrate Semantic Release Status Call on Travis [livingdocs-editor #2350](https://github.com/livingdocsIO/livingdocs-editor/pull/2350) :gift:
* Exclude HotModuleReplacementPlugin from production build [livingdocs-editor #2344](https://github.com/livingdocsIO/livingdocs-editor/pull/2344) :gift:
* feat(modal): Support Escape key to close modal windows [livingdocs-editor #2336](https://github.com/livingdocsIO/livingdocs-editor/pull/2336) :gift:
* Fix webpack build loop triggered by changes in dist directory [livingdocs-editor #2337](https://github.com/livingdocsIO/livingdocs-editor/pull/2337) :gift:
* fix(content types): Link icon [livingdocs-editor #2335](https://github.com/livingdocsIO/livingdocs-editor/pull/2335) :gift:
* Don't Show History Restore Option with a different content type [livingdocs-editor #2332](https://github.com/livingdocsIO/livingdocs-editor/pull/2332) :gift:
* Document History: Return “Today” instead of hours [livingdocs-editor #2330](https://github.com/livingdocsIO/livingdocs-editor/pull/2330) :gift:
* Update assets-webpack-plugin to the latest version 🚀 [livingdocs-editor #2316](https://github.com/livingdocsIO/livingdocs-editor/pull/2316) :gift:
* Design component library [livingdocs-editor #2318](https://github.com/livingdocsIO/livingdocs-editor/pull/2318) :gift:
* Update fastify-webpack-hmr to the latest version 🚀 [livingdocs-editor #2324](https://github.com/livingdocsIO/livingdocs-editor/pull/2324) :gift:
* Update serialize-error to the latest version 🚀 [livingdocs-editor #2323](https://github.com/livingdocsIO/livingdocs-editor/pull/2323) :gift:
* Update style-loader to the latest version 🚀 [livingdocs-editor #2322](https://github.com/livingdocsIO/livingdocs-editor/pull/2322) :gift:
* Fix readonly authorization [livingdocs-editor #2317](https://github.com/livingdocsIO/livingdocs-editor/pull/2317) :gift:
* Fix link popover in Safari [livingdocs-editor #2310](https://github.com/livingdocsIO/livingdocs-editor/pull/2310) :gift:
* Fix: immediately save when trying to go to the dashboard [livingdocs-editor #2314](https://github.com/livingdocsIO/livingdocs-editor/pull/2314) :gift:
* Use ng-readonly instead of ng-disabled in content type configuration forms [livingdocs-editor #2311](https://github.com/livingdocsIO/livingdocs-editor/pull/2311) :gift:
* Read comments from mock [livingdocs-editor #2236](https://github.com/livingdocsIO/livingdocs-editor/pull/2236) :gift:
* Fix the debounce of the list search [livingdocs-editor #2307](https://github.com/livingdocsIO/livingdocs-editor/pull/2307) :gift:
* fix(editor): Titles [livingdocs-editor #2305](https://github.com/livingdocsIO/livingdocs-editor/pull/2305) :gift:
* Fix tooltips [livingdocs-editor #2303](https://github.com/livingdocsIO/livingdocs-editor/pull/2303) :gift:
* Fix the version.json fallback interval [livingdocs-editor #2300](https://github.com/livingdocsIO/livingdocs-editor/pull/2300) :gift:
* Add link to cypress howto [livingdocs-editor #2299](https://github.com/livingdocsIO/livingdocs-editor/pull/2299) :gift:
* Remove `file:` declaration in package.json, something i… [livingdocs-editor #2298](https://github.com/livingdocsIO/livingdocs-editor/pull/2298) :gift:
* Replace webpack-dev-server with a custom node server [livingdocs-editor #2264](https://github.com/livingdocsIO/livingdocs-editor/pull/2264) :gift:
* Get webpack build to work again after they accidentally broke compatibility with webpack-cli [livingdocs-editor #2290](https://github.com/livingdocsIO/livingdocs-editor/pull/2290) :gift:
* Bump minor version to v34.5.0 for release management [livingdocs-editor #2288](https://github.com/livingdocsIO/livingdocs-editor/pull/2288) :gift:




------------ SERVER ---------------
* Bump minor version to 75.10.0 for release management [livingdocs-server #2162](https://github.com/livingdocsIO/livingdocs-server/pull/2162) :gift:
* Update framework to 11.2.0 [livingdocs-server #2163](https://github.com/livingdocsIO/livingdocs-server/pull/2163) :gift:
* Comments [livingdocs-server #2139](https://github.com/livingdocsIO/livingdocs-server/pull/2139) :gift:
* Update living-times design to 0.0.14 [livingdocs-server #2154](https://github.com/livingdocsIO/livingdocs-server/pull/2154) :gift:
* update seed design [livingdocs-server #2153](https://github.com/livingdocsIO/livingdocs-server/pull/2153) :gift:
* Update design server [livingdocs-server #2152](https://github.com/livingdocsIO/livingdocs-server/pull/2152) :gift:
* Auto-login existing SSO users [livingdocs-server #2149](https://github.com/livingdocsIO/livingdocs-server/pull/2149) :gift:
* Include filtered users in response [livingdocs-server #2146](https://github.com/livingdocsIO/livingdocs-server/pull/2146) :gift:
* Fix handle conflict in project seeding [livingdocs-server #2145](https://github.com/livingdocsIO/livingdocs-server/pull/2145) :gift:
* Fix the comparison of elasticsearch mappings on sequential runs [livingdocs-server #2143](https://github.com/livingdocsIO/livingdocs-server/pull/2143) :gift:
* Improve server admin screens [livingdocs-server #2134](https://github.com/livingdocsIO/livingdocs-server/pull/2134) :gift:
* Integrate Semantic Release Status Call on Travis [livingdocs-server #2135](https://github.com/livingdocsIO/livingdocs-server/pull/2135) :gift:
* Add property disableEditTitleAtToolbar to the contentType config [livingdocs-server #2140](https://github.com/livingdocsIO/livingdocs-server/pull/2140) :gift:
* Bump framework 11.0.4 -> 11.1.2 [livingdocs-server #2138](https://github.com/livingdocsIO/livingdocs-server/pull/2138) :gift:
* Fix service signup [livingdocs-server #2128](https://github.com/livingdocsIO/livingdocs-server/pull/2128) :gift:
* Pass data.layout property by default at /revisions [livingdocs-server #2131](https://github.com/livingdocsIO/livingdocs-server/pull/2131) :gift:
* Fix document routes checker, second issue [livingdocs-server #2126](https://github.com/livingdocsIO/livingdocs-server/pull/2126) :gift:
* Bring document route checker up to date with newest routing change [livingdocs-server #2124](https://github.com/livingdocsIO/livingdocs-server/pull/2124) :gift:
* Bump core-server-includes to v0.0.3 [livingdocs-server #2122](https://github.com/livingdocsIO/livingdocs-server/pull/2122) :gift:
* e2e setup for auth tests [livingdocs-server #2120](https://github.com/livingdocsIO/livingdocs-server/pull/2120) :gift:
* Fix unpublish route [livingdocs-server #2085](https://github.com/livingdocsIO/livingdocs-server/pull/2085) :gift:
* Bump minor version to v75.3.0 for release management [livingdocs-server #2116](https://github.com/livingdocsIO/livingdocs-server/pull/2116) :gift:
  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
