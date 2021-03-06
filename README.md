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
$ npm run build
```

Now the final site will be in `_site`

## Docs: Key things to knw

### Generally how this works
- Eleventy will automatically scan for `.md` files, will translate it into HTML, and will put the HTML into a `_site` output directory.
- The `.md` files all have Markdown frontmatter (the YAML key-value pairs in-between the `---`):
  - `layout:` is a special Eleventy variable that refers to what template to use in `_includes`
  -  You can define other variables yourself then use them in templates, see e.g. `title` in the `.md` files and how it's referenced in template `.njk` fiels
  - After the frontmatter is the contents of the page.
- The templates are in `_includes`, and they are HTML with variables that look like this: `{{ variableName }}`
  - `{{ content }}` is a special variable that references the contents of the page - the examples also use the [`safe` filter](https://mozilla.github.io/nunjucks/templating.html#safe), so it looks like `{{ content | safe }}`
  - Other freeform template variables are defined in frontmatter

### Other details
- This uses the Nunjucks (.njk) templating system, which doesn't need to be configured because Eleventy will automatically scan for and process all files with these extensions by default: [template formats](https://www.11ty.dev/docs/config/#template-formats)
  - `.md` is also included by default
  - ...but this `README` file is included in `.eleventyignore`, so it won't be included in the site output directory despite having a `.md` extension: [ignore files](https://www.11ty.dev/docs/ignores/)
- Eleventy will put the generated assets into `_site` by default: [output dir](https://www.11ty.dev/docs/config/#output-directory)
- Eleventy will search for templates in `_includes` by default: [includes dir](https://www.11ty.dev/docs/config/#directory-for-includes)
- The templates I used also take advantage of [layout chaining](https://www.11ty.dev/docs/layout-chaining/)
- `.eleventy.js` is the Eleventy config file, which, because I'm using the above defaults, just needs to tell Eleventy to do a passthrough copy of the `css/` directory: [passthrough file copy](https://www.11ty.dev/docs/copy/)
