
**Attention:** If you skipped one or more release, please also check the release-notes of the skipped ones.
# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `75.9.3`
`@livingdocs/editor` | `35.15.4`

## Livingdocs Server
How to require the server in your package.json:

```json
"dependencies": {
  "@livingdocs/server": "75.9.3",
}
```
- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2018-11

### Livingdocs Server Patches
- [v75.9.3](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v75.9.3): indexer: Set the correct user and creation timestamp on an indexed document
- [v75.9.2](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v75.9.2): metadata: integrate custom teaser image for testing
- [v75.9.1](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v75.9.1): image-processing: Catch newer imagemagic error message when applying the image-processing on an invalid image
- [v75.9.0](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v75.9.0): version bump



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "35.15.4",
}
```
- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2018-11

### Livingdocs Editor Patches
- [v35.15.4](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v35.15.4): Integrate custom teaser image for testing
- [v35.15.3](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v35.15.3): signup: Get rid of error messages caused by redirects
- [v35.15.2](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v35.15.2): fix broken menu tool
- [v35.15.1](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v35.15.1): fix Thumbnail of copied image

# Highlights

## Comments :gift:

You can now add comment threads to text of a document. The comment threads can have replies to allow for discussions directly in the editor. You can edit or delete your own replies and comment threads can be resolved to indicate that they have been addressed. We hope you can use comments in a variety of ways to improve your workflows and would love feedback how you use them and how they can be improved.

* Related Pull Requests
  * [livingdocs-editor #2301](https://github.com/livingdocsIO/livingdocs-editor/pull/2301)



## Copy Component :gift:

With an enabled 'Copy Component' feature it's possible to copy component or sets of components in a document or across different documents.

Workflow:
- Click on a component in the editor
- Click on `copy` at the sidebar
- Go to the clipboard
- Drag and drop the copied component into the editor

When trying to drop a component, you get immediate feedback when drop zones are not allowed with a reason.


#### Enable copy component feature

To enable the copy component feature add `componentCopyEnabled` to your editor environment config, e.g.

```all.js
modules.exports: {
  app: {
    copy: {
      componentCopyEnabled: true
    }
  }
}
```

* Related Pull Requests
  * [livingdocs-editor #2312](https://github.com/livingdocsIO/livingdocs-editor/pull/2312)



## Improved server admin screens :gift:

You have now a lot more information on the server admin screen like
- create date of a user
- identity of the user (SSO or mail)
- user login graph

For a description of all additions check the related pull requests.

* Related Pull Requests
  * [livingdocs-editor #2372](https://github.com/livingdocsIO/livingdocs-editor/pull/2372)
  * [livingdocs-server #2134](https://github.com/livingdocsIO/livingdocs-server/pull/2134)




# Breaking Changes :fire:

## Migrate the database

```sh
# run grunt migrate to update to the newest database scheme
# migration - 111-add-comments-table.js
#   create comments table + add events to the stream_events_types table
grunt migrate
```

## Teaser images

### Update custom elasticsearch document mapping
When using a custom elasticsearch document mapping (the mapping can be found at `search: metadata_mapping` usually in the all environment config), and you used teaser images at the publish screen, the elasticsearch mapping of the corresponding field needs to be updated with a `ratio` property.

```
"teaserImage": {
  "properties": {
    "crops": {
      "properties": {
        ...,
        "ratio": {
          "type": "double",
          "index": "not_analyzed"
        }
      }
    }
  }
}
```

After adding `ratio` to the mapping, execute `grunt search-index:document` during deployment to update the mapping.

### Update custom metadata plugins

When using a custom image metadata plugin, instead of the default `li-image` plugin, it's needed to set `behaveAsLiImage: true` to your metadata config for backwards compatibility, e.g.

```
metadata:
    teaserImage: {
      plugin: 'my-custom-image-plugin',
      config: {
        behaveAsLiImage: true
      }
    }
}
```


##  Replaced Webpack Dev-server with a custom node server :gift: :fire:

This change migrated from a traditional webpack setup to a custom node server with built in webpack support. The consequence is to have a much faster build cycle. The build scripts are now provided as an executable (`bin`) to the downstream. You can run `./node_modules/.bin/livingdocs-editor watch` or `./node_modules/.bin/liivngdocs-editor build` in the downstreams to run the dev server or build the final docker container.

### Migration guide

#### How to require the editor config.

```javascript
// old approach was requiring the config via the index file
const config = require('../../../../config')

// new approach is to require the config via appConfig
const config = require('appConfig')
```

#### How to build a docker container
```bash
# previous setup, all dev dependencies were deployed to production
docker build -t livingdocs-editor:production .
docker run livingdocs-editor:production npm test

