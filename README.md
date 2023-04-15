![GitHub Workflow Status (branch)](https://img.shields.io/github/actions/workflow/status/stackblogger/parent-package-json-ts/master.yml?style=flat-square&logo=github&color=success)
![npm](https://img.shields.io/npm/v/parent-package-json-ts?style=flat-square&color=success&logo=npm)

# parent-package-json-ts

A plugin to read and parse parent package.json file as JSON object in TypeScript Node.Js. It is useful when you have a library that requires some attributes from parent Package.Json file. Simply install this library in your parent Node.Js JavaScript/TypeScript based application and call the function.

The objective of the plugin is to read the `package.json` file contents as a valid JSON objects wherever you call the function. It will read the `package.json` file of the caller location.

## Installation

```bash
npm install parent-package-json-ts
```

## Default Usage

Once the plugin is installed, import `packageJson` function from `parent-package-json-ts` package anywehere in your project and assign the JSON object in a variable.

```typescript
import { packageJson } from 'parent-package-json-ts';

const contents = packageJson();

console.log(contents);

/*
  {
    "name": "parent-package-json-ts",
    "version": "0.1.0",
    "description": "Read and Parse Parent Package Json file in TypeScript.",
    "scripts": {
      "test": "jest --coverage",
      "lint": "eslint ."
    },
    "repository": {
      "type": "git",
      "url": "git+https://github.com/stackblogger/parent-package-json-ts.git"
    },
    "engines": {
      "node": ">= 16.0.0"
    }
  }
*/
```

## Use your own custom interface to read json values

If you don't want to use the plugin's default interface then you can have your own interface and provide it as prefix at the time of `packageJson` function call. More details here-

```typescript
import { packageJson } from 'parent-package-json-ts';

interface PackageJsonContent {
  name: string;
  version: string;
}

const contents = <PackageJsonContent>packageJson();
console.log(contents);

/*
  {
    "name": "parent-package-json-ts",
    "version": "0.1.0"
  }
*/
```

## Read Package.Json from a custom directory

You can also read the parsed `package.json` as JSON object from a custom directory. Simply pass the custom directory path in the function parameter.
Here are more details with example-

```typescript
import { packageJson } from 'parent-package-json-ts';

const customPath = path.join('some-directory-here');
const contents = packageJson(customPath);

console.log(contents);

/*
  {
    "name": "parent-package-json-ts",
    "version": "0.1.0",
    "description": "Read and Parse Parent Package Json file in TypeScript.",
    "scripts": {
      "test": "jest --coverage",
      "lint": "eslint ."
    },
    "repository": {
      "type": "git",
      "url": "git+https://github.com/stackblogger/parent-package-json-ts.git"
    },
    "engines": {
      "node": ">= 16.0.0"
    }
  }
*/
```

### License

[MIT](https://choosealicense.com/licenses/mit/)
