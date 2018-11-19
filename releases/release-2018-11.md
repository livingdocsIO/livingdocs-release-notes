
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

* Features
  * Copy Component - MVP [livingdocs-editor #2312](https://github.com/livingdocsIO/livingdocs-editor/pull/2312) :gift:


BREAKING
* Replace webpack-dev-server with a custom node server [livingdocs-editor #2264](https://github.com/livingdocsIO/livingdocs-editor/pull/2264) :gift:

Comment
* Highlight comments [livingdocs-editor #2301](https://github.com/livingdocsIO/livingdocs-editor/pull/2301) -- wait for updated PR notes --:gift:
* Comments [livingdocs-server #2139](https://github.com/livingdocsIO/livingdocs-server/pull/2139) :gift:
* --- add this to the description? --- Read comments from mock [livingdocs-editor #2236](https://github.com/livingdocsIO/livingdocs-editor/pull/2236) :gift:






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
* UX
  * Add titles to most pages [livingdocs-editor #2400](https://github.com/livingdocsIO/livingdocs-editor/pull/2400) :gift:
  * Make sign-up responsive [livingdocs-editor #2360](https://github.com/livingdocsIO/livingdocs-editor/pull/2360) :gift:
  * Design component library [livingdocs-editor #2318](https://github.com/livingdocsIO/livingdocs-editor/pull/2318) :gift:
  * Brush up our public documentation [livingdocs-editor #2392](https://github.com/livingdocsIO/livingdocs-editor/pull/2392) :gift:

* Improvements
  * Support Escape key to close modal windows [livingdocs-editor #2336](https://github.com/livingdocsIO/livingdocs-editor/pull/2336) :gift:
  * Add flag to disable editing the document title at the toolbar [livingdocs-editor #2370](https://github.com/livingdocsIO/livingdocs-editor/pull/2370)  [livingdocs-server #2140](https://github.com/livingdocsIO/livingdocs-server/pull/2140) :gift:
  * Show content type of an old revision in history [livingdocs-editor #2366](https://github.com/livingdocsIO/livingdocs-editor/pull/2366) :gift:
  * Don't Show History Restore Option with a different content type [livingdocs-editor #2332](https://github.com/livingdocsIO/livingdocs-editor/pull/2332)  [livingdocs-server #2131](https://github.com/livingdocsIO/livingdocs-server/pull/2131) :gift:
  * Document History: Return “Today” instead of hours [livingdocs-editor #2330](https://github.com/livingdocsIO/livingdocs-editor/pull/2330) :gift:
  * No check for id for an active filter [livingdocs-editor #2364](https://github.com/livingdocsIO/livingdocs-editor/pull/2364) :gift:

* Server Administration
  * Improve server admin screens [livingdocs-editor #2372](https://github.com/livingdocsIO/livingdocs-editor/pull/2372)  [livingdocs-server #2134](https://github.com/livingdocsIO/livingdocs-server/pull/2134) :wrench:
  * Show links to kibana usage statistics at the admin section [livingdocs-editor #2382](https://github.com/livingdocsIO/livingdocs-editor/pull/2382) :wrench:
  * don’t show filtered users [livingdocs-editor #2378](https://github.com/livingdocsIO/livingdocs-editor/pull/2378)  [livingdocs-server #2146](https://github.com/livingdocsIO/livingdocs-server/pull/2146)
   :wrench:

* Service
  * add delete button to content type menu in project settings [livingdocs-editor #2216](https://github.com/livingdocsIO/livingdocs-editor/pull/2216) :gift:
  * Configure imageRatios in li-image metadata form [livingdocs-editor #2238](https://github.com/livingdocsIO/livingdocs-editor/pull/2238) :gift:
  * Fix service signup [livingdocs-editor #2328](https://github.com/livingdocsIO/livingdocs-editor/pull/2328)  [livingdocs-server #2128](https://github.com/livingdocsIO/livingdocs-server/pull/2128) :gift:


* Bugfixes
  * Fix multiselect [livingdocs-editor #2362](https://github.com/livingdocsIO/livingdocs-editor/pull/2362) :beetle:
  * Fix: immediately save when trying to go to the dashboard [livingdocs-editor #2314](https://github.com/livingdocsIO/livingdocs-editor/pull/2314) :beetle:
  * Fix tooltips [livingdocs-editor #2303](https://github.com/livingdocsIO/livingdocs-editor/pull/2303) :beetle:
  * Redirect on email signup [livingdocs-editor #2384](https://github.com/livingdocsIO/livingdocs-editor/pull/2384) [livingdocs-server #2149](https://github.com/livingdocsIO/livingdocs-server/pull/2149) :beetle:
  * pass terms acceptance to server [livingdocs-editor #2379](https://github.com/livingdocsIO/livingdocs-editor/pull/2379) :beetle:
  * Remove request for title when useAsTitle is set to a metadata property [livingdocs-editor #2375](https://github.com/livingdocsIO/livingdocs-editor/pull/2375) :beetle:
  * Fix webpack build loop triggered by changes in dist directory [livingdocs-editor #2337](https://github.com/livingdocsIO/livingdocs-editor/pull/2337) :beetle:
  * Fix readonly authorization [livingdocs-editor #2317](https://github.com/livingdocsIO/livingdocs-editor/pull/2317) [livingdocs-server #2120](https://github.com/livingdocsIO/livingdocs-server/pull/2120) :beetle:
  * Fix link popover in Safari [livingdocs-editor #2310](https://github.com/livingdocsIO/livingdocs-editor/pull/2310) :beetle:
  * Fix the version.json fallback interval [livingdocs-editor #2300](https://github.com/livingdocsIO/livingdocs-editor/pull/2300) :beetle:
  * Fix the comparison of elasticsearch mappings on sequential runs [livingdocs-server #2143](https://github.com/livingdocsIO/livingdocs-server/pull/2143) :beetle:
  * Bring document route checker up to date with newest routing change [livingdocs-server #2124](https://github.com/livingdocsIO/livingdocs-server/pull/2124) :beetle:
  * Fix unpublish route [livingdocs-server #2085](https://github.com/livingdocsIO/livingdocs-server/pull/2085) :beetle:
  * Reorganize toolbar action css to fix paddings [livingdocs-editor #2395](https://github.com/livingdocsIO/livingdocs-editor/pull/2395) :gift:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
