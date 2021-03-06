# Eleventy Example

This is an example of a very simple [eleventy](https://www.11ty.dev/) site.

## To install and run locally

Clone the repo locally and then run:

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

## Documentation

### How this works in general
- The `package.json` file specifies eleventy as a dev dependency. `eleventy --serve` is defined as the `npm start` command.
- When Eleventy runs, it will scan for `.md` files, translate the `.md` files into HTML, and will put the HTML into a `_site` output directory.
- The `.md` files all have Markdown frontmatter (the YAML key-value pairs in-between the `---`) that specify further how it should be converted into HTML
  - `layout:` is a special Eleventy variable that refers to what template to use in `_includes`
  -  You can define your own variables then use them in templates, see e.g. `title` in the `.md` files and how it's referenced in template `.njk` fiels
  - After the frontmatter is the contents of the page.
- The templates are in `_includes`, and they are HTML with variables that look like this: `{{ variableName }}`. Eleventy will use the template referenced by the frontmatter and fill in the values for the variables as part of the translation from Markdown to HTML.
  - `{{ content }}` is a special variable that references the contents of the page.
    - The examples also use the [`safe` filter](https://mozilla.github.io/nunjucks/templating.html#safe), so it looks like `{{ content | safe }}`
  - Other freeform template variables are defined in frontmatter

### Details
- This uses the Nunjucks (.njk) templating system, which doesn't need to be specified in configs because Eleventy will automatically scan for and process all files with these extensions by default: [template formats](https://www.11ty.dev/docs/config/#template-formats)
  - `.md` is also included by default
  - ...but this `README` file is included in `.eleventyignore`, so it won't be included in the site output directory despite having a `.md` extension: [ignore files](https://www.11ty.dev/docs/ignores/)
- Eleventy will put the generated assets into `_site` by default: [output dir](https://www.11ty.dev/docs/config/#output-directory)
- Eleventy will search for templates in `_includes` by default: [includes dir](https://www.11ty.dev/docs/config/#directory-for-includes)
- The templates I used also take advantage of [layout chaining](https://www.11ty.dev/docs/layout-chaining/)
- `.eleventy.js` is the Eleventy config file, which, because I'm using the above defaults, just needs to tell Eleventy to do a passthrough copy of the `css/` directory: [passthrough file copy](https://www.11ty.dev/docs/copy/)

### Aside: An odd style choice

It'd be neater/better if I created a separate `src` directory where I put the (non-README) `.md` files and `css/` directories. But that involved slightly more config, so I thought it'd be ever-so-slightly easier understand if I forwent a `src` directory.

If this decision bugs you, add a `src` directory for practice! 😄
