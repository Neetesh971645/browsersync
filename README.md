BrowserSync plugin for Webpack

Easily use BrowserSync in your Webpack project.
----------------------------------------------------------------------

Install:
yarn add -D browser-sync-webpack-plugin
----------------------------------------------------------------------

Usage:
BrowserSync will start only when you run Webpack in watch mode:
----------------------------------------------------------------------

Basic:

If you're not using Webpack Dev Server, you can make BrowserSync to serve your project. The setup is pretty easy: just pass the BrowserSync options to the plugin as the first argument.

In your webpack.config.js:

const BrowserSyncPlugin = require('browser-sync-webpack-plugin')
----------------------------------------------------------------------

Advanced:
The advanced usage is about using Webpack Dev Server with BrowserSync in order to use awesome features of both.

To achieve this, BrowserSync offers the proxy option. So, basically, you are about to proxy the output from the Webpack Dev Server through BrowserSync to get the best out of both.

In your webpack.config.js:

const BrowserSyncPlugin = require('browser-sync-webpack-plugin')

module.exports = {
  // ...
  plugins: [
    new BrowserSyncPlugin(
      // BrowserSync options
      {
        // browse to http://localhost:3000/ during development
        host: 'localhost',
        port: 3000,
        // proxy the Webpack Dev Server endpoint
        // (which should be serving on http://localhost:3100/)
        // through BrowserSync
        proxy: 'http://localhost:3100/'
      },
      // plugin options
      {
        // prevent BrowserSync from reloading the page
        // and let Webpack Dev Server take care of this
        reload: false
      }
    )
  ]
}

----------------------------------------------------------------------