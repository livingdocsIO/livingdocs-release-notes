**Attention:** If you skipped one or more releases, please also check the release-notes of the skipped ones.

# Table of content
- [Patches](#repositories)
- [Highlights](#highlights)
- [Breaking Changes](#breaking-changes-fire)
- [Other Changes](#other-changes)

# Newsletter

* Newsletter: TODO
* Link to subscription form: https://confirmsubscription.com/h/j/61B064416E79453D


# Repositories

This release consists of the following new versions of the `livingdocs-server` and the `livingdocs-editor`:

Package | Version
--- | ---
`@livingdocs/server` | `release-2020-05`
`@livingdocs/editor` | `release-2020-05`

## Livingdocs Server
How to require the server in your package.json:
```json
"dependencies": {
  "@livingdocs/server": "release-2020-05",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-server/tree/release-2020-05

### Livingdocs Server Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-server/releases/tag/v??.?.?): TODO



## Livingdocs Editor
How to require the editor in your package.json:
```json
"dependencies": {
  "@livingdocs/editor": "release-2020-05",
}
```

- Link to the release branch:
  https://github.com/livingdocsIO/livingdocs-editor/tree/release-2020-05

### Livingdocs Editor Patches
- [v??.?.?](https://github.com/livingdocsIO/livingdocs-editor/releases/tag/v??.?.?): TODO



# Highlights

## Editor UI Changes

..........TODO: Lukas wording.............

### Canvas added
We have now removed the side-panel for properties and comments. Instead we have a canvas on the right side of the document and scrolling of the document is on the right side of the canvas.

![image](https://user-images.githubusercontent.com/4352425/80966827-8f6d8c00-8e15-11ea-8335-d1c042d2611a.png)

### Comments moved to Canvas
The comments are now shown in the canvas. They can be shown or hidden in the collab-bar. The default is that the open comments will be shown and the resolved comments will be hidden.
![image](https://user-images.githubusercontent.com/4352425/80967132-26d2df00-8e16-11ea-89f4-66e29a21460c.png)

### properties-panel
The properties-panel is now not anymore in the side-panel. It is now over the canvas and can be closed so that the cards behind can be selected.
![image](https://user-images.githubusercontent.com/4352425/80968640-9c3faf00-8e18-11ea-9cec-9998f0e82ef3.png)


## Live Coverage :tada:

Live coverage mode enables teams of editors to collaborate under moderation. This is particularly useful for things like live tickers. Every change is written as a proposal (draft) that can be reviewed and accepted. Only accepted changes are published when an editor presses the publish button. As things can get a bit messy with many people writing proposals, the UI allows you to hide proposals to see what is currently published.

![image](https://user-images.githubusercontent.com/4352425/81931412-5938c500-95ea-11ea-8358-8e67145af59a.png)

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3446)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2920)


## Translations :tada:

Livingdocs now supports translations. You can for example create an article in german and translate this document into another language like english.

![Translations](https://user-images.githubusercontent.com/39759830/80695632-79d72a00-8ad6-11ea-90e2-3e5107336d5c.gif)


References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3436)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2903)


## Webhooks :tada:

Livingdocs adds Webhooks to the core system. Webhooks can be configured to call a 3rd-party endpoint on `document.published` and `document.unpublished` event.
Check out the [documentation](https://github.com/livingdocsIO/livingdocs/pull/294) if you want to know more.

![webhooks](https://user-images.githubusercontent.com/172394/81531875-c5ee5e00-9363-11ea-868f-3ea5cb1a952a.png)

References:
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/294)
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3445)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2907)


## Custom Document Preview :tada:

Livingdocs now supports a custom document preview. You are now able to register your own rendering function to generate a preview of
your delivery system like your webpage or an RSS feed. It's even thinkable to generate a truly native app preview. For more information on how to do it look into the [Server Pull Request](https://github.com/livingdocsIO/livingdocs-server/pull/2887).

![document-preview3](https://user-images.githubusercontent.com/172394/81532319-79575280-9364-11ea-8d38-7f8fbc34b43e.png)

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3410)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2887)


## Delivery Links :tada:

Delivery links are shown in the publish panel when a document is published. These links are usually used to check if the document has been published correctly on the website.
You can now configure more than one of these links through channelConfig (or UI).
Check out the [Editor Pull Request](https://github.com/livingdocsIO/livingdocs-editor/pull/3453) if you want to know more.

![delivery-link](https://user-images.githubusercontent.com/172394/81531842-b66f1500-9363-11ea-93c6-c1eec1ecb8d5.png)

References:
  * [Editor PR](https://github.com/livingdocsIO/livingdocs-editor/pull/3453)
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2924)
  * [Documentation](https://github.com/livingdocsIO/livingdocs/pull/301)


## 2 Times Faster Image Upload :tada: :speedoat:

If you upload/drop an image into Livingdocs, the image upload is now twice as fast with the new `libvips` strategy.

### Dropped image format support :fire:

- `libvips` does not support `.bmp`images, but supports HEIC (iphone format for images)

```js
// change your environment config on the server to upload images twice as fast as with the 'imagemagick' strategy
images: {
  processingStrategy: 'libvips'
}
```

References:
  * [Server PR](https://github.com/livingdocsIO/livingdocs-server/pull/2925)


# Breaking Changes :fire:

## Migrate the database

The migration is simple, the duration is short and there are no datalosses expected on up-/downgrade.

```sh
# run grunt migrate to update to the newest database scheme
# migration - 135-add-webhooks.js.js
#   create webhooks table
livingdocs-server migrate up
```

# Other Changes

### Features

* Metadata: Add `li-publish-date` metadata plugin [livingdocs-server #2929](https://github.com/livingdocsIO/livingdocs-server/pull/2929) :gift:
* Elasticsearch: Indexes and support `numberOfReplicas` and `numberOfShards` configs [livingdocs-server #2911](https://github.com/livingdocsIO/livingdocs-server/pull/2911) :gift:
* Image: Add remove image button for an existing image on the properties panel [livingdocs-editor #3444](https://github.com/livingdocsIO/livingdocs-editor/pull/3444) :gift:
* Metadata: Support dataSources/dataProvider and more data types in Select/Multiselect [livingdocs-editor #3458](https://github.com/livingdocsIO/livingdocs-editor/pull/3458) :gift:
* Remote includes beta: [livingdocs-editor #3451](https://github.com/livingdocsIO/livingdocs-editor/pull/3451)


### Improvements

* ChannelConfig: Handle/validate static and dynamic channelConfig the same way [livingdocs-server #2906](https://github.com/livingdocsIO/livingdocs-server/pull/2906) :gift:
* References: Move the extraction from the editor to the server (on create / on save) [livingdocs-server #2901](https://github.com/livingdocsIO/livingdocs-server/pull/2901) :gift:
* Metadata: Add default item for `liMetaSelect` component [livingdocs-editor #3423](https://github.com/livingdocsIO/livingdocs-editor/pull/3423) :gift:
* Config: Allow to configure metadata reference search to only show published records [livingdocs-editor #3466](https://github.com/livingdocsIO/livingdocs-editor/pull/3466) :gift:

### Bugfixes

* Import: Add image service URL to imported image [livingdocs-server #2889](https://github.com/livingdocsIO/livingdocs-server/pull/2889) :beetle:
* Images: Fix image extraction bug [livingdocs-server #2896](https://github.com/livingdocsIO/livingdocs-server/pull/2896) :beetle:
* Imatrics: Config fixes [livingdocs-server #2923](https://github.com/livingdocsIO/livingdocs-server/pull/2923) :beetle:
* History: 
  * Fix history user colors [livingdocs-editor #3424](https://github.com/livingdocsIO/livingdocs-editor/pull/3424) :beetle:
  * Fix history char counter & PO-truck [livingdocs-editor #3431](https://github.com/livingdocsIO/livingdocs-editor/pull/3431) :beetle:
* Navigation: Fix spacing / scrolling [livingdocs-editor #3440](https://github.com/livingdocsIO/livingdocs-editor/pull/3440) :beetle:

  ---
  **Icon Legend**
  * Breaking changes: :fire:
  * Feature: :gift:
  * Bugfix: :beetle:
  * Chore: :wrench:
