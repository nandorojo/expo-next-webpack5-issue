# Next.js webpack 5 issue

Setting `future.webpack5 = true` doesn't work with `@expo/next-adapter`.

I patched `@expo/webpack-config` to follow Webpack v5's `externals` syntax, but I see this error:

```sh
HookWebpackError: Cannot read property 'replace' of undefined
```

<details>
  <summary>Click to see full error</summary>

```sh
HookWebpackError: Cannot read property 'replace' of undefined
    at makeWebpackError (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:54949:9)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39896:12
    at eval (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:12:1)
    at fn (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:37857:17)
    at Hook.eval [as callAsync] (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:10:1)
    at Hook.CALL_ASYNC_DELEGATE [as _callAsync] (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28514:14)
    at cont (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39893:34)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39939:10
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:41304:18
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:54969:3
-- inner error --
TypeError: Cannot read property 'replace' of undefined
    at PagesManifestPlugin.createAssets (/workspaces/expo-next-monorepo/node_modules/next/dist/build/webpack/plugins/pages-manifest-plugin.js:5:135)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/build/webpack/plugins/pages-manifest-plugin.js:7:82
    at fn (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:37855:10)
    at Hook.eval [as callAsync] (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:10:1)
    at Hook.CALL_ASYNC_DELEGATE [as _callAsync] (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28514:14)
    at cont (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39893:34)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39939:10
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:41304:18
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:54969:3
    at _done (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:9:1)
caused by plugins in Compilation.hooks.processAssets
TypeError: Cannot read property 'replace' of undefined
    at PagesManifestPlugin.createAssets (/workspaces/expo-next-monorepo/node_modules/next/dist/build/webpack/plugins/pages-manifest-plugin.js:5:135)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/build/webpack/plugins/pages-manifest-plugin.js:7:82
    at fn (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:37855:10)
    at Hook.eval [as callAsync] (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:10:1)
    at Hook.CALL_ASYNC_DELEGATE [as _callAsync] (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28514:14)
    at cont (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39893:34)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39939:10
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:41304:18
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:54969:3
    at _done (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:9:1)
```

</details>

# Run this example

`yarn install`

`yarn next`

## How to reproduce this

1. Create an empty next project
2. Add yarn `resolutions` to `package.json`:

```json
{
  "resolutions": {
    "html-webpack-plugin": "5.3.1",
    "webpack": "^5"
  }
}
```

3. `yarn add -D @expo/next-adapter next-compose-plugins`
4. Create the following files:

```js
// babel.config.js
module.exports = { presets: ["@expo/next-adapter/babel"] };
```

```js
// next.config.js
const { withExpo } = require("@expo/next-adapter");
const withPlugins = require("next-compose-plugins");

module.exports = withPlugins(
  [
    [
      withExpo,
      {
        projectRoot: __dirname,
      },
    ],
  ],
  {
    future: {
      webpack5: true, // set to false to make it work
    },
  }
);
```

6. Run `yarn next`. This triggers an error since `@expo/webpack-config` uses v4 syntax for webpack externals.
7. Patch the webpack external error.

- `yarn add patch-package`
- Add the following file in `patches/@expo+webpack-config+0.12.68.patch`:

<details>
  <summary>Click to see code</summary>

```diff
diff --git a/node_modules/@expo/webpack-config/webpack/addons/withUnimodules.js b/node_modules/@expo/webpack-config/webpack/addons/withUnimodules.js
index 67671c7..4f66d77 100644
--- a/node_modules/@expo/webpack-config/webpack/addons/withUnimodules.js
+++ b/node_modules/@expo/webpack-config/webpack/addons/withUnimodules.js
@@ -132,15 +132,26 @@ function ignoreExternalModules(webpackConfig, shouldIncludeModule) {
     if (!Array.isArray(webpackConfig.externals)) {
         webpackConfig.externals = [webpackConfig.externals];
     }
-    webpackConfig.externals = webpackConfig.externals.map(external => {
+    webpackConfig.externals = webpackConfig.externals.map((external) => {
         if (typeof external !== 'function') {
-            return external;
+          return external
         }
-        return ((ctx, req, cb) => {
-            const relPath = path_1.default.join('node_modules', req);
-            return shouldIncludeModule(relPath) ? cb() : external(ctx, req, cb);
-        });
-    });
+        return (...args) => {
+          const [arg1, arg2, arg3] = args
+          let request = arg2
+          let callback = arg3
+          // in case of webpack 5
+          if (arg1 && arg1.context && arg1.request) {
+            request = arg1.request
+            callback = arg2
+          }
+          const relPath = path_1.default.join('node_modules', request)
+          const willInclude = shouldIncludeModule(relPath)
+
+          // this works, if you don't import react-native
+          return willInclude ? callback(null) : external(...args);
+        }
+      });
     return webpackConfig;
 }
 exports.ignoreExternalModules = ignoreExternalModules;

```

</details>

8. Run `yarn install`, and `yarn next`
9. See the following error:

```sh
HookWebpackError: Cannot read property 'replace' of undefined
    at makeWebpackError (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:54949:9)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39896:12
    at eval (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:12:1)
    at fn (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:37857:17)
    at Hook.eval [as callAsync] (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:10:1)
    at Hook.CALL_ASYNC_DELEGATE [as _callAsync] (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28514:14)
    at cont (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39893:34)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39939:10
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:41304:18
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:54969:3
-- inner error --
TypeError: Cannot read property 'replace' of undefined
    at PagesManifestPlugin.createAssets (/workspaces/expo-next-monorepo/node_modules/next/dist/build/webpack/plugins/pages-manifest-plugin.js:5:135)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/build/webpack/plugins/pages-manifest-plugin.js:7:82
    at fn (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:37855:10)
    at Hook.eval [as callAsync] (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:10:1)
    at Hook.CALL_ASYNC_DELEGATE [as _callAsync] (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28514:14)
    at cont (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39893:34)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39939:10
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:41304:18
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:54969:3
    at _done (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:9:1)
caused by plugins in Compilation.hooks.processAssets
TypeError: Cannot read property 'replace' of undefined
    at PagesManifestPlugin.createAssets (/workspaces/expo-next-monorepo/node_modules/next/dist/build/webpack/plugins/pages-manifest-plugin.js:5:135)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/build/webpack/plugins/pages-manifest-plugin.js:7:82
    at fn (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:37855:10)
    at Hook.eval [as callAsync] (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:10:1)
    at Hook.CALL_ASYNC_DELEGATE [as _callAsync] (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28514:14)
    at cont (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39893:34)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:39939:10
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9438
    at done (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9750)
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/neo-async/async.js:1:9380
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:41304:18
    at /workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:54969:3
    at _done (eval at create (/workspaces/expo-next-monorepo/node_modules/next/dist/compiled/webpack/bundle5.js:28712:10), <anonymous>:9:1)
```

It looks like the issue arises with this line: https://github.com/vercel/next.js/blob/9c47ca2cfd8d0494562dee92791a2195f9655bdc/packages/next/build/webpack/plugins/pages-manifest-plugin.ts#L55
