# Depcheck bug with Rollup

- **depcheck version:** _1.4.3_

This project demonstrates a bug with [depcheck] not detecting [rollup.js]. Namely,
this project has two dependencies, [depcheck] and [rollup.js]. [depcheck] itself
is used in an npm script called "vet". [rollup.js] is used in an npm script called
transpile and also has a configuration file (though the existence of a configuration
file does not guarantee the dependency is actually used). Still, depcheck reports
[rollup.js] as an unused dependency, as seen by running:

```sh
$ npm install
...

$ npm run vet
> depcheck-with-rollup@0.0.1 vet /path/to/depcheck-with-rollup
> depcheck

Unused devDependencies
* rollup
```

[depcheck]: https://github.com/depcheck/depcheck
[rollup.js]: https://rollupjs.org/
