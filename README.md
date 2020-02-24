# Fork TS Checker Webpack Plugin Issue
```
ERROR in fork-ts-checker-webpack-plugin-resolution-issue/packages/baz/src/app/index.ts
ERROR in fork-ts-checker-webpack-plugin-resolution-issue/packages/baz/src/app/index.ts(1,20):
TS6305: Output file 'fork-ts-checker-webpack-plugin-resolution-issue/packages/bar/dist/Foobar/index.d.ts' has not been built from source file 'fork-ts-checker-webpack-plugin-resolution-issue/packages/bar/src/Foobar/index.ts'.
error Command failed with exit code 2.
```

## Package Structure
```
- packages/baz is the main app and contains a webpack configuration
- packages/bar depends on packages/foo and exports Foobar
- packages/foo does not depend on anything and exports Foo
```

## How To Reproduce
1. Run `yarn bootstrap` from the root to install all dependencies and kick off the first build. This will show the failure.
2. Run `yarn build` from the root. This will not show the failure
3. Run `yarn clean && yarn build` from the root. This will show the failure. Running without `yarn clean` will not show the failure.
4. Run `yarn clean && yarn build:fixed` to show the everything okay when not using ForkTsCheckerWebpackPlugin.
