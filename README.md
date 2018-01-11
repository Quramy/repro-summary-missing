This is a repository to reproduce `@angular/compiler-cli` ngsummary issue.

```sh
git checkout https://github.com/Quramy/repro-summary-missing.git
yarn install
yarn ngc
```

And `find out-tsc src/tsconfig.aot.json -name "*.ngsummary.json"` outputs the following:

```txt
out-tsc/app/node_modules/@angular/common/common.ngsummary.js
out-tsc/app/node_modules/@angular/core/core.ngsummary.js
out-tsc/app/node_modules/@angular/platform-browser/platform-browser.ngsummary.js
out-tsc/app/node_modules/@angular/platform-browser-dynamic/platform-browser-dynamic.ngsummary.js
out-tsc/app/src/app/app.component.ngsummary.js
out-tsc/app/src/app/app.module.ngsummary.js
```

The above output is strange because there is not `node_modules/@angular/common/http/http.ngsummary.js` in spite of `common.ngsummary.js` exists :thinking:


And with Angular 5.1.3, ngc emits the following `ngsummary.js`s:

```txt
out-tsc/app/node_modules/@angular/common/common.ngsummary.js
out-tsc/app/node_modules/@angular/common/http/http.ngsummary.js
out-tsc/app/node_modules/@angular/core/core.ngsummary.js
out-tsc/app/node_modules/@angular/platform-browser/platform-browser.ngsummary.js
out-tsc/app/node_modules/@angular/platform-browser-dynamic/platform-browser-dynamic.ngsummary.js
out-tsc/app/src/app/app.component.ngsummary.js
out-tsc/app/src/app/app.module.ngsummary.js
```
