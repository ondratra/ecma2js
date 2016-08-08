# ecma2js

[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0)

Skeleton for projects that needs to convert ECMA6(also known as ES2015) code to pure javascript compatible
with browsers that currently supports limited set of ECMA features.

# Install
Copy or integrate content of files `gulfile.js` and `package.json`(only it's devDependencies section is relevant)
into your own project. In top of `gulpfile.js` change your configuration(source folder, build output folder, etc.). Then run:

```
npm install
```

# Usage
```
gulp browserify # converts ECMA to pure js and bundles it into one file
gulp browserifyWatch # convertion on source file(s) change
gulp uglify # minifies build
gulp buildStats # prints original, build and minified file sizes
```

## Example buildStats output
```
$ gulp buildStats
[17:07:18] Using gulpfile /somePath/ecma2js/gulpfile.js
[17:07:18] Starting 'buildStats'...
[17:37:51] all files 1.2 kB
[17:37:51] all files 3.38 kB
[17:37:51] all files 362 B
[17:37:51] Clean project has 3 files with total size 362 B
[17:37:51] Build size is 3.38 kB (935% of original size)
[17:37:51] Build size after minification is 1.2 kB (332% of original size and 35% of build)
[17:37:51] Finished 'buildStats' after 31 ms
```

## Uglify note
In default mode uglify(used here to minify js code) mangles(uglifies) function names.
That process unfortunately breaks usual ECMA way to get class name `this.constructor.name`.
To workaround the issue function name mangeling is turned off, but you can enable it if you don't need to ask
for class names in that manner(it will save some extra bytes). Look for `{mangle: { keep_fnames: true}` in `gulpfile.js`.

