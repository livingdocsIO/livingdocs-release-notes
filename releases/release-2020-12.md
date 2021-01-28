**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Newsletter](#newsletter)
- [Webinar](#webinar)
- [Patches](#repositories)
- [Highlights](#highlights)
- [Experimental](#experimental)
- [Breaking Changes](#breaking-changes-fire)
- [APIs](#apis-gift)
- [Internal Changes](#internal-changes)
- [Other Changes](#other-changes)

# Newsletter

* Newsletter: **TODO**
* Subscribe here: https://confirmsubscription.com/h/j/61B064416E79453D


# Webinar

* Recording: **TODO**
* Documentation: **TODO**

# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2020-12`
`@livingdocs/editor` | `release-2020-12`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2020-12",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2020-12

### Livingdocs Server Patches
- [v114.0.28](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.28): fix(grunt-user-create): task works again
- [v114.0.27](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.27): fix: support openid-connect
- [v114.0.26](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.26): fix: do not require routing for push notifications
- [v114.0.25](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.25): chore(express): Name our middlewares
- [v114.0.24](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.24): chore(test): Pause the indexers before recreating the indexes as we have pending jobs
- [v114.0.23](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.23): fix(indexing): Start the indexers after server initialization
- [v114.0.22](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.22): test: fix failing imageUploadProxy test
- [v114.0.21](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.21): chore: add error handling and fix linting issues
- [v114.0.20](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.20): fix(document-relations): Fix the updates of document relations that didn't work when the CTE was executed in the wrong order
- [v114.0.19](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.19): fix(document-relations): Fix the updates of document relations after a first insert
- [v114.0.18](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.18): fix(envoy): Fix the envoy support for cookies as they only serve the original url, not the prefix
- [v114.0.17](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.17): fix(video-upload-btn): remove backwards-compatibility-transformations for video
- [v114.0.16](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.16): fix(authentication): Expose the authUtils.setCookies method on authApi.setCookies
- [v114.0.15](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.15): fix(public-api): fix breaking change in GET design
- [v114.0.14](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.14): chore(indexing): Pass the bulk method to the custom index factory
- [v114.0.13](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.13): fix: correctly redirect on user sign up
- [v114.0.12](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.12): fix: bump livingdocs framework
- [v114.0.11](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.11): fix(knex): update to 0.21.14
- [v114.0.10](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.10): fix(factories): remove uuid.v1
- [v114.0.9](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.9): chore: Only execute one http request when deleting configured indexes
- [v114.0.8](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.8): fix(import): add trx to resolveHandles
- [v114.0.7](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.7): fix: remove videoLibrary menu entry from example server
- [v114.0.6](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v114.0.6): fix(indexing): Make the redis prefix optional


## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2020-12",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2020-12

### Livingdocs Editor Patches
- [v57.33.32](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.32): fix(link tool): don't throw if no link config given
- [v57.33.31](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.31): fix: view of lists creation in the side-panel
- [v57.33.30](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.30): fix: jquery version to ~3.4.1
- [v57.33.29](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.29): fix(documentModel): prevent js errors from undefined configs
- [v57.33.28](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.28): fix: add vh growing infinite guard
- [v57.33.27](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.27): chore(drag and drop): fix drop handler function name
- [v57.33.26](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.26): fix(push-notifications): Make routing optional

Remove dependency on `routing` metadata.
- [v57.33.25](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.25): chore: update framework
- [v57.33.24](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.24): fix: debounce-input directive so that it debounces the calls
- [v57.33.23](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.23): fix(includes): correctly apply params from paramsSchema if additional uiComponents are configured for the include service
- [v57.33.22](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.22): fix: tag search in metadata with imatrics calls
- [v57.33.21](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.21): fix: update iframe height on every change of a component
- [v57.33.20](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.20): fix(assets): Serve a 404 error if a non-existent woff2 file is requested
- [v57.33.19](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.19): fix(properties panel): correctly show red alert line for pinned position
- [v57.33.18](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.18): fix: Various viewport-units-buggyfill improvements

- Handle styles without ownerNode in buggyfill
- Reset buggyfill when replacing viewport
- Append buggyfill CSS to body for specicifity
- [v57.33.17](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.17): fix(srcissors): update to 2.0.2
- [v57.33.16](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.16): fix(tasks-panel): Align task panel in publish page
- [v57.33.15](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.15): fix(properties panel): apply correct spacing for include UI components in properties panel
- [v57.33.14](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.14): fix: bump livingdocs framework
- [v57.33.13](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.13): fix(metadata): fix iMatrics inappropriate toggle
- [v57.33.12](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.12): fix: improve image upload layout
- [v57.33.11](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.11): fix(dashboard): Show create buttons to valid users
- [v57.33.10](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.10): chore: unskip character counter cypress test
- [v57.33.9](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.9): fix(inline-links): allow localhost in dev
- [v57.33.8](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.8): fix(deliveries): remove path and routingPath handling from the internal document link feature since it's not reliable
- [v57.33.7](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v57.33.7): fix visibility of inline add button


# Highlights


## Internal Document Links :tada:

When selecting text in the editor, the link tool in the editable toolbar allows to link to documents instead of URLs only. The input field is a combined input and detects if you want to search, or if you entered an URL.

Attention: The delivery needs a strategy to redirect id route patterns in order for inline links to work in the delivery.

![image](https://user-images.githubusercontent.com/821875/95599481-6ea70380-0a51-11eb-9cb5-639db68b238c.png)

- If you search, you get back a list of internal documents
- If you paste an URL that matches one of your deliveries, the link is automatically upgraded to a document reference.

References:
  * [Internal Document Links PR with Screenshots and Explanations](https://github.com/livingdocsIO/livingdocs-editor/pull/3909)
  * [Internal Document Links Extended Search](https://github.com/livingdocsIO/livingdocs-editor/pull/4027)
  * [Internal Document Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3150)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/329)


## Custom Indexes / Queue Base Work :tada:

### Queue Base Work
To support all kind of features which need (job-)queues (now/future), we did some base work. These are the most important changes:
- Get rid of [bullmq](https://github.com/taskforcesh/bullmq)
- Introduce [Redis streams](https://github.com/livingdocsIO/livingdocs-server/pull/3224) for messaging (more control/reliability/transparency)

### Custom Indexes
Some customers want to have their customised Elasticsearch publication index to make customised search requests. The switch to Redis streams was necessary to
make custom indexes possible. Why you could need a custom index and how to setup one, can be found [here](https://github.com/livingdocsIO/livingdocs/pull/328).

**Migration Guide**
If you already have implemented a custom index in your downstream and want to replace it with the Livingdocs custom index solution, please contact us to make a planning. The upgrade is not difficult, but every customer is different and therefore it needs individual planning.

References:
  * [Base Work - Queue Refactoring - Part I](https://github.com/livingdocsIO/livingdocs-server/pull/3187)
  * [Base Work - Queue Refactoring - Part II](https://github.com/livingdocsIO/livingdocs-server/pull/3193)
  * [Base Work - Redis Streams](https://github.com/livingdocsIO/livingdocs-server/pull/3224)
  * [Visualize Redis Queue Infos - Editor](https://github.com/livingdocsIO/livingdocs-editor/pull/3924)
  * [Visualize Redis Queue Infos - Server](https://github.com/livingdocsIO/livingdocs-server/pull/3193)
  * [Custom Elasticsearch Index](https://github.com/livingdocsIO/livingdocs-server/pull/3185)
  * [Custom Elasticsearch Index - Documentation](https://github.com/livingdocsIO/livingdocs/pull/328)
  * [Indexing Cleanup](https://github.com/livingdocsIO/livingdocs-server/pull/3284)


## Cloudinary Storage Support :tada:

Beside Amazon S3 we introduced Cloudinary as storage. Look into the [documentation - TODO: Marc]() for instructions.

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4023)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3270)
  * [Documentation - TODO: Marc]()


## More Secure Authentication Workflow :tada:

We worked on the security for the user authentication in Livingdocs. Some improvements are:

- Increased security for the accessTokens
- if an accessToken is stolen, it can't be used without a valid client cookie
- accessTokens can't renew themselves anymore
- an accessToken is bound to a valid client and session

For more information, read [here](https://github.com/livingdocsIO/livingdocs-server/pull/3225).

References:
  * [Server PR Part I](https://github.com/livingdocsIO/livingdocs-server/pull/3225)
  * [Server PR Part II](https://github.com/livingdocsIO/livingdocs-server/pull/3282)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3952)


## Airship Integration for Push Notifications :tada:

We integrated [Airship](https://www.airship.com/) for push notifications.

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3975)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3231)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/340)




# Experimental

## Mobile - Inline Editing :tada:

With this release, we allow a user to inline add/edit components and its settings in the editor with your mobile. This is a MVP, but we will gradually improve the inline editing in the next few releases.

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3900)


## Editable Teasers :tada:

Editable teasers are embedded editable livingdocs components. Technically editable teasers are doc-includes returning livingdocs components, which can be edited like any other component. For more information read the [documentation - TODO: Beni]() and look into the [example](https://github.com/livingdocsIO/livingdocs-server/pull/3235) on the example-server.

Attention: Editable teasers do not work with the render pipeline v1 (which most of the customers are using at the moment). This should be fixed in an upcoming release.

References:
  * [Editable Teasers Editor Integration](https://github.com/livingdocsIO/livingdocs-editor/pull/3961)
  * [Base Work - Properties Panel Refactoring](https://github.com/livingdocsIO/livingdocs-editor/pull/3951)
  * [Base Work - Resolve Includes](https://github.com/livingdocsIO/livingdocs-editor/pull/3949)
  * [Example - Teaser Include on Example Server](https://github.com/livingdocsIO/livingdocs-server/pull/3235)
  * [Documentation - TODO: Beni]()


## Videos :tada:

We introduce videos in Livingdocs with these abilities:

- upload videos and set metadata in media library
- upload videos and set metadata in editor via drag + drop / upload button
- import videos via public API
- Add project configuration for mediaVideo MediaType
- Add new directive `doc-video` in a livingdocs design

In the upcoming releases we will bring in some improvements and make the video feature more stable.

References:
  * [Editor PR with Screenshots](https://github.com/livingdocsIO/livingdocs-editor/pull/3957)
  * [Editor PR with Improvements (drag+drop from filesystem)](https://github.com/livingdocsIO/livingdocs-editor/pull/3989)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3234)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/337)





# Breaking Changes :fire:

## Migrate the database :fire:

It's a simple/fast migration with no expected data losses.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 142-add-legacy-design-name.js
#   rename document_migrations.design_name to target_design_name
# migration - 143-drop-unused-postgres-extensions.js
#   drop unused uuid-ossp extension
# migration - 144-add-missing-primary-keys.js
#   add missing primary keys to tables to support replication better
# migration - 145-document-content-types.js
#   introduce document_content_types table to support migrations better in the future
# migration - 146-add-metadata-id-to-revisions.js
#   add document_revisions.metadata_id to support metadata to document/publication relations better in the future
# migration - 147-add-user-sessions.js
#   add user_sessions table to support new auth workflow
livingdocs-server migrate up
```

## Drop Support for Elasticsearch < 6.8.5 :fire:

:fire: The support for Elasticsearch versions < 6.8.5 has been dropped. Please update your Elasticsearch cluster to Elasticsearch >= 6.8.5.

**Important!** You have to do an Elasticsearch update to >=6.8.5 before installing the December release. How to to a rolling upgrade is documented [here](https://www.elastic.co/guide/en/elasticsearch/reference/current/rolling-upgrades.html).


References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3275)

## Elasticsearch Indexes :fire:

#### Server Configuration
- 🔥 moved server config `search.articlePublicationIndexEnabled` to `elasticIndex.documentPublicationIndexEnabled`
- 🔥 removed server config `search.articlePublicationIndex`. The publication index name is now auto generated: `${indexNamePrefix}-li-document-publications-index`

#### CLI
- 🔥 removed `livingdocs-server es-publication-delete-index` use `livingdocs-server elasticsearch-delete-index --handle=li-publications -y` instead
- 🔥 removed `livingdocs-server es-publication-reindex` use `livingdocs-server elasticsearch-index --handle=li-publications -y` instead

#### Environment Config

We automatically create a publication index for the public API. Therefore you **must** define an `indexNamePrefix` for every environment. The definition of `indexNamePrefix` is free, but we suggest a pattern like `${your-company}-${environment}`.

🔥  Define an `indexNamePrefix` for every environment

```js
elasticIndex: {

  // every index name will be prefixed to prevent name clashes
  // the index will be created with this pattern: `${indexNamePrefix}-${handle}-index`
  indexNamePrefix: 'your-company-local',
}
```

#### Publication Index for public API

🔥 Run a background index job for the publication index

To support future updates, we did an internal update where we define Elasticsearch aliases pointing on an index. With this change, you need to re-index the publication index used for the public API search endpoint.

After the deployment, please **immediately** run this cli task (the publication index will be empty after the deployment):

```bash
livingdocs-server elasticsearch-index --handle=li-publications -y
```


#### public API publications search

🔥  When using the public API search endpoint (`/api/v1/publications/search`), then you have to reindex all publications, with the command `livingdocs-server elasticsearch-index --handle=li-publications -y`.

When you start the new server version, the publication index is empty. To use the publication index in production for the public API as fast as possible, you have 2 options:

- 1) Start a sidekick container with the new server version and make a full background index with `livingdocs-server elasticsearch-index --handle=li-publications -y`. As soon as it's done, you can start your casual servers with the new server version
- 2) If you want to deploy/start your new server version without a preparation step, you can index the most recent publication with an additional parameter `--since`. For example `livingdocs-server elasticsearch-index --handle=li-publications --since 1m -y` does indexing all publications published within the last month. As soon as you're done with this indexing step, you can run another background without `--since` argument to index all publications.


## SSO Logins :fire:

With the improved [authentication workflow](https://github.com/livingdocsIO/livingdocs-server/pull/3225), we have some additional [breaking changes](https://github.com/livingdocsIO/livingdocs-planning/issues/4140) for SSO Logins. If the callback URL for SSO does not match the editorUrl, we set the auth cookies for a wrong domain leading to issues when logging in.

**Migrating an existing SSO login**

With cookies being set on a new URL, the SSO Logins need to be re-configured. Do the following:

1. Make sure your `editor__public_host` env variable is set to the editor URL (e.g. `https://edit.livingdocs.io`)
2. Change all callback URLs for your SSO provider to the pattern `https://{editorUrl}/proxy/auth/{provider}/callback`. For the livingdocs service this looked e.g. as follows: `auth__connections__github__config__callbackURL = https://edit.livingdocs.io/proxy/auth/github/callback`. (NOTE: depending on your traefik setup it might also require `proxy/api` instead of `/proxy`).
3. In the settings for your social providers, allow the new callback URLs (for FB for example we had to allow the redirect URL `https://edit.livingdocs.io/proxy/auth/facebook/callback` in our Facebook app)



## Migration to Redis Streams :fire:

- :fire: Existing messages from `bull` won't be processed anymore.
- :fire: If you had pending index or imports, you'll need to restart them. Our whole setup already supported retries everywhere except in the importer of the public api. It's probably best if you re-trigger the imports after deployment.
- ❌ Removed bull dashboard and replaced it with an operations screen in the admin interface of the editor.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3224)

## Slug Metadata in Slug Routing Pattern :fire:

If you activated the routing feature and if you are using a route pattern containing `:slug` and at the same time you have a metadata property with the handle `slug` the behavior will change in such a way that the route pattern for `:slug` will be built out of the `slug` metadata property value and not the document title. In most cases this is what you want. If it is not, you can rename the handle of your existing slug metadata property to prevent clashes.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3227)

## DocumentsApi - Removed functions :fire:

- :fire: Removed `DocumentEntity.find` and `DocumentEntity.findById` methods, please use the official apis
- :fire: Removed `RevisionEntity.find` and `RevisionEntity.findById` methods, please use the official apis
- :fire: Changed parameters of `documentApi.getLocks` from `(documentId)` to `({projectId, documentId})`, so we can save a few roundtrips to check whether a user is allowed to access the document.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3237)

## S3 Storage Default :fire:

:fire: The S3 default changed from `{ACL: 'public-read'}` to `undefined` - it now uses the bucket ACL-defaults.

#### How to revert to the behaviour before the release :fire:
To restore the behaviour you can explicitly pass the `{ACL: 'public-read'}` in `(images|files).storage.config.params.ACL`

```js
storage: {
  strategy: 's3',
  config: {
    bucket: 'li-bucket-dev',
    region: 'eu-central-1',
    accessKeyId: 'secret',
    secretAccessKey: 'secret',
    params: {
      ACL: 'public-read' // <--------- add this to go back to the old behavior
    }
  }
}
```

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3262)

## DocumentRelationApi - Changed Params :fire:

🔥 Changed params on `documentRelationApi.setDocumentEmbedReferences` from `(documentVersion)` to `({documentVersion, trx})`

NOTE: The new param `trx` is optional and only necessary if you want to call within a transactional context. If you do pass it, you are responsible to call `trx.commit` or `trx.rollback` when you're done.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3259)

## Index Feature - Removed publicationTransformModule :fire:

- 🔥 Remove server config option search.indexer.publicationTransformModule
- 🔥 Remove parameter publication-transform-module in livingdocs-server es-publication-reindex task

Note: This change should have no consequences for customers.

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3222)

## Index Feature - Removed/Renamed Functions :fire:

- 🔥 Removed `req.accessToken` from all requests. Please migrate to `req.verifiedToken.bearerToken`
- 🔥 Removed `searchManager.putDocument`. Please migrate to `indexingApi.addJob` that executes the same method internally

References: [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3187)

## Security - User access tokens require valid cookies

- 🔥 Cypress helpers need some adaptions to correctly support cookies.

Our core implementation can serve as reference for a cypress login helper: https://github.com/livingdocsIO/livingdocs-editor/blob/master/cypress/support/liLogin.js/#L69

- 🔥 All requests against the server using an user access token require a valid session and the cookies that belong to it.

You may need to allow credentials or forwarding cookies if you have been working with User tokens. _(API Tokens should still work exactly as before!)_

Example an `axios` instance using the withCredentials flag
```
const axios = require('axios').create({..., withCredentials: true})
```

## Editor CSS Class Renamings :fire:

:fire: If you've done CSS modifications based on the original upstream classes in the editor please look into this PR. We did a lot of small refactorings/renamings.

References: [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4015)


# APIs :gift:

## Public API

For all endpoints documentation, look into your editor's public API doc - 'https://your-editor.com/public-api'.

#### Added Endpoint for a MediaLibrary Import :gift:

:gift: `POST /api/v1/import/mediaLibrary`

References:

  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3895)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3152)


#### Added Endpoint for a MediaLibrary Metadata Update :gift:

:gift: `PATCH /api/v1/mediaLibrary/:id`

References:
  * Documentation - 'https://your-editor.com/public-api'
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/4014)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3267)


#### Added Endpoints for Document Lists :gift:

- :gift: `GET /api/v1/document-lists`  Search endpoint for document lists
- :gift: `GET /api/v1/document-lists/:id` Get a document list by :id

References:
  * Documentation - 'https://your-editor.com/public-api'
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3956)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3226)


#### Added Endpoint for a Video Import :gift:

:gift: `POST api/v1/import/videos`

References:
  * Documentation - 'https://your-editor.com/public-api'
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3234)





## Server Events API

We added new events to the sever events API
- :gift: `mediaLibraryEntry.create`
- :gift: `mediaLibraryEntry.update`
- :gift: `mediaLibraryEntry.archive`

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/345)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3255)




# Internal Changes

## Beta Endpoints for Publications :gift:

We added a new base endpoint `/api/beta/`. This allows us to expose things on the public API we are not
sure enough yet, to introduce it on the `v1` endpoint that we can never break.

The first 2 introduced beta endpoints are already existing and have the same format on `v1`, but extend the response
with `references`. This might break in the future.

New endpoints:
- :gift: `GET /api/beta/documents/:documentId/latestPublication`
- :gift: `GET /api/beta/documents/latestPublications`

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/3254)


# Other Changes

### Security

* Registration: Do not allow long usernames or // in a username [livingdocs-server #3257](https://github.com/livingdocsIO/livingdocs-server/pull/3257) :gift:
* Registration: Escape user input in email html [livingdocs-server #3256](https://github.com/livingdocsIO/livingdocs-server/pull/3256) :gift:

### Design

* Document reference polish
  * Part I  [livingdocs-editor #3897](https://github.com/livingdocsIO/livingdocs-editor/pull/3897) :gift:
  * Part II [livingdocs-editor #3950](https://github.com/livingdocsIO/livingdocs-editor/pull/3950) :gift:
* Use consistent button styles on metadata screen [livingdocs-editor #3918](https://github.com/livingdocsIO/livingdocs-editor/pull/3918) :gift:
* Improve conflict mode [livingdocs-editor #3927](https://github.com/livingdocsIO/livingdocs-editor/pull/3927) :gift:
* Overhauled Link-Buttons [livingdocs-editor #3982](https://github.com/livingdocsIO/livingdocs-editor/pull/3982) :gift:
* Refactor: Remove Atomic Design [livingdocs-editor #4012](https://github.com/livingdocsIO/livingdocs-editor/pull/4012) :gift:
* A huge amount of design fixes for release-2020-12 [livingdocs-editor #4015](https://github.com/livingdocsIO/livingdocs-editor/pull/4015) :gift:
* Updated mail templates [livingdocs-server #3203](https://github.com/livingdocsIO/livingdocs-server/pull/3203) :gift:

### Improvements

#### Editor

* Login: Show login buttons for all auth providers [livingdocs-editor #3934](https://github.com/livingdocsIO/livingdocs-editor/pull/3934) :gift:
* Dashboard: Scroll to last article [livingdocs-editor #4006](https://github.com/livingdocsIO/livingdocs-editor/pull/4006) :gift:
* Operation Screen
  * Support design bumps from referenced to embedded designs via UI [livingdocs-editor #3932](https://github.com/livingdocsIO/livingdocs-editor/pull/3932)
  * Migrate server operations screen to websockets [livingdocs-server #3192](https://github.com/livingdocsIO/livingdocs-server/pull/3192) :gift:
  * Improve import jobs log in editor [livingdocs-server #3202](https://github.com/livingdocsIO/livingdocs-server/pull/3202) :gift:
* Allow to register icons in downstream [livingdocs-editor #3925](https://github.com/livingdocsIO/livingdocs-editor/pull/3925) :gift:

#### Server

* Media services improvements [livingdocs-server #3243](https://github.com/livingdocsIO/livingdocs-server/pull/3243) :gift:
* Proxy: Add support for proxying websockets [livingdocs-editor #3905](https://github.com/livingdocsIO/livingdocs-editor/pull/3905) :gift:
* APIs: Serve Cache-Control header in authenticated requests [livingdocs-server #3280](https://github.com/livingdocsIO/livingdocs-server/pull/3280) :gift:
* Migrations: Support `migrateAsync` method on migration files [livingdocs-server #3204](https://github.com/livingdocsIO/livingdocs-server/pull/3204) :gift:
* DataSources: Support documentId in params [livingdocs-editor #3896](https://github.com/livingdocsIO/livingdocs-editor/pull/3896) :gift:
* Postgres:
  * Add missing primary keys to support logical replication [livingdocs-server #3236](https://github.com/livingdocsIO/livingdocs-server/pull/3236) :gift:
  * Introduce a `document_content_types` table to keep the media types similar [livingdocs-server #3238](https://github.com/livingdocsIO/livingdocs-server/pull/3238) :gift:
* Example Server: Add Twitch include example [livingdocs-server #3246](https://github.com/livingdocsIO/livingdocs-server/pull/3246) :gift:
* Notifications: Pass server error messages to li-notifications [livingdocs-editor #3929](https://github.com/livingdocsIO/livingdocs-editor/pull/3929) :gift:

### Bugfixes

* Metadata: Fix metadata save trigger [livingdocs-editor #3967](https://github.com/livingdocsIO/livingdocs-editor/pull/3967) :beetle:
* MediaLibrary
  * Fix drop behavior for galleries [livingdocs-editor #3884](https://github.com/livingdocsIO/livingdocs-editor/pull/3884) :beetle:
  * Correctly handle drops in all browsers [livingdocs-editor #3878](https://github.com/livingdocsIO/livingdocs-editor/pull/3878) :beetle:
* Filter: Allow strings for dateRange query [livingdocs-editor #3941](https://github.com/livingdocsIO/livingdocs-editor/pull/3941) :beetle:
* Public API: Fix public API docs [livingdocs-editor #3976](https://github.com/livingdocsIO/livingdocs-editor/pull/3976) :beetle:
* Operation Screen
  * Correctly indicate total users [livingdocs-editor #4002](https://github.com/livingdocsIO/livingdocs-editor/pull/4002) :beetle:
  * Fix Add Member Screen for users that are already in a group [livingdocs-editor #4004](https://github.com/livingdocsIO/livingdocs-editor/pull/4004) :beetle:
  * Display error message during user create on admin screen [livingdocs-editor #4007](https://github.com/livingdocsIO/livingdocs-editor/pull/4007) :beetle:
* Directives
  * Don't show UI elements in non-interactive iframe view [livingdocs-editor #4008](https://github.com/livingdocsIO/livingdocs-editor/pull/4008) :beetle:
  * Set clean data from paramsSchema form instead of reactive vue objects to the include directive [livingdocs-editor #4018](https://github.com/livingdocsIO/livingdocs-editor/pull/4018) :beetle:
* Fix focus reset and error log in embedded teaser [livingdocs-editor #4028](https://github.com/livingdocsIO/livingdocs-editor/pull/4028) :beetle:
* Desknet: Fix Desk-Net Plugin for embedded designs [livingdocs-server #3183](https://github.com/livingdocsIO/livingdocs-server/pull/3183) :beetle:
* Imatrics: Fix tag slugging [livingdocs-server #3188](https://github.com/livingdocsIO/livingdocs-server/pull/3188) :beetle:
* Includes: Allow `ui.label` for paramsSchema entries [livingdocs-server #3239](https://github.com/livingdocsIO/livingdocs-server/pull/3239) :beetle:

---

**Icon Legend**

* Breaking changes: :fire:
* Feature: :gift:
* Bugfix: :beetle:
* Chore: :wrench:
