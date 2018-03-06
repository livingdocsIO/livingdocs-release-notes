
## Repositories

This release consists of the following new versions of the `livingdocs-server` and `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `66.3.0`
`@livingdocs/editor` | `27.4.4`

### Livingdocs Server

How to require the server in your package.json:

```json
"dependencies": {
  "@livingdocs/server": "x.x.x",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-server/tree/release-2018-02


### Livingdocs Editor

How to require the editor in your package.json:

```json
"dependencies": {
  "@livingdocs/editor": "x.x.x",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-editor/tree/release-2018-02


# Highlights

## Routing

The routing now supports contentType specific routing configuration. The
configuration also offers more options and possibilities.

Example contentType configuration:
```js
routing: {
  enabled: true,
  pathPatterns: {
    // type 'article' needs to have an `:id` in the pathTemplate
    type: 'article',
    // used to build and parse paths
    current: '/:YYYY/:MM/:DD/:slug--:id',
    // previously used path patterns, used to parse paths if current` failed
    legacy: '/article/:slug--:id'
  }
}
```

For details see:
https://github.com/upfrontIO/livingdocs-server/pull/1673


# Other Changes

* Editor
  * Add contentType selection to page creation
    [#1849](https://github.com/upfrontIO/livingdocs-editor/pull/1849) :gift:
  * Scroll to inlined errors on metadata screen
    [#1874](https://github.com/upfrontIO/livingdocs-editor/pull/1874) :gift:
  * Prevent input selection for publication date
    [#1879](https://github.com/upfrontIO/livingdocs-editor/pull/1879) :beetle:
  * Fix endless redirect loop with missing pusher config
    [#1833](https://github.com/upfrontIO/livingdocs-editor/pull/1833) :beetle:
  * Improved error handling for session initialization errors
    [#1863](https://github.com/upfrontIO/livingdocs-editor/pull/1863) :wrench:
  * Update material-design-icons-svg to version 2.0.0
    [#1822](https://github.com/upfrontIO/livingdocs-editor/pull/1822) :wrench:
  * Disable version check locally
    [#1838](https://github.com/upfrontIO/livingdocs-editor/pull/1838) :wrench:
  * Validate editor imageService config
    [#1884](https://github.com/upfrontIO/livingdocs-editor/pull/1884) :wrench:


* Server
  * Various bugfixes for server shutdown
    [#1795](https://github.com/upfrontIO/livingdocs-server/pull/1795) :beetle:
  * Allow to run tests while app-path contains spaces
    [#1810](https://github.com/upfrontIO/livingdocs-server/pull/1810) :wrench:
  * Add a feature for running tasks
    [#1622](https://github.com/upfrontIO/livingdocs-server/pull/1622) :wrench:
  * Provide a better error message when sending a mail fails
    [#1803](https://github.com/upfrontIO/livingdocs-server/pull/1803) :wrench:


---

  **Icon Legend**

  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
