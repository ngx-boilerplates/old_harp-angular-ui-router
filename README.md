![AngularJS Express](http://i.imgur.com/nTj9QgN.png)

## Boilerplate for AngularJS Express

**Zero configuration required!**

This boilerplate combines all best practices of:

- the official [Google recommended AngularJS application structure](https://docs.google.com/document/d/1XXMvReO8-Awi1EZXAXS4PzDzdNvV6pGcuaF4Q9821Es/pub)
- the fantastic [AngularJS styleguide](https://github.com/toddmotto/angularjs-styleguide) by [Todd Motto](http://toddmotto.com/)
- the lovely [HarpJS](http://harpjs.com) web server

and includes:

- Pre-configured AngularJS 1.3 application
- Pre-configured ui-router
- Pre-configured Gulpfile for concatenation, linting, unit testing, livereload and selectively copying bower component files
- Pre-configured Karma configuration for running unit tests
- [HarpJS](http://harpjs.com/) preprocessor support e.g. include a markdown file in your Jade file
- [HarpJS](http://harpjs.com/) compilation support to compile your application to a static version for deployment

## Installation

First make sure you have the [AngularJS Express](https://github.com/angular-express/angular-express) CLI installed:

```sh
$ sudo npm install -g ngx-cli
```

Then initialize the boilerplate:

```sh
$ ngx init -b harp-angular-ui-router myproject
```

Change the directory to the new `myproject` directory:

```sh
$ cd myproject
```

Install the latest dependencies:

```sh
$ npm install
$ bower install
```

Run gulp to assemble the concatenated AngularJS library:

```sh
$ gulp
```

Start the harp server from your project directory:

```sh
$ harp server
```

And navigate to `http://localhost:9000` in your browser:

![Homepage](http://i.imgur.com/dORKysf.png)

## Adding AngularJS Express components

Adding additional AngularJS Express components to your application is easy.

For example:

```bash
# Install a ui-router state not found handler component
$ ngx install ui-router-state-not-found-handler

# Install a ui-router state change error handler component
$ ngx install ui-router-state-change-error-handler

# Install less helper classes
$ ngx install less-padding-helper-classes
```

Components are downloaded from GitHub and installed in the `public/components` directory where you can customize it to your needs.

> Check the [official AngularJS Express components directory](https://github.com/ngx-components) for all available components.

You can also easily include components from your own GitHub account like this:

```bash
# Install your custom component
$ ngx install github-username/component-repo-name
```

> Check out the official [AngularJS Express](https://github.com/angular-express/angular-express) documentation for more info.

## How it works

All action happens in the `public` directory, so let's have a look at its structure:

```sh
public
├── 200.jade
├── _build                          # main _build directory for global app stuff
│   ├── app.config.router.js        # Configure the router
│   ├── app.less                    # Global app styles that you want Gulp to add to /public/build/css/app.css
│   ├── app.module.js               # Main 'app' module
│   └── app.module.spec.js          # Sample unit tests for main 'app' module
├── build                           # Build directory where files built by Gulp are saved
│   ├── css
│   │   ├── app.css                 # All .less files from _build directories are concatenated here
│   │   └── app.min.css             # Minified version for production
│   └── js
│       ├── app.js                  # All .js files from _build directories are concatenated here
│       └── app.min.js              # Minified version for production
└── components
    ├── footer                      # Example footer component
    │   ├── _build                  # Component _build directory with files that you want Gulp to build
    │   │   └── footer.less         # Styles that you want to add to /public/build/css/app.css
    │   └── footer.jade             # Jade file will be compiled to HTML automatically
    ├── header                      # Example header component
    │   ├── _build                  # Component _build directory with files that you want Gulp to build
    │   │   └── header.less         # Styles that you want to add to /public/build/css/app.css
    │   └── header.jade             # Jade file will be compiled to HTML automatically
    └── homepage                    # Example homepage component
        ├── _build                  # Component _build directory with files that you want Gulp to build
        │   └── homepage.routes.js  # JavaScript code that you want to add to /public/build/js/app.js
        └── homepage.jade           # Jade file will be compiled to HTML automatically
```

## Compiling to static

To build a static version for deployment, run:

```sh
$ harp compile . dist
```

This will create a `dist` directory with all files ready to be hosted statically.

## Unit tests

Gulp is configured to automatically run all tests in `public/**/_build/**/*.spec.js`.

## Gulp

Gulp is configured to:

- jshint all JavaScript files in the `public` directory
- concatenate all JavaScript files in all `public/**/_build` directories to `public/build/js/app(.min).js`
- concatenate all LESS files in all `public/**/_build` directories to `public/build/css/app(.min).css`
- selectively copy specific files from the Bower components to the `public/vendor` directory to prevent bloat that you don't want to push to your server
- run all JavaScript unit tests in all `public/**/_build` directories using Karma, Chai and Sinon

## Changelog

### v1.1.0

- Add livereload server
- Update documentation
- Update to Angular 1.3 by default

### v1.0.0

- Refactor Grunt to Gulp
- Update documentation

### v0.2.0

- Add Karma configuration
- Update documentation

### v0.1.0

- Initial boilerplate
