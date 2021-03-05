# package.json

> It is a JSON file in the root of a JS/Node project, which holds **metadata** relevant to the project and it is used for managing the project's name, version, dependencies, etc.

- metadata : a set of data that gives information about other data

## How To Create A `package.json` File

- `$ npm init` (or `$ yarn init`)
  - You can also run `$ npm init -y` (or `$yarn init -y`) to generate the `package.json` file with default values.
- Or you can create it manually: at the root of the project, create a `package.json` file containing required fields (`name` and `version`)

## Fields

- `name`
  - **required**
  - name of the project
  - must be lowercase, one word (`-` or `_` allowed)

- `version`
  - **required**
  - current version of the module for the project
  - follow [semantic versioning](https://docs.npmjs.com/about-semantic-versioning)

- `description`
  - description of the project

- `main`
  - the entry point of the project

- `scripts`
  - scripts that can be used to perform certain tasks such as building or testing the project

- `keywords`
  - an array of keywords that helps the users to identify the project

- `author`
  - the creator of the project

- `license`
  - the type of license

- `engines`
  - the version of the libraries (npm) and runtime (node) on which the project should run

- `dependencies`
  - the list of the required modules/packages for the project
  - after installing dependencies by running `npm install packagename`, they are added to this list

- `devDependencies`
  - the list of the modules/packages that are only needed for the project development (such as linters, testing libraries and transpilers)
  - install devDependencies by running `npm install packagename --save-dev`

## Example
```json
{
  "name": "my_package",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "Alex Lee",
  "license": "ISC",
}s
```