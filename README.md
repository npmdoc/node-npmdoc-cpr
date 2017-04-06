# api documentation for  [cpr (v2.0.2)](https://github.com/davglass/cpr)  [![npm package](https://img.shields.io/npm/v/npmdoc-cpr.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-cpr) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-cpr.svg)](https://travis-ci.org/npmdoc/node-npmdoc-cpr)
#### cp -R

[![NPM](https://nodei.co/npm/cpr.png?downloads=true)](https://www.npmjs.com/package/cpr)

[![apidoc](https://npmdoc.github.io/node-npmdoc-cpr/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-cpr_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-cpr/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-cpr/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-cpr/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Dav Glass",
        "email": "davglass@gmail.com"
    },
    "bin": {
        "cpr": "./bin/cpr"
    },
    "bugs": {
        "url": "http://github.com/davglass/cpr/issues"
    },
    "contributors": [
        {
            "name": "soyuka",
            "email": "soyuka@gmail.com"
        },
        {
            "name": "fresheneesz",
            "email": "bitetrudpublic@gmail.com"
        },
        {
            "name": "silverwind",
            "email": "me@silverwind.io"
        },
        {
            "name": "Peter deHaan",
            "email": "peter@deseloper.com"
        },
        {
            "name": "André Cruz",
            "email": "andremiguelcruz@msn.com"
        },
        {
            "name": "Brian J Brennan",
            "email": "brianloveswords@gmail.com"
        },
        {
            "name": "Elijah Insua",
            "email": "tmpvar@gmail.com"
        },
        {
            "name": "Jonny Reeves",
            "email": "github@jonnyreeves.co.uk"
        },
        {
            "name": "Lydie Danet",
            "email": "lydie@happinov.fr"
        },
        {
            "name": "Ben Elliott",
            "email": "ben.elliott@gsacapital.com"
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
            "name": "davglass",
            "email": "davglass@gmail.com"
        }
    ],
    "name": "cpr",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module cpr](#apidoc.module.cpr)
1.  [function <span class="apidocSignatureSpan"></span>cpr (from, to, opts, callback)](#apidoc.element.cpr.cpr)
1.  object <span class="apidocSignatureSpan">cpr.</span>stack

#### [module cpr.stack](#apidoc.module.cpr.stack)
1.  [function <span class="apidocSignatureSpan">cpr.stack.</span>Stack ()](#apidoc.element.cpr.stack.Stack)



# <a name="apidoc.module.cpr"></a>[module cpr](#apidoc.module.cpr)

#### <a name="apidoc.element.cpr.cpr"></a>[function <span class="apidocSignatureSpan"></span>cpr (from, to, opts, callback)](#apidoc.element.cpr.cpr)
- description and source-code
```javascript
cpr = function (from, to, opts, callback) {
    if (typeof opts === 'function') {
        callback = opts;
        opts = {};
    }

    var options = {},
        proc;

    Object.keys(opts).forEach(function(key) {
        options[key] = opts[key];
    });

    options.from = from;
    options.to = to;
    options.errors = [];

    proc = function() {
        getTree(options.from, options, function(err, tree) {
            filterTree(tree, options, function(err, t) {
                splitTree(t, options, function(dirs, files) {
                    if (!dirs.length && !files.length) {
                        return callback(new Error('No files to copy'));
                    }
                    createDirs(dirs, to, options, function() {
                        createFiles(files, to, options, function() {
                            var out = [], err;
                            Object.keys(options.toHash).forEach(function(k) {
                                out.push(options.toHash[k]);
                            });
                            if (options.confirm) {
                                confirm(out, options, callback);
                            } else if (!options.errors.length) {
                                callback(null, out.sort());
                            } else {
<span class="apidocCodeCommentSpan">                                /*istanbul ignore next*/
</span>                                err = new Error('Unable to copy directory' + (out.length ? ' entirely' : ''));
                                /*istanbul ignore next*/
                                err.list = options.errors;
                                /*istanbul ignore next*/
                                callback(err, out.sort());
                            }
                        });
                    });
                });
            });
        });
    };

    fs.stat(options.from, function(err, stat) {
        if (err) {
            return callback(new Error('From should be a file or directory'));
        }
        if (stat && stat.isDirectory()) {
            if (options.deleteFirst) {
                rimraf(to, function() {
                    proc();
                });
            } else {
                proc();

            }
        } else {
            if (stat.isFile()) {
                var dirRegex = new RegExp(path.sep + '$');
                if (dirRegex.test(to)) { // Create directory if has trailing separator
                  to = path.join(to, path.basename(options.from));
                }
                return copyFile(options.from, to, options, callback);
            }
            callback(new Error('From should be a file or directory'));
        }
    });
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.cpr.stack"></a>[module cpr.stack](#apidoc.module.cpr.stack)

#### <a name="apidoc.element.cpr.stack.Stack"></a>[function <span class="apidocSignatureSpan">cpr.stack.</span>Stack ()](#apidoc.element.cpr.stack.Stack)
- description and source-code
```javascript
Stack = function () {
    this.errors   = [];
    this.finished = 0;
    this.results  = [];
    this.total    = 0;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
