# Dynamic configuration of third-party controls

Origo comes with many built-in controls, however there also exist many useful third-party plugins, distributed as plugins. They can be instantiated manually, however you also have to option to let Origo instantiate them, in which case they can also be configured by the `controls` section in the normal configuration file.

This has two primary advantages over manually instantiating plugins:

* All configuration in one place
* Re-use the same HTML & JavaScript files for different map configurations, including different sets of controls

Synchronous loading requires the control factory function to be available in the instantiating scope. This can be achived by adding a `<script>` tag for the plugin, or by importing it using `ESM` (`import ... from ...`) or `CommonJS` (`const ... = require(...)`) syntax.

For asynchronous loading using a bundler is strongly recommended, as it simplifies the required loading code. Note that asynchronous loading requires the plugin to `export` the control factory function, the examples shown assume that the function is the default export. This is not the case for some published plugins, which can be solved by adding `export default FUNCTION;` at the end of the minified plugin file (where `FUNCTION` is the name of the control factory function).

In general, asynchronous loading is recommended especially for plugins that are large or infrequently used.

#### Example of synchronously loaded plugin control

```javascript
var origo = Origo('index.json', {
 controls: {
   lmsearch: Lmsearch,
 }
});
```

#### Example of asynchronously loaded plugin control (using Vite)

```javascript
var origo = Origo('index.json', {
 controls: {
   swiper: async () => (await import("swiper-plugin")).default,
 }
});
```


#### Example of asynchronously loaded plugin control (without bundler)

```javascript
var origo = Origo('index.json', {
 controls: {
   swiper: async () => (await import("./plugins/swiper/swiper.min.js")).default,
 }
});
```
