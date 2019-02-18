# React project boilerplate

This is a minimalist set of files to quickly bootstrap a React Web application development environment. This repository exists only to provide a light and fast alternative to [create-react-app](https://github.com/facebook/create-react-app), with very little support for the production phase.

Typical components and features of such an environment are:

- "transpiler" from modern JavaScript and JSX to EcmaScript 5
- a project bundler
- a web-server
- file monitoring, re-bundling and refreshing when they change

This repository uses [Parcel](https://parceljs.org)  as a bundler, which in turn uses [Babel](https://babeljs.io) to transpile the code.
Parcel provides a Web-server with live-reloading to run the app and monitor the changes.
As an alternate Web-server, [live-server](https://github.com/tapio/live-server) is also provided in this project.


# Installation

To start working, you first need to download the files locally.

Example with the Git command line tool:

```bash
git clone <URL_of_this_repository>
```

Then you need to install the packages.
To do so, open a terminal in the project's root folder and issue the `install` command of your package manager of choice - typically `npm` or `yarn` - like so:

```bash
yarn install
npm install # alternatively
```


# Usage

To launch the development environment (live-server and auto-bundling), run one of the following:

```bash
npm start
yarn start # alternatively
```

This will build a development bundle in the `dist/` folder (relatively to the project root), and launch a server on port `1234` with auto-reloading on file changes.

A tab should open in your default web browser at the following address:
`http://localhost:1234`


# Alternate server

If you follow the "Usage" indications, your app will be served by Parcel.
This project contains the `live-server` package, which can be used alternatively.

An npm script is provided for convenience: it will bundle the project and monitor file changes with Parcel, and serve the app with live-server. This script's name is `serve-alt`, you can run it with one of the following commands:

```bash
yarn serve-alt
yarn run serve-alt
npm run serve-alt
```

This should provide the same development environment features as the `start` script.

#### More info:

The `serve-alt` npm script uses the `parcel watch` command in conjunction with `live-server`.
The former will take care of bundling the project and monitoring: the app page will refresh when it detects changes in the bundle.
That is why the project includes the `concurrently` package for convenience, which is used like so :

```bash
npx concurrently "npm watch" "live-server" # or
yarn concurrently "npm watch" "live-server"
```

Note: `live-server` knows several options. One worth mentioning is the `--no-browser` option, which prevents `live-server` from opening the page in a new tab in the default browser.


# Production build

The `production` npm script is provided in order to let Parcel create a production bundle. Read Parcel's `build` command documentation for information about what it is and the options it can take.

```bash
yarn production
npm run production
```

# Options

## Browser auto open

The default behavior in this project is to automatically open the application page in the default browser when the development environment starts and is ready to serve the app. This can be disabled by editing the npm scripts:

- In the `start` script -serving with Parcel- remove the `--open` option.
- In the `serve-alt` script -serving with Live-server- add the `--no-browser` option after `--quiet`.
