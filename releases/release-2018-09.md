

**Attention:** If you skipped one or more release, please also check the release-notes of the skipped ones.

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `75.2.1`
`@livingdocs/editor` | `34.3.1`


## Livingdocs Server

How to require the server in your package.json:

```json
"dependencies": {
  "@livingdocs/server": "75.2.1",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-YYYY-MM


## Livingdocs Editor

How to require the editor in your package.json:

```json
"dependencies": {
  "@livingdocs/editor": "34.3.1",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-YYYY-MM



# Highlights

## Document Copy Feature Improvement :gift: :fire:

... Add a proper description ...



#### Breaking Changes
- renamed `documentCopyApi.copy` to `documentCopyApi.copyByDocumentId`
- removed `source` parameter in the `afterConversion` function of a conversionInstruction.
- removed `copyUnknownComponents` of the copy config (but this setting had no effect anyway)


#### Related Pull Requests
* Transform Document [livingdocs-server #2092](https://github.com/livingdocsIO/livingdocs-server/pull/2092) :gift:


* Allow a simple copy (1:1 copy of a content-type without a copy config on the server) [livingdocs-server #2099](https://github.com/livingdocsIO/livingdocs-server/pull/2099) :gift:

* Transform Document [livingdocs-editor #2251](https://github.com/livingdocsIO/livingdocs-editor/pull/2251) :gift:


* Refactoring: Split Up Document Copy Feature to Support Main Use Cases Better [livingdocs-server #2081](https://github.com/livingdocsIO/livingdocs-server/pull/2081) :wrench:




# Breaking Changes :fire:

## Indexing API and index separation :gift: :fire:

This change improves the speed and reliability of (re)indexing documents to elasticsearch.

* Redis is required as a dependency
* New Redis config is required:
```js
redis: {
  // Simple configuration (HA redis cluster can be found in PR 2009)
  host: process.env.redis_host || 'localhost',
  port: process.env.redis_port || 6379,
}
```

For a more detailed description check the [server PR #2009](https://github.com/livingdocsIO/livingdocs-server/pull/2009)

## Removed (unused) image API :wrench: :fire:

Removed the `/images` endpoint and API on the server.

Required actions:
* If `liServer.features.api('li-images').create` was used, go to the [server PR #2068](https://github.com/livingdocsIO/livingdocs-server/pull/2068) and check the description in more detail



## Improve the build performance :wrench: :fire:

During development, sourcemaps are not built with `npm start` anymore. Use `npm run start:sourcemaps` instead.

Read more at [livingdocs-editor #2262](https://github.com/livingdocsIO/livingdocs-editor/pull/2262)



## Search Filters :fire:

**Caution**: Custom filters should be tested for the reset. It depends on their implementation if they react to 'reset all filters'.

Read more at [livingdocs-editor #2267](https://github.com/livingdocsIO/livingdocs-editor/pull/2267)



## Title handling :fire:

Implicit title behaviour where the metadata property 'title' was synced with the document title now has to be defined explicitly in the configuration.

The previous behaviour can be achieved with setting `useAsTitle` to `true` on the title property.

```js
metadata: [{
  type: 'li-text',
  handle: 'title',
  config: {
    useAsTitle: true
  }
}]
```

Read more at [livingdocs-editor #2253](https://github.com/livingdocsIO/livingdocs-editor/pull/2253)



# Other Changes
* Chore
  * Introduce Content Behavior [livingdocs-editor #2170](https://github.com/livingdocsIO/livingdocs-editor/pull/2170) :gift: :gift: :gift:
  * Support `--reporter` option in test cli [livingdocs-server #2042](https://github.com/livingdocsIO/livingdocs-server/pull/2042) :wrench:
  * Throw a MetadataValidationError during autosave [livingdocs-server #2054](https://github.com/livingdocsIO/livingdocs-server/pull/2054) :wrench:
  * Add component properties styles to styleguide  [livingdocs-editor #2219](https://github.com/livingdocsIO/livingdocs-editor/pull/2219) :chore:


* Bugfixes
  * Support partial document include renders [livingdocs-server #2086](https://github.com/livingdocsIO/livingdocs-server/pull/2086) :beetle:
  * allow default handle set by editor [livingdocs-server #2078](https://github.com/livingdocsIO/livingdocs-server/pull/2078) :beetle:
  * Fix multiselect [livingdocs-server #2075](https://github.com/livingdocsIO/livingdocs-server/pull/2075) :beetle:
  * Fix of Hugo Article Drag & Drop [livingdocs-server #2113](https://github.com/livingdocsIO/livingdocs-server/pull/2113) :beetle:
  * metadataFormArrangement to metadataProperty compatibility check [livingdocs-server #2100](https://github.com/livingdocsIO/livingdocs-server/pull/2100) :beetle:
  * Fix: Always enable channel configs feature [livingdocs-server #2107](https://github.com/livingdocsIO/livingdocs-server/pull/2107) :beetle:
  * Fix token mask [livingdocs-editor #2147](https://github.com/livingdocsIO/livingdocs-editor/pull/2147) :beetle:
  * Fix dependencies requirement [livingdocs-editor #2196](https://github.com/livingdocsIO/livingdocs-editor/pull/2196) :beetle: :gift:
  * Fix NZZ logo styles  [livingdocs-editor #2239](https://github.com/livingdocsIO/livingdocs-editor/pull/2239) :beetle:
  * Create content-types with title and teaserImage [livingdocs-editor #2230](https://github.com/livingdocsIO/livingdocs-editor/pull/2230) :beetle:
  * Fix to show a pusher error again with wrong credentials [livingdocs-editor #2234](https://github.com/livingdocsIO/livingdocs-editor/pull/2234) :beetle:


* Print
  * adds authors and editor to print export [livingdocs-server #2037](https://github.com/livingdocsIO/livingdocs-server/pull/2037) :gift:
  * fix(print): escaping special characters in title for hugo. Added additional metadata to print section on export to hugo [livingdocs-server #2105](https://github.com/livingdocsIO/livingdocs-server/pull/2105) :beetle:


* Channel config v2
  * Allow to rewrite the channel config [livingdocs-server #2066](https://github.com/livingdocsIO/livingdocs-server/pull/2066) :gift:
  * feat: li-enum metadata plugin now supports a dataProvider config [livingdocs-server #2040](https://github.com/livingdocsIO/livingdocs-server/pull/2040) :gift:
  * Added channel config publish event [livingdocs-server #2029](https://github.com/livingdocsIO/livingdocs-server/pull/2029) :gift:
  * extend schema for contentType.editor [livingdocs-server #2091](https://github.com/livingdocsIO/livingdocs-server/pull/2091) :gift:
  * Channel config diff improvements [livingdocs-server #2080](https://github.com/livingdocsIO/livingdocs-server/pull/2080) :gift:
  * Support language configuration through the editor [livingdocs-server #2071](https://github.com/livingdocsIO/livingdocs-server/pull/2071) :gift:
  * Fix: li-string-list / li-numeric-list metadata plugins [livingdocs-server #2063](https://github.com/livingdocsIO/livingdocs-server/pull/2063) :beetle:
  * Fix the compatibility of the metadata plugin property 'label' between channelConfig v1 and v2 [livingdocs-server #2073](https://github.com/livingdocsIO/livingdocs-server/pull/2073) :beetle:
  * Fix channel config diff [livingdocs-server #2072](https://github.com/livingdocsIO/livingdocs-server/pull/2072) :beetle:


* Features
  * Design viewer [livingdocs-editor #2202](https://github.com/livingdocsIO/livingdocs-editor/pull/2202) :gift:
  * Feat/admin project details [livingdocs-editor #2237](https://github.com/livingdocsIO/livingdocs-editor/pull/2237) :gift:



  * admin-project-details: aggregate documents by content_type [livingdocs-server #2084](https://github.com/livingdocsIO/livingdocs-server/pull/2084) :gift:
  * Improve Multiselect [livingdocs-editor #2227](https://github.com/livingdocsIO/livingdocs-editor/pull/2227) :gift:
  * allow autoSaveInterval to be configurable [livingdocs-server #2061](https://github.com/livingdocsIO/livingdocs-server/pull/2061) :gift:
  * Allow for Array in Content Type Filter [livingdocs-server #2094](https://github.com/livingdocsIO/livingdocs-server/pull/2094) :gift:
  * Change the default language handle [livingdocs-server #2093](https://github.com/livingdocsIO/livingdocs-server/pull/2093) :gift:



* Testing
  * re-add author for e2e tests [livingdocs-server #2090](https://github.com/livingdocsIO/livingdocs-server/pull/2090) :wrench:
  * Remove old author plugin in the e2e seeding [livingdocs-server #2089](https://github.com/livingdocsIO/livingdocs-server/pull/2089) :wrench:
  * Increase content type limit [livingdocs-server #2109](https://github.com/livingdocsIO/livingdocs-server/pull/2109) :wrench:
  * fix magazine setup for cypress tests [livingdocs-server #2104](https://github.com/livingdocsIO/livingdocs-server/pull/2104) :beetle:
  * Set CI env for cypress editor tests [livingdocs-server #2103](https://github.com/livingdocsIO/livingdocs-server/pull/2103) :wrench:
  * Fix Cypress Tests [livingdocs-editor #2242](https://github.com/livingdocsIO/livingdocs-editor/pull/2242) :gift:



* UX/Design
  * Design responsive home screen [livingdocs-editor #2167](https://github.com/livingdocsIO/livingdocs-editor/pull/2167) :gift:
  * Fix scrolling and mobile metadata [livingdocs-editor #2215](https://github.com/livingdocsIO/livingdocs-editor/pull/2215) :gift:
  * fix(docked content): Responsiveness [livingdocs-editor #2205](https://github.com/livingdocsIO/livingdocs-editor/pull/2205) :beetle:
  * design(content type settings): Clean-up [livingdocs-editor #2189](https://github.com/livingdocsIO/livingdocs-editor/pull/2189) :wrench:
  * fix(sidebar): Scrolling [livingdocs-editor #2191](https://github.com/livingdocsIO/livingdocs-editor/pull/2191) :beetle:
  * fix(application menu): Top group label [livingdocs-editor #2181](https://github.com/livingdocsIO/livingdocs-editor/pull/2181) :beetle:
  * fix(wrappers): Scroll overflow [livingdocs-editor #2177](https://github.com/livingdocsIO/livingdocs-editor/pull/2177) :beetle:
  * fix(floating navi): Inactive state [livingdocs-editor #2175](https://github.com/livingdocsIO/livingdocs-editor/pull/2175) :beetle:
  * Design Floating Navi [livingdocs-editor #2173](https://github.com/livingdocsIO/livingdocs-editor/pull/2173) :gift:
  * Lay out password reset forms horizontally [livingdocs-editor #2259](https://github.com/livingdocsIO/livingdocs-editor/pull/2259) :gift:
  * Add comment card to styleguide [livingdocs-editor #2252](https://github.com/livingdocsIO/livingdocs-editor/pull/2252) :wrench:
  * [Styleguide] Add comment icon to editable tooltip [livingdocs-editor #2247](https://github.com/livingdocsIO/livingdocs-editor/pull/2247) :gift:
  * Improve Menu UI [livingdocs-editor #2266](https://github.com/livingdocsIO/livingdocs-editor/pull/2266) :gift:


* Metadata References
  * Add form for li-metadata-references [livingdocs-editor #2208](https://github.com/livingdocsIO/livingdocs-editor/pull/2208) :gift:
  * Integrate references in example server [livingdocs-server #2057](https://github.com/livingdocsIO/livingdocs-server/pull/2057) :gift:
  * Metadata References [livingdocs-server #2030](https://github.com/livingdocsIO/livingdocs-server/pull/2030) :gift:
  * Metadata References [livingdocs-editor #2141](https://github.com/livingdocsIO/livingdocs-editor/pull/2141) :gift:


* Metadata Administration
  * Client side validation [livingdocs-editor #2165](https://github.com/livingdocsIO/livingdocs-editor/pull/2165) :gift:
  * Fix: li-integer metadata property service / validation [livingdocs-editor #2144](https://github.com/livingdocsIO/livingdocs-editor/pull/2144) :beetle:
  * Feature: Add required checkbox metadata forms [livingdocs-editor #2138](https://github.com/livingdocsIO/livingdocs-editor/pull/2138) :gift:
  * Configure multi-language feature [livingdocs-editor #2214](https://github.com/livingdocsIO/livingdocs-editor/pull/2214) :gift:
  * Fix: string-list / numeric-list metadata types [livingdocs-editor #2206](https://github.com/livingdocsIO/livingdocs-editor/pull/2206) :gift:
  * Feat: hide from form checkbox for metadata properties [livingdocs-editor #2200](https://github.com/livingdocsIO/livingdocs-editor/pull/2200) :gift:
  * Feat: Limit content types and metadata properties [livingdocs-editor #2184](https://github.com/livingdocsIO/livingdocs-editor/pull/2184) :gift:
  * Feat: li-text form supports max-length & choosing input type (text vs textarea) [livingdocs-editor #2179](https://github.com/livingdocsIO/livingdocs-editor/pull/2179) :gift:
  * Fix li enum metadata type [livingdocs-editor #2169](https://github.com/livingdocsIO/livingdocs-editor/pull/2169) :gift:
  * Fix: Project settings publish screen recognised changes when there where none [livingdocs-editor #2176](https://github.com/livingdocsIO/livingdocs-editor/pull/2176) :beetle:
  * Fix dynamic component [livingdocs-editor #2183](https://github.com/livingdocsIO/livingdocs-editor/pull/2183) :beetle:
  * feat: support metadata plugin configurationUi.disableSelection [livingdocs-editor #2224](https://github.com/livingdocsIO/livingdocs-editor/pull/2224) :gift:
  * Make language handle read-only [livingdocs-editor #2249](https://github.com/livingdocsIO/livingdocs-editor/pull/2249) :gift:
  * Feat: Handle metadata validation errors on autosave [livingdocs-editor #2198](https://github.com/livingdocsIO/livingdocs-editor/pull/2198) :beetle:


  ---

  **Icon Legend**

  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