# new setup, only the minimal dependencies are deployed to production
docker build -t livingdocs-editor:test .
docker run livingdocs-editor:test npm test
docker run -v $PWD/bundle:/app/bundle livingdocs-editor:test npm run build
docker build -t livingdocs-editor:production ./bundle
```

#### Changes in package.json

* :fire: Renamed `DIST_PATH` to `DIST_DIR`
* :fire: Renamed `CONFIG_PATH ` to `CONFIG_DIR`
* :fire: Removed `ROOT_PATH` without replacement
* :fire: Replaced `npm explore @livingdocs/editor -- npm run build` with a build and watch script.

```javascript
// old approach at the scripts sections of package.json
"build": "DIST_PATH=$PWD/dist CUSTOM_PATH=$PWD/app/editor.js CONFIG_PATH=$PWD/config EDITOR_STYLE_PATH=$PWD/app/styles/editor-styles.scss ROOT_PATH=$PWD npm explore @livingdocs/editor -- npm run build",
"start": "DIST_PATH=$PWD/dist CUSTOM_PATH=$PWD/app/editor.js CONFIG_PATH=$PWD/config EDITOR_STYLE_PATH=$PWD/app/styles/editor-styles.scss ROOT_PATH=$PWD npm explore @livingdocs/editor -- npm run start",
"build:environment": "DIST_PATH=$PWD/dist CUSTOM_PATH=$PWD/app/editor.js CONFIG_PATH=$PWD/config EDITOR_STYLE_PATH=$PWD/app/styles/editor-styles.scss ROOT_PATH=$PWD npm explore @livingdocs/editor -- npm run build:environment",

// new approach at the scripts sections of package.json
"build": "CUSTOM_PATH=./app/editor.js EDITOR_STYLE_PATH=./app/styles/editor-styles.scss livingdocs-editor build",
"start": "CUSTOM_PATH=./app/editor.js EDITOR_STYLE_PATH=./app/styles/editor-styles.scss livingdocs-editor watch",
```

For test instructions, build instructions and supported environment variables and more check the detailed description at the [livingdocs-editor #2264](https://github.com/livingdocsIO/livingdocs-editor/pull/2264).



# Other Changes
* UX
  * Add titles to most pages [livingdocs-editor #2400](https://github.com/livingdocsIO/livingdocs-editor/pull/2400) :gift:
  * Make sign-up responsive [livingdocs-editor #2360](https://github.com/livingdocsIO/livingdocs-editor/pull/2360) :gift:
  * Design component library [livingdocs-editor #2318](https://github.com/livingdocsIO/livingdocs-editor/pull/2318) :gift:
  * Brush up our public documentation [livingdocs-editor #2392](https://github.com/livingdocsIO/livingdocs-editor/pull/2392) :gift:
  * Implement undo/redo in toolbar [livingdocs-editor #2381](https://github.com/livingdocsIO/livingdocs-editor/pull/2381) :gift:

* Improvements
  * Support Escape key to close modal windows [livingdocs-editor #2336](https://github.com/livingdocsIO/livingdocs-editor/pull/2336) :gift:
  * Add flag to disable editing the document title at the toolbar [livingdocs-editor #2370](https://github.com/livingdocsIO/livingdocs-editor/pull/2370)  [livingdocs-server #2140](https://github.com/livingdocsIO/livingdocs-server/pull/2140) :gift:
  * Show content type of an old revision in history [livingdocs-editor #2366](https://github.com/livingdocsIO/livingdocs-editor/pull/2366) :gift:
  * Don't Show History Restore Option with a different content type [livingdocs-editor #2332](https://github.com/livingdocsIO/livingdocs-editor/pull/2332)  [livingdocs-server #2131](https://github.com/livingdocsIO/livingdocs-server/pull/2131) :gift:
  * Document History: Return “Today” instead of hours [livingdocs-editor #2330](https://github.com/livingdocsIO/livingdocs-editor/pull/2330) :gift:
  * No check for id for an active filter [livingdocs-editor #2364](https://github.com/livingdocsIO/livingdocs-editor/pull/2364) :gift:

* Server Administration
  * don’t show filtered users [livingdocs-editor #2378](https://github.com/livingdocsIO/livingdocs-editor/pull/2378)  [livingdocs-server #2146](https://github.com/livingdocsIO/livingdocs-server/pull/2146)
   :wrench:

* Service
  * add delete button to content type menu in project settings [livingdocs-editor #2216](https://github.com/livingdocsIO/livingdocs-editor/pull/2216) :gift:
  * Configure imageRatios in li-image metadata form [livingdocs-editor #2238](https://github.com/livingdocsIO/livingdocs-editor/pull/2238) :gift:
  * Introduction of SSO logins [livingdocs-editor #2328](https://github.com/livingdocsIO/livingdocs-editor/pull/2328)  [livingdocs-server #2128](https://github.com/livingdocsIO/livingdocs-server/pull/2128) :gift:


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