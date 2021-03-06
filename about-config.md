---
layout: subpage
title: a little more on config
---

You can configure eleventy using an `.eleventy.js` file.

I found the 11ty defaults to be quite good so you probably don't have to configure too much if you don't want to. The one thing I set was a [passthrough copy](https://www.11ty.dev/docs/copy/) for the css directory so that it gets copied into the output directory, which is `_site` [by default](https://www.11ty.dev/docs/config/#output-directory).
