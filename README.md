# api documentation for  [jsinspect (v0.12.4)](https://github.com/danielstjules/jsinspect)  [![npm package](https://img.shields.io/npm/v/npmdoc-jsinspect.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-jsinspect) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-jsinspect.svg)](https://travis-ci.org/npmdoc/node-npmdoc-jsinspect)
#### Detect structural similarities in your code

[![NPM](https://nodei.co/npm/jsinspect.png?downloads=true)](https://www.npmjs.com/package/jsinspect)

[![apidoc](https://npmdoc.github.io/node-npmdoc-jsinspect/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-jsinspect_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-jsinspect/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-jsinspect/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-jsinspect/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Daniel St. Jules",
        "email": "danielst.jules@gmail.com"
    },
    "bin": {
        "jsinspect": "./bin/jsinspect"
    },
    "bugs": {
        "url": "https://github.com/danielstjules/jsinspect/issues"
    },
    "dependencies": {
        "babylon": "6.16.1",
        "chalk": "*",
        "commander": "*",
        "filepaths": "0.3.0",
        "stable": "0.1.6",
        "strip-indent": "^1.0.0",
        "strip-json-comments": "1.0.2"
    },
    "description": "Detect structural similarities in your code",
    "devDependencies": {
        "concat-stream": "^1.5.0",
        "dirmap": "0.0.2",
        "expect.js": "*",
        "mocha": "*"
    },
    "directories": {},
    "dist": {
        "shasum": "f1f8258678d9994ac90629985c227d121874c768",
        "tarball": "https://registry.npmjs.org/jsinspect/-/jsinspect-0.12.4.tgz"
    },
    "gitHead": "019b0bf33d3ff23dc9b9f5c2e6170bcde6f66b18",
    "homepage": "https://github.com/danielstjules/jsinspect",
    "keywords": [
        "inspect",
        "detect",
        "code",
        "duplicate",
        "structure",
        "copy",
        "paste"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "danielstjules",
            "email": "danielst.jules@gmail.com"
        }
    ],
    "name": "jsinspect",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/danielstjules/jsinspect.git"
    },
    "scripts": {
        "test": "mocha -R spec spec spec/reporters"
    },
    "version": "0.12.4"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module jsinspect](#apidoc.module.jsinspect)
1.  [function <span class="apidocSignatureSpan">jsinspect.</span>Inspector (filePaths, opts)](#apidoc.element.jsinspect.Inspector)
1.  object <span class="apidocSignatureSpan">jsinspect.</span>helpers
1.  object <span class="apidocSignatureSpan">jsinspect.</span>parser
1.  object <span class="apidocSignatureSpan">jsinspect.</span>reporters

#### [module jsinspect.helpers](#apidoc.module.jsinspect.helpers)
1.  [function <span class="apidocSignatureSpan">jsinspect.helpers.</span>captureOutput ()](#apidoc.element.jsinspect.helpers.captureOutput)
1.  [function <span class="apidocSignatureSpan">jsinspect.helpers.</span>collectMatches (inspector)](#apidoc.element.jsinspect.helpers.collectMatches)
1.  [function <span class="apidocSignatureSpan">jsinspect.helpers.</span>getOutput ()](#apidoc.element.jsinspect.helpers.getOutput)
1.  [function <span class="apidocSignatureSpan">jsinspect.helpers.</span>parse (filePath)](#apidoc.element.jsinspect.helpers.parse)
1.  [function <span class="apidocSignatureSpan">jsinspect.helpers.</span>restoreOutput ()](#apidoc.element.jsinspect.helpers.restoreOutput)
1.  [function <span class="apidocSignatureSpan">jsinspect.helpers.</span>trimlines (str)](#apidoc.element.jsinspect.helpers.trimlines)

#### [module jsinspect.parser](#apidoc.module.jsinspect.parser)
1.  [function <span class="apidocSignatureSpan">jsinspect.parser.</span>parse (src, filePath)](#apidoc.element.jsinspect.parser.parse)

#### [module jsinspect.reporters](#apidoc.module.jsinspect.reporters)
1.  [function <span class="apidocSignatureSpan">jsinspect.reporters.</span>default (inspector, opts)](#apidoc.element.jsinspect.reporters.default)
1.  [function <span class="apidocSignatureSpan">jsinspect.reporters.</span>json (inspector, opts)](#apidoc.element.jsinspect.reporters.json)
1.  [function <span class="apidocSignatureSpan">jsinspect.reporters.</span>pmd (inspector, opts)](#apidoc.element.jsinspect.reporters.pmd)



# <a name="apidoc.module.jsinspect"></a>[module jsinspect](#apidoc.module.jsinspect)

#### <a name="apidoc.element.jsinspect.Inspector"></a>[function <span class="apidocSignatureSpan">jsinspect.</span>Inspector (filePaths, opts)](#apidoc.element.jsinspect.Inspector)
- description and source-code
```javascript
class Inspector extends EventEmitter {
<span class="apidocCodeCommentSpan">  /**
   * Creates a new Inspector, which extends EventEmitter. filePaths is expected
   * to be an array of string paths. Also accepts an options object with any
   * combination of the following: threshold, identifiers literals, and
   * minInstances. Threshold indicates the minimum number of nodes to analyze.
   * Identifiers indicates whether or not the nodes in a match should also have
   * matching identifiers, and literals whether or not literal values should
   * match. minInstances specifies the min number of instances for a match.
   * An instance of Inspector emits the following events: start, match and end.
   *
   * @constructor
   * @extends EventEmitter
   *
   * @param {string[]} filePaths The files on which to run the inspector
   * @param {object}   [opts]    Options to set for the inspector
   */
</span>  constructor(filePaths, opts) {
    super();
    opts = opts || {};

    this._filePaths    = filePaths || [];
    this._threshold    = opts.threshold || 30;
    this._identifiers  = opts.identifiers;
    this._literals     = opts.literals;
    this._minInstances = opts.minInstances || 2;
    this._map          = Object.create(null);
    this._fileContents = {};
    this._traversals   = {};
    this.numFiles      = this._filePaths.length;
  }

  /**
   * Runs the inspector on the given file paths, as provided in the constructor.
   * Emits a start event, followed by a series of match events for any detected
   * similarities, and an end event on completion.
   *
   * @fires Inspector#start
   * @fires Inspector#match
   * @fires Inspector#end
   */
  run() {
    this.emit('start');

    // File contents are split to allow for specific line extraction
    this._filePaths.forEach((filePath) => {
      var src = fs.readFileSync(filePath, {encoding: 'utf8'});
      this._fileContents[filePath] = src.split('\n');
      try {
        var syntaxTree = parse(src, filePath);
      } catch (err) {
        return console.error(err.message);
      }
      this._traversals[filePath] = NodeUtils.getDFSTraversal(syntaxTree);
      this._walk(syntaxTree, (nodes) => this._insert(nodes));
    });

    this._analyze();
    this.emit('end');
  }

  /**
   * Walks a given node's AST, building up arrays of nodes that meet the
   * inspector's threshold. When found, the callback is invoked and passed
   * the array of nodes.
   *
   * @private
   *
   * @param {Node}     node The node to traverse
   * @param {function} fn   The callback to invoke
   */
  _walk(node, fn) {
    NodeUtils.walkSubtrees(node, (node, parent, ancestors) => {
      var state = ancestors.concat(node);
      if (NodeUtils.isAMD(state) ||
          NodeUtils.isCommonJS(state) ||
          NodeUtils.isES6ModuleImport(state) ||
          NodeUtils.isES6ClassBoilerplate(state)) {
        return;
      }

      var nodes = NodeUtils.getDFSTraversal(node, this._threshold);
      if (nodes.length === this._threshold) {
        fn(nodes);
      }

      this._walkSiblings(node, fn);
    });
  }

  /**
   * Walks sibling nodes under a parent, grouping their DFS traversals, and
   * invoking the callback for those that wouldn't otherwise meet the threshold.
   * Helpful for nodes like BlockStatements that hold a sequence. Note that
   * this will generate overlapping instances, and so _omitOverlappingInstances
   * helps cleanup the results.
   *
   * @private
   *
   * @param {Node}     node The node to traverse
   * @param {function} fn   The callback to invoke
   */
  _walkSiblings(parent, fn) {
    // group siblings that wouldn't otherwise meet threshold
    var children = NodeUtils.getChildren(parent);
    var n = this._threshold;

    for (let i = 0; i < children.length - 1; i++) {
      let nodes = NodeUtils.getDFSTraversal(children[i], n);
      if (nodes.length === n) continue;

      for (let j = i + 1; j < children.length; j++) {
        nodes = nodes.concat(NodeUtils.getDFSTraversal(children[j], n));
        if (nodes.length >= n) {
          fn(nodes.slice(0, n));
          break;
        }
      }
    }
  }

  /** ...
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.jsinspect.helpers"></a>[module jsinspect.helpers](#apidoc.module.jsinspect.helpers)

#### <a name="apidoc.element.jsinspect.helpers.captureOutput"></a>[function <span class="apidocSignatureSpan">jsinspect.helpers.</span>captureOutput ()](#apidoc.element.jsinspect.helpers.captureOutput)
- description and source-code
```javascript
captureOutput = function () {
  chalk.enabled = false;
  output = '';
  process.stdout.write = function(string) {
    if (!string) return;
    output += string;
  };
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jsinspect.helpers.collectMatches"></a>[function <span class="apidocSignatureSpan">jsinspect.helpers.</span>collectMatches (inspector)](#apidoc.element.jsinspect.helpers.collectMatches)
- description and source-code
```javascript
collectMatches = function (inspector) {
  var array = [];
  inspector.on('match', function(match) {
    array.push(match);
  });
  return array;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jsinspect.helpers.getOutput"></a>[function <span class="apidocSignatureSpan">jsinspect.helpers.</span>getOutput ()](#apidoc.element.jsinspect.helpers.getOutput)
- description and source-code
```javascript
getOutput = function () {
  return output;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jsinspect.helpers.parse"></a>[function <span class="apidocSignatureSpan">jsinspect.helpers.</span>parse (filePath)](#apidoc.element.jsinspect.helpers.parse)
- description and source-code
```javascript
parse = function (filePath) {
  if (parseCache[filePath]) return parseCache[filePath];

  // Skip the root Program node
  var src = fs.readFileSync(filePath, {encoding: 'utf8'});
  var ast = parse(src, filePath).body;
  parseCache[filePath] = ast;

  return ast;
}
```
- example usage
```shell
...
  } catch (err) {
    if (i === fns.length - 1) throw err;
  }
}
}

function _parse(src, filePath, sourceType) {
return babylon.parse(src, {
  allowReturnOutsideFunction: true,
  allowImportExportEverywhere: true,
  sourceType: sourceType,
  sourceFilename: filePath,
  plugins: ['jsx', 'flow', 'doExpressions', 'objectRestSpread', 'decorators',
    'classProperties', 'exportExtensions', 'asyncGenerators', 'functionBind',
    'functionSent', 'dynamicImport']
...
```

#### <a name="apidoc.element.jsinspect.helpers.restoreOutput"></a>[function <span class="apidocSignatureSpan">jsinspect.helpers.</span>restoreOutput ()](#apidoc.element.jsinspect.helpers.restoreOutput)
- description and source-code
```javascript
restoreOutput = function () {
  chalk.enabled = enabled;
  process.stdout.write = write;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jsinspect.helpers.trimlines"></a>[function <span class="apidocSignatureSpan">jsinspect.helpers.</span>trimlines (str)](#apidoc.element.jsinspect.helpers.trimlines)
- description and source-code
```javascript
trimlines = function (str) {
  return str.split('\n').map(str => str.trim()).join('\n');
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.jsinspect.parser"></a>[module jsinspect.parser](#apidoc.module.jsinspect.parser)

#### <a name="apidoc.element.jsinspect.parser.parse"></a>[function <span class="apidocSignatureSpan">jsinspect.parser.</span>parse (src, filePath)](#apidoc.element.jsinspect.parser.parse)
- description and source-code
```javascript
parse = function (src, filePath) {
  debug('parsing ${filePath}');
  try {
    return attempt(
      () => _parse(src, filePath, 'script'),
      () => _parse(src, filePath, 'module')
    );
  } catch (err) {
    let ctx = getErrorContext(err, src);
    throw new Error('Couldn't parse ${filePath}: ${err.message}${ctx}');
  }
}
```
- example usage
```shell
...
  } catch (err) {
    if (i === fns.length - 1) throw err;
  }
}
}

function _parse(src, filePath, sourceType) {
return babylon.parse(src, {
  allowReturnOutsideFunction: true,
  allowImportExportEverywhere: true,
  sourceType: sourceType,
  sourceFilename: filePath,
  plugins: ['jsx', 'flow', 'doExpressions', 'objectRestSpread', 'decorators',
    'classProperties', 'exportExtensions', 'asyncGenerators', 'functionBind',
    'functionSent', 'dynamicImport']
...
```



# <a name="apidoc.module.jsinspect.reporters"></a>[module jsinspect.reporters](#apidoc.module.jsinspect.reporters)

#### <a name="apidoc.element.jsinspect.reporters.default"></a>[function <span class="apidocSignatureSpan">jsinspect.reporters.</span>default (inspector, opts)](#apidoc.element.jsinspect.reporters.default)
- description and source-code
```javascript
class DefaultReporter extends BaseReporter {
<span class="apidocCodeCommentSpan">  /**
   * The default reporter, which displays both file and line information for
   * each given match.
   *
   * @constructor
   *
   * @param {Inspector} inspector Instance on which to register its listeners
   * @param {object}    opts      Options to set for the reporter
   */
</span>  constructor(inspector, opts) {
    opts = opts || {};
    super(inspector, opts);
    this._registerSummary();
  }

  /**
   * Returns the string output to print for the given reporter. The string
   * contains the number of instances associated with the match and the files
   * and lines involved.
   *
   * @private
   *
   * @param   {Match}  match The inspector match to output
   * @returns {string} The formatted output
   */
  _getOutput(match) {
    var instances = match.instances;
    var output = '\n' + '-'.repeat(60) + '\n\n' +
      chalk.bold('Match - ${instances.length} instances\n');

    instances.forEach((instance) => {
      var location = this._getFormattedLocation(instance);
      var lines = this._getLines(instance);
      output += '\n${location}\n${chalk.grey(lines)}\n';
    });

    return output;
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jsinspect.reporters.json"></a>[function <span class="apidocSignatureSpan">jsinspect.reporters.</span>json (inspector, opts)](#apidoc.element.jsinspect.reporters.json)
- description and source-code
```javascript
class JSONReporter extends BaseReporter {
<span class="apidocCodeCommentSpan">  /**
   * A JSON reporter, which displays both file and line information for
   * each given match.
   *
   * @constructor
   *
   * @param {Inspector} inspector Instance on which to register its listeners
   * @param {object}    opts      Options to set for the reporter
   */
</span>  constructor(inspector, opts) {
    opts = opts || {};
    super(inspector, opts);

    var enabled = chalk.enabled;

    inspector.on('start', () => {
      chalk.enabled = false;
      this._writableStream.write('[');
    });

    inspector.on('end', () => {
      chalk.enabled = enabled;
      this._writableStream.write(']\n');
    });
  }

  /**
   * Returns the string output to print for the given reporter. The formatted
   * JSON string contains the number of instances associated with the match and
   * the files and lines involved.
   *
   * @private
   *
   * @param   {Match}  match The inspector match to output
   * @returns {string} The formatted output
   */
  _getOutput(match) {
    var output = (this._found > 1) ? ',\n' : '';

    output += JSON.stringify({
      id: match.hash,
      instances: match.instances.map(instance => {
        return {
          path: this._getRelativePath(instance.filename),
          lines: [instance.start.line, instance.end.line],
          code: this._getLines(instance)
        };
      })
    });

    return output;
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.jsinspect.reporters.pmd"></a>[function <span class="apidocSignatureSpan">jsinspect.reporters.</span>pmd (inspector, opts)](#apidoc.element.jsinspect.reporters.pmd)
- description and source-code
```javascript
class PMDReporter extends BaseReporter {
<span class="apidocCodeCommentSpan">  /**
   * A PMD CPD XML reporter, which tries to fit jsinspect's output to something
   * CI tools might expect from PMD.
   *
   * @constructor
   *
   * @param {Inspector} inspector Instance on which to register its listeners
   * @param {object}    opts      Options to set for the reporter
   */
</span>  constructor(inspector, opts) {
    opts = opts || {};
    super(inspector, opts);

    var enabled = chalk.enabled;

    inspector.on('start', () => {
      chalk.enabled = false;
      this._writableStream.write(
        '<?xml version="1.0" encoding="utf-8"?>\n' +
        '<pmd-cpd>\n'
      );
    });

    inspector.on('end', () => {
      chalk.enabled = enabled;
      this._writableStream.write('</pmd-cpd>\n');
    });
  }

  /**
   * Returns an XML string containing a <duplication> element, with <file>
   * children indicating the instance locations, and <codefragment> to hold the
   * lines.
   *
   * @private
   *
   * @param   {Match}  match The inspector match to output
   * @returns {string} The formatted output
   */
  _getOutput(match) {
    var output = (this._found > 1) ? '\n' : '';
    var codeFragment = '';
    var instances = match.instances;
    var totalLines = this._getTotalLines(match);

    output += '<duplication lines="${totalLines}" id="${match.hash}">\n';
    instances.forEach((instance) => output += this._getFile(instance));

    output += '<codefragment>';
    instances.forEach((instance) => {
      var location = this._getFormattedLocation(instance);
      var lines = this._getLines(instance);
      codeFragment += '\n${location}\n${chalk.grey(lines)}\n';
    });
    output += '${this._escape(codeFragment)}</codefragment>\n</duplication>\n';

    return output;
  }

  /**
   * Returns the total number of lines spanned by a match.
   *
   * @param   {Match} match
   * @returns {int}
   */
  _getTotalLines(match) {
    return match.instances.reduce((res, curr) => {
      return res + curr.end.line - curr.start.line + 1;
    }, 0);
  }

  /**
   * Returns an XML string containing the path to the file in which the instance
   * is located, as well as its starting line. Absolute paths are required for
   * Jenkins.
   *
   * @param   {object} instance
   * @returns {string}
   */
  _getFile(instance) {
    var filePath = this._getAbsolutePath(instance.filename);
    return '<file path="${filePath}" line="${instance.start.line}"/>\n';
  }

  /**
   * Returns an escaped string for use within XML.
   *
   * @param   {string} string The string to escape
   * @returns {string} The escaped string
   */
  _escape(string) {
    var escaped = {
      "'": '&apos;',
      '"': '&quot;',
      '&': '&amp;',
      '>': '&gt;',
      '<': '&lt;'
    };

    return string.replace(/(['"&><])/g, (string, char) => {
      return escaped[char];
    });
  }
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
