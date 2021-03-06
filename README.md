# Eleventy Example

This is an example of a very simple [eleventy](https://www.11ty.dev/) site.

## To install and run locally

```
$ npm install
$ npm start
```

This will launch the eleventy watcher with hot-reloading so that you can live preview your changes.

## To generate the site

```
$ npm build
```

Now the final site will be in `_site`

## Docs: Key config & things to know

- This uses the Nunchucks (.njk) templating system, which doesn't need to be configured because Eleventy will automatically scan for and process all files with these extensions by default: [template formats](https://www.11ty.dev/docs/config/#template-formats)
  - `.md` is also included by default
  - ...but this `README` file is included in `.eleventyignore`, so it won't be included in the site output directory despite having a `.md` extension: [ignore files](https://www.11ty.dev/docs/ignores/)
- Eleventy will put the generated assets into `_site` by default: [output dir](https://www.11ty.dev/docs/config/#output-directory)
- Eleventy will search for templates in `_includes` by default: [includes dir](https://www.11ty.dev/docs/config/#directory-for-includes)
- The templates I used also take advantage of [layout chaining](https://www.11ty.dev/docs/layout-chaining/)
- `.eleventy.js` is the Eleventy config file, which, because I'm using the above defaults, just needs to tell Eleventy to do a passthrough copy of the `css/` directory: [passthrough file copy](https://www.11ty.dev/docs/copy/)
