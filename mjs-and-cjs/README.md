# Depcheck bug with `.mjs` and `.cjs

- **depcheck version:** _1.4.3_

This project demonstrates a bug with [depcheck] not detecting dependencies used in
files using the `.mjs` (for ModuleJS, or ESModules) or `.cjs` (for CommonJS) file
extension. In this project you can find one `.mjs` file and one `.cjs` file, each
importing a unique dependency. When scanning this project with [depcheck] both dependencies
will be reported as unused (with the default configuration), as seen by running:

```sh
$ npm install
...

$ npm run vet
> depcheck-with-rollup@0.0.1 vet /path/to/depcheck-with-rollup
> depcheck

Unused dependencies
* ava
* dotenv
```

From my testing, this is regardless of

1. The specific dependencies.
1. How the dependencies are imported.
1. Whether they're dependencies or devDependencies.
1. The value of `"type"` in the package manifest.

[depcheck]: https://github.com/depcheck/depcheck
