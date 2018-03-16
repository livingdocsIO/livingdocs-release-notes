
## Repositories

This release consists of the following new versions of the `livingdocs-server` and `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `66.3.5`
`@livingdocs/editor` | `27.4.9`

### Livingdocs Server

How to require the server in your package.json:

```json
"dependencies": {
  "@livingdocs/server": "66.3.5",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-server/tree/release-2018-02

### Livingdocs Editor

How to require the editor in your package.json:

```json
"dependencies": {
  "@livingdocs/editor": "27.4.9",
}
```

- Link to the release branch:
  https://github.com/upfrontIO/livingdocs-editor/tree/release-2018-02

# Highlights

## Routing :gift:

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

### Configuration

Routing configuration consists of two parts:

### Server configuration

The environment files need two pieces of configuration:

#### KV config

Routing data is stored in a Key-Value (KV) store. This store is abstracted by
a leveldb API named **levelup**.

```js
  routing: {
    enabled: true,
    redis: {
      masterCheckInterval: 5000
    },
    indexing: {
      enabled: true,
      batchSize: 1000,
      watchInterval: 1000,
      debugRoutes: false
    }
  }
```

#### Configurable path patterns

`type PathPattern = string;`


```js
  routing: {
    enabled: bool,
    pathPatterns: {
      // path to an 'article' needs to have an `:id`, path to a 'page' doesn't
      type: 'article' | 'page',
      // used to build `documentType` paths and to parse article paths
      current: PathPattern,
      // previously used path patterns, used to parse paths if `current` failed
      legacy: PathPattern[]
    }
  }
```

A path pattern is a string defining the structure of paths to documents.
Dynamic parts are defined with `:placeholders`.

A path patterns is used when generating the path to a publication during the
publication process. It is part of what gets written in the Publication Metadata
under the `routing` key. It is also used to resolve some path to the
corresponding document.

Here is the list of default path pattern placeholders available, together with
their respective RegExp part used while resolving a path:

* `:id`: document id

    `[0-9]+`

* `:slug`: title slug

    `[a-zA-Z0-9_-]+`

* `:M`: month: 1 2 ... 11 12

    `1|2|3|4|5|6|7|8|9|10|11|12`

* `:MM`: month: 01 02 ... 11 12

    `01|02|03|04|05|06|07|08|09|10|11|12`

* `:MMM`: month: jan feb ... nov dec

    `jan|feb|mar|apr|may|jun|jul|aug|sep|oct|nov|dec`

* `:MMMM`: month: january february ... november december

    `january|february|march|april|may|june|july|august|september|october|november|december`

* `:D`: day: 1 2 ... 30 31

    `1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|16|17|18|19|20|21|22|23|24|25|26|27|28|29|30|31`

* `:DD`: day: 01 02 ... 30 31

    `01|02|03|04|05|06|07|08|09|10|11|12|13|14|15|16|17|18|19|20|21|22|23|24|25|26|27|28|29|30|31`

* `:Y`: year: 70 71 ... 29 30

    `[0-9]{2}`

* `:YYYY`: year: 1970 1971 ... 2029 2030

    `[0-9]{4}`

##### Custom placeholders:
Example config:

```js
// content type named 'article', article.js
  metadata: {
    …

    configuredpluginname: {
      plugin: 'li-some-plugin'
    }
  },
  routing: {
    enabled: true,
    pathPatterns: {
      type: 'article',
      current: '/:YYYY/:MM/:DD/:configuredpluginname/:slug--:id',
      legacy: [
        '/article/:slug--:id'
      ]
    }
  }
// content type named 'page', page.js
  routing: {
    enabled: true,
    pathPatterns: {
      type: 'page',
      current: '/page/:slug',
      legacy: [
        '/:slug'
      ]
    }
  }
```

* Patterns are used to build a path for a document by replacing the `:placeholder`s with actual values extracted from the published `documentVersion`.
* Patterns are customizable, if our backend does not know what to do with a `:placeholder` it looks for a configured metadata plugin with that name and calls its `.getRoutePart(documentVersion) => string` method to retrieve a string with which to replace this custom placeholder.
* Patterns are used to resolve a path to the corresponding `documentId`, provided the path matches a pattern that contains an `:id`
* `legacy` patterns are used as fallback, when all else fails a KV lookup is issued.
* Since any path with `type: 'article'` has an `:id` in it, these path do not get indexed in the KV store. Extracting the document ID from the URL is faster than looking it up in a KV store.

#### Routing API

Available on the routing feature API `server.features.api('li-routing').`

##### Indexer API

```js
/**
 * @function start Starts the indexer. Used by the tests.
 * @param callback: (err: Error | null): void
 */
indexer.start(done)

/**
 * @function stop Stops the indexer. Used by the tests.
 * @param callback: (err: Error | null): void
 */
indexer.stop(done)

/**
 * @function startDistributed Starts distributed routes indexing, will elect a master
 * which will start indexing.
 */
indexer.startDistributed()

/**
 * @function checkRoutes Starts routes checker.
 */
indexer.checkRoutes()
```

### New Routing API

```
type PublicationStatus = {
  route: {
    metadata: {
      projectId: number;
      channelId: number;
      channelHandle: string;
    };
    data: {
      path: string;
      type: 'document' | 'unpublished' | 'deleted';
      resource: {
      id: number;
      statusCode: 200 | 410;
      };
    };
  };
};

type Placeholder = {
  placeholder: string;
  index: number;
  regex: string;
};
```

#### Builder API

##### `getBuilder`

```js
/**
 * @function getBuilder Gets builders for both documentTypes for this channel.
 * @param obj: { projectId: number, channelId: number }
 * @param callback: (err: Error | null, value: obj | null): void
 */
getBuilder({projectId, channelId}, callback)
```

##### `buildPath`

```js
/**
 * @function buildPath Builds the path to a published document.
 * @param obj: documentVersion: DocumentVersion
 * @param callback: (err: Error | null, value: string | null): void
 */
buildPath(documentVersion, callback)
```

##### `buildPathWith`

```js
/**
 * @function buildPath Builds the path to a published document.
 * @param obj
 * @param obj.documentVersion: DocumentVersion
 * @param obj.pattern: String
 * @param callback: (err: Error | null, value: string | null): void
 */
buildPath({documentVersion, pattern}, callback)
```

#### Resolver API

##### `resolveFromPath`

Resolving strategy is:

1. attempt `documentId` extraction using the parsers built with `pathPatterns.current` from contentTypes that have `pathPattern.type === 'article'`
1. attempt `documentId` extraction using the parsers built with `pathPatterns.legacy` from contentTypes that have `pathPattern.type === 'article'`
1. attempt `documentId` extraction using the parsers built with `pathPatterns.current` from contentTypes that have `pathPattern.type === 'page'`
1. attempt `documentId` extraction using the parsers built with `pathPatterns.legacy` from contentTypes that have `pathPattern.type === 'page'`
1. do a KV lookup with the path
1. give up and return an error (404)

```js
/**
 * @function fromPath Resolves a path to a publicationStatus
 * @param obj: { projectId: number, channelId: number, path: string }
 * @param callback: (err: Error | number | null, value: PublicationStatus | null): void
 */
resolveFromPath({projectId, channelId, path}, callback)
```

##### `resolveDocumentId`

```js
/**
 * @function fromDocumentId Gets publication status from document ID
 * @param obj: { projectId: number, channelId: number, documentId: number }
 * @param callback: (err: Error | number | null, value: PublicationStatus | null): void
 */
resolveFromDocumentId({projectId, channelId, documentId}, callback)
```

##### `resolveDocumentIds`

```js
/**
 * @function fromDocumentIds Gets publication status from document IDs
 * @param obj: { projectId: number, channelId: number, documentIds: number[] }
 * @param callback: (err: Error | number | null, value: PublicationStatus | null): void
 */
resolveFromDocumentId({projectId, channelId, documentIds}, callback)
```

### Libs

##### `placeholder_utils.js`

This lib takes care of all `pathPattern`s handling.

It exposes the following:

###### `parsePattern`

```js
/**
 * @function parsePattern Validates and parses a pathPattern into an object that can be used
 * to build and parse actual paths
 * @param pathPattern: string
 * @param skipIdCheck?: skipIdCheck: boolean = false
 * @return Placeholder[]
 */
parsePattern(pathPattern, skipIdCheck)
```

###### `buildParser`

```js
/**
 * @function buildParser Validates and parses a pathPattern into an object that can be used
 * to build and parse actual paths
 * @param pattern: string
 * @param placeholders: Placeholder[]
 * @return (path, callback: (err, parsed) => void)
 */
buildParser(pattern, placeholders)
```

[Server PR #1673](https://github.com/upfrontIO/livingdocs-server/pull/1673)





## Support for Animated gifs in the Images Editing API :gift:

The editor now supports animated gifs.

[Server PR #1858](https://github.com/upfrontIO/livingdocs-server/pull/1858)

## Manual migration script to fix content types :beetle:

In the current releases (january & february) the content_type column on the publication events table is missing all the data. The script db/manual-migrations/004-write-content-type-on-events-table.js inserts that data in a non-blocking script.

We won't do a blocking migration as that might cause downtime for big customers (we'll need to find good solutions for that in the future). Please run the regular migration and after that apply the manual one. A blocking migration that makes sure that all columns are `NOT NULLABLE` will follow in the february or march release.

### Required Action
```bash
./node_modules/@livingdocs/server/db/manual-migrations/003-write-content-type-v2.js
# and
./node_modules/@livingdocs/server/db/manual-migrations/004-write-content-type-on-events-table.js
```

[Server PR #1857](https://github.com/upfrontIO/livingdocs-server/pull/1857)



## Reduce image flashing when uploading an image :beetle:

Reduce flashing when an image is uploaded. Before this pull request first the image was set and then one tick later the crop was set. Resulting in a rerender that caused the flashing.

[Editor PR #1829](https://github.com/upfrontIO/livingdocs-editor/pull/1829)


## Scroll to inlined errors :gift:

When an error happens for a metadata field in the publish screen, if the error is inlined, it scrolls to that specific error.
Example of an inlined error:
![screen shot 2018-02-27 at 3 17 53 pm](https://user-images.githubusercontent.com/1951875/36733629-78b552d0-1bd1-11e8-95e1-01cf6fca6821.png)

[Editor PR #1874](https://github.com/upfrontIO/livingdocs-editor/pull/1874)



## Throw an Error if there are no configured Metadata Plugins :beetle:

- Fix: Improve the warning log when the contentType can not be loaded.
- Fix: Throw an error on workspace creation (open article), when no metadata plugins are configured

### Deprecations

- `channel.getContentTypeConfig` is deprecated and has been replaced with `channel.getContentType`.

[Editor PR #1918](https://github.com/upfrontIO/livingdocs-editor/pull/1918)


## Add contentType selection to page creation :beetle:

The page creation now includes choosing a content type before setting the page title.

### Deprecations

- ui-router state `app.editor.articles` moved to `app.articles`
- method `documentCreator.createArticle()` changed to the more generic `documentCreator.createDocument()`. The createDocument method also optionally accepts title and metadata parameters. This gives you more flexibility when creating articles.

### Refactorings

All document creation and document copy UI code was refactored to reduce code duplications.

[Editor PR #1849](https://github.com/upfrontIO/livingdocs-editor/pull/1849)


# Other Changes

* Editor
  * Add contentType selection to page creation [#1849](https://github.com/upfrontIO/livingdocs-editor/pull/1849) :gift:
  * Fix endless redirect loop with missing pusher config [#1833](https://github.com/upfrontIO/livingdocs-editor/pull/1833) :beetle:
  * Improved error handling for session initialization errors [#1863](https://github.com/upfrontIO/livingdocs-editor/pull/1863) :wrench:
  * Update material-design-icons-svg to version 2.0.0 [#1822](https://github.com/upfrontIO/livingdocs-editor/pull/1822) :wrench:
  * Disable version check locally [#1838](https://github.com/upfrontIO/livingdocs-editor/pull/1838) :wrench:
  * Validate editor imageService config [#1884](https://github.com/upfrontIO/livingdocs-editor/pull/1884) :wrench:
  * Fix missing list assignment in publish screen [#1850](https://github.com/upfrontIO/livingdocs-editor/pull/1850) :beetle:
  * Fix anchor links are persisted [#1845](https://github.com/upfrontIO/livingdocs-editor/pull/1845) :beetle:
  * Hide toolbar when editing teaser image [#1841](https://github.com/upfrontIO/livingdocs-editor/pull/1841) :beetle:
  * Disable version check locally [#1838](https://github.com/upfrontIO/livingdocs-editor/pull/1838) :beetle:
  * Properly set home page title on selection [#1834](https://github.com/upfrontIO/livingdocs-editor/pull/1834) :beetle:
  * Fix endless redirect loop with missing pusher config [#1833](https://github.com/upfrontIO/livingdocs-editor/pull/1833) :beetle:
  * Use designProxy instead of removed designLoader [#1815](https://github.com/upfrontIO/livingdocs-editor/pull/1815) :beetle:
  * Еmbed code should break across lines so that all is visible [#1878](https://github.com/upfrontIO/livingdocs-editor/pull/1878) :beetle:
  * Show only a component transformation if there are valid transformations [#1885](https://github.com/upfrontIO/livingdocs-editor/pull/1885) :beetle:
  * Fix print dialogs [#1902](https://github.com/upfrontIO/livingdocs-editor/pull/1902) :beetle:
  * Fixes print layout select for new release [#1911](https://github.com/upfrontIO/livingdocs-editor/pull/1911) :beetle:
  * The editor considers canReset: true for a li-meta-slug-form [#1917](https://github.com/upfrontIO/livingdocs-editor/pull/1917) :beetle:
  * Missing list assignment in publish screen [#1873](https://github.com/upfrontIO/livingdocs-editor/pull/1873) :beetle:
  * Update public api documentation [#1827](https://github.com/upfrontIO/livingdocs-editor/pull/1827) :gift:
  * Position the proofreading box properly [#1820](https://github.com/upfrontIO/livingdocs-editor/pull/1820) :gift:
  * Update a module to the latest version [roboto-fontface](https://github.com/upfrontIO/livingdocs-editor/pull/1832), [imports-loader](https://github.com/upfrontIO/livingdocs-editor/pull/1861), [file-loader](https://github.com/upfrontIO/livingdocs-editor/pull/1856), [autoprefixer](https://github.com/upfrontIO/livingdocs-editor/pull/1840), [coveralls](https://github.com/upfrontIO/livingdocs-editor/pull/1675), [exports-loader](https://github.com/upfrontIO/livingdocs-editor/pull/1830), [url-loader](https://github.com/upfrontIO/livingdocs-editor/pull/1684), [angular-legacy-sortablejs-maintained](https://github.com/upfrontIO/livingdocs-editor/pull/1852), [material-design-icons-svg](https://github.com/upfrontIO/livingdocs-editor/pull/1822), [cpy](https://github.com/upfrontIO/livingdocs-editor/pull/1662), [pusher-js](https://github.com/upfrontIO/livingdocs-editor/pull/1670), [human-format](https://github.com/upfrontIO/livingdocs-editor/pull/1728) :gift:
  * Improve no results feedback [#1859](https://github.com/upfrontIO/livingdocs-editor/pull/1859) :wrench:
  * Migrate profile modal onto separate page [#1843](https://github.com/upfrontIO/livingdocs-editor/pull/1843) :wrench:
  * Increase padding on the left and right of text inputs [#1835](https://github.com/upfrontIO/livingdocs-editor/pull/1835) :wrench:
  * Provide a better error message when the server is offline [#1831](https://github.com/upfrontIO/livingdocs-editor/pull/1831) :wrench:
  * Prettify project settings form [#1836](https://github.com/upfrontIO/livingdocs-editor/pull/1836) :wrench:
  * Prevent input selection for publication date [#1879](https://github.com/upfrontIO/livingdocs-editor/pull/1879) :beetle:


* Server
  * Various bugfixes for server shutdown [#1795](https://github.com/upfrontIO/livingdocs-server/pull/1795) :beetle:
  * Support spaces in directory paths when running tests [#1846](https://github.com/upfrontIO/livingdocs-server/pull/1846) :beetle:
  * Allow to run tests while app-path contains spaces [#1810](https://github.com/upfrontIO/livingdocs-server/pull/1810) :wrench:
  * Add a feature for running tasks [#1622](https://github.com/upfrontIO/livingdocs-server/pull/1622) :wrench:
  * Provide a better error message when sending a mail fails [#1803](https://github.com/upfrontIO/livingdocs-server/pull/1803) :wrench:
  * Update livingdocs-framework to 8.1.0 [#1832](https://github.com/upfrontIO/livingdocs-server/pull/1832) :beetle:
  * Expose origin array to the editor [#1813](https://github.com/upfrontIO/livingdocs-server/pull/1813) :beetle:
  * Validate image service config [#1820](https://github.com/upfrontIO/livingdocs-server/pull/1820), [#1884](https://github.com/upfrontIO/livingdocs-editor/pull/1884) :beetle:
  * Upgrade to eslint@4.18.2 [#1829](https://github.com/upfrontIO/livingdocs-server/pull/1829) :beetle:
  * Fix data-migration task [#1818](https://github.com/upfrontIO/livingdocs-server/pull/1818) :beetle:
  * Allow `editor.images` config for contentTypes [#1799](https://github.com/upfrontIO/livingdocs-server/pull/1799) :beetle:
  * Silently skip indexing for publications that have no path [#1824](https://github.com/upfrontIO/livingdocs-server/pull/1824) :wrench:
---

  **Icon Legend**

  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
