# Nasqueron documentations

**This site contains ONLY the cover page. Documentations subdirectories are deployed by Salt states in rOPS and updated by CI jobs.**

## Setup

To download a working development copy of the site:

```bash
git clone https://devcentral.nasqueron.org/source/docs-www.git
```

Then open the folder in your command line, and install the needed dependencies:

```bash
cd docs-www
npm install
```

Finally, run `npm start` to run Gulp. Your finished site will be created in a folder called `dist`, viewable at this URL:

```
http://localhost:8000
```

To create compressed, production-ready assets, run `npm run build`.

## Update list of docs

The list of docs is stored in `src/data/docs.yml`.
Add an entry to this file for each subdirectory.

## Based on the Zurb Foundation template

This site prototype is prepared with the official ZURB Template for use with [Foundation for Sites](http://foundation.zurb.com/sites). We use this template at ZURB to deliver static code to our clients. It has a Gulp-powered build system with these features:

- Handlebars HTML templates with Panini
- Sass compilation and prefixing
- JavaScript module bundling with webpack
- Built-in BrowserSync server
- For production builds:
  - CSS compression
  - JavaScript compression
  - Image compression
