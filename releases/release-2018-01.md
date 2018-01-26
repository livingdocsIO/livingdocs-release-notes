**Legend of Changes**

* Breaking changes: :fire:
* Feature: :gift:
* Bugfix: :beetle:
* Chore: :wrench:


# Highlights
* Editor
  * allow to replace an image by an image drop [#1769](https://github.com/upfrontIO/livingdocs-editor/pull/1769) :gift:
* Document History
  * improved document history [#1762](https://github.com/upfrontIO/livingdocs-server/pull/1762) :gift: :fire:
* Project
  * specify homepage in project settings [#1767](https://github.com/upfrontIO/livingdocs-editor/pull/1767) [#1751](https://github.com/upfrontIO/livingdocs-server/pull/1751) :gift:
* Design
  * improved design loader [#1803](https://github.com/upfrontIO/livingdocs-editor/pull/1803) [#1787](https://github.com/upfrontIO/livingdocs-server/pull/1787) :gift: :fire:
* Lists
  * mark list with pending changes with a blue dot [#1792](https://github.com/upfrontIO/livingdocs-editor/pull/1792) [#1776](https://github.com/upfrontIO/livingdocs-server/pull/1776) :gift:
* Collaboration
  * fix the behaviour of read-only mode during collaboration [#1791](https://github.com/upfrontIO/livingdocs-editor/pull/1791) :beetle:



# Breaking Changes / Required Actions
...





# Other Changes
* Editor
  * add visibility config switch for the "transform component" in the side panel [#1793](https://github.com/upfrontIO/livingdocs-editor/pull/1793) :wrench:
  * disable copy button on saving [#1795](https://github.com/upfrontIO/livingdocs-editor/pull/1795) :beetle:
  * keep image focus after cropping [#1769](https://github.com/upfrontIO/livingdocs-editor/pull/1769) :beetle:
* Elasticsearch
  * make elasticsearch apiVersion configurable [#1754](https://github.com/upfrontIO/livingdocs-server/pull/1754) :gift:
  * replace top-level filter parameter with post_filter [#1726](https://github.com/upfrontIO/livingdocs-server/pull/1726) :wrench:
* Hooks
  * handle resolveHandle errors [#1766](https://github.com/upfrontIO/livingdocs-server/pull/1766) :beetle:
  * publication hooks registration ignores missing projects/channels [#1771](https://github.com/upfrontIO/livingdocs-server/pull/1771) :gift:
* Print
  * advanced woodwing infobox [#1710](https://github.com/upfrontIO/livingdocs-server/pull/1710) :gift:
  * send `<br>` to printAPI [#1746](https://github.com/upfrontIO/livingdocs-server/pull/1746) :wrench:
  * set publicationDates period to 30d [#1778](https://github.com/upfrontIO/livingdocs-editor/pull/1778) :wrench:
* Redis
  * use ioredis instead of node-redis [#1773](https://github.com/upfrontIO/livingdocs-server/pull/1773) :wrench:
* Design loader
  * Fix assets.public_url camelization in design-loader [#1788](https://github.com/upfrontIO/livingdocs-server/pull/1788) :wrench:
* Tests
  * Get headless chromium properly to work [#1784](https://github.com/upfrontIO/livingdocs-editor/pull/1784) :beetle:
