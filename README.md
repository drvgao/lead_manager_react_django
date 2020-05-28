# Lead Manager

> Full stack Django/React/Redux app that uses token based authentication with Knox.

## Quick Start

```bash
# Install dependencies
npm install

# Serve API on localhost:8000
python leadmanager/manage.py runserver

# Run webpack (from root)
npm run dev

# Build for production
npm run build
```

# react + django project travesy media tutorial

# setup

    * install pipenv
    * pipenv shell
        Creates a virutal environment. Look for cmd line errors. This creates a pipfile, contains all the libraries.
    * pipenv install django djangorestframework django-rest-knox
        Check, all these are installed and added to pipfile
    * django-admin startproject leadmanager
        Creates a django project.
        * cd leadmanager
        * select the python interpreter.
        On VSCODE Ctl+Shift+P then select the one which created above and have pipenv label in it.

        * create django app leads
            * python .\manage.py startapp leads
            * add app in settings
            * create Model, makemigrations & migrate
            * pipenv install djongo
            for mongo db.

## frontend

### inside django project, create django-app named frontend

    * npm init -y
    creates a package.json with javascript depandancies.
    * install web-packs
        * npm install -D webpack webpack-cli
    * install babel transpilers
        *  npm install -D @babel/core babel-loader @babel/preset-env @babel/preset-react babel-plugin-transform-class-properties
    * npm i react react-dom prop-types

#### .babelrc

In order to use babel core and presets create .babelrc file. Add presets and plugin details.

#### webpack.config.js

To use webpack create this file at root. It loads the babel loader.

### modify package.json

- modify the build scripts

  - replace "test": "echo \"Error: no test specified\" && exit 1" with "dev": "webpack --mode development --watch ./leadmanager/frontend/src/index.js --output ./leadmanager/frontend/static/frontend/main.js", \* watch switch, dynamically reloads the content.
    and "build": "webpack --mode production ./leadmanager/frontend/src/index.js --output ./leadmanager/frontend/static/frontend/main.js"

  the npm run build will do few more things for production.

### Create react index.js under src

- import app from components
  - create App in components
  - the app renders at index.html root, app element. ReactDOM.render(<App />, document.getElementById('app'));
  - create index.html under templates
  <div id="app"></div>
  {% load static %}
  <script src="{ % static "frontend/main.js" % }"
  Note: The main.js will be created dynamilly when npm run dev or build runs.

#### layout

    * Create a nav bar, leadmanager\frontend\src\components\layout\Header.js
    * dashboard, leadmanager\frontend\src\components\leads\Dashboard.js
        * holds leads form and listing
            * Form.js to add a lead
            * Leads.js list of leads.
