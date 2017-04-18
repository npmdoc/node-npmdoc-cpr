# npmdoc-cpr

#### api documentation for  [cpr (v2.0.2)](https://github.com/davglass/cpr)  [![npm package](https://img.shields.io/npm/v/npmdoc-cpr.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-cpr) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-cpr.svg)](https://travis-ci.org/npmdoc/node-npmdoc-cpr)

#### cp -R

[![NPM](https://nodei.co/npm/cpr.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/cpr)

- [https://npmdoc.github.io/node-npmdoc-cpr/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-cpr/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-cpr/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-cpr/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-cpr/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-cpr/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Dav Glass"
    },
    "bin": {
        "cpr": "./bin/cpr"
    },
    "bugs": {
        "url": "http://github.com/davglass/cpr/issues"
    },
    "contributors": [
        {
            "name": "soyuka"
        },
        {
            "name": "fresheneesz"
        },
        {
            "name": "silverwind"
        },
        {
            "name": "Peter deHaan"
        },
        {
            "name": "André Cruz"
        },
        {
            "name": "Brian J Brennan"
        },
        {
            "name": "Elijah Insua"
        },
        {
            "name": "Jonny Reeves"
        },
        {
            "name": "Lydie Danet"
        },
        {
            "name": "Ben Elliott"
        }
    ],
    "dependencies": {
        "graceful-fs": "^4.1.5",
        "minimist": "^1.2.0",
        "mkdirp": "~0.5.1",
        "rimraf": "^2.5.4"
    },
    "description": "cp -R",
    "devDependencies": {
        "github-changes": "^1.0.4",
        "istanbul": "~0.4.4",
        "jenkins-mocha": "^3.0.0",
        "jshint": "^2.9.2",
        "yui-lint": "~0.2.0"
    },
    "directories": {},
    "dist": {
        "shasum": "9e44be91101f644a3e1f8c908712b70cdd547056",
        "tarball": "https://registry.npmjs.org/cpr/-/cpr-2.0.2.tgz"
    },
    "gitHead": "0f2c8b51a33610d53f7f9604e55bea8fe6360966",
    "homepage": "https://github.com/davglass/cpr",
    "keywords": [
        "copy",
        "recursive",
        "cp -r",
        "cp"
    ],
    "license": "BSD-3-Clause",
    "main": "./lib/index.js",
    "maintainers": [
        {
            "name": "davglass"
        }
    ],
    "name": "cpr",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/davglass/cpr.git"
    },
    "scripts": {
        "changes": "github-changes -o davglass -r cpr",
        "posttest": "istanbul check-coverage",
        "pretest": "jshint --config ./node_modules/yui-lint/jshint.json ./lib/",
        "test": "jenkins-mocha ./tests/full.js",
        "windows-test": "jenkins-mocha ./tests/full.js"
    },
    "version": "2.0.2"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
