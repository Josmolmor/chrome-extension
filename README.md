# Altru chrome extension
Chrome installable extension. Made for Altru Labs using Vue and Webpack.

![altru](https://assets.website-files.com/5d71246584d80240ec1470f0/5d71246584d80278e914713b_logo.svg)

## Setup

 1. Clone the repository
 2. Install dependecies with `yarn`
 3. Build a development version with `yarn build:dev`

## Usage
 1. Type `chrome://extensions` in the search bar
 2. Turn the the top-right switch `Developer mode` on
 3. Look for the button `Load unpacked` at the top-left and select the `dist` folder found in the root's path of the extension.
4. Once you have loaded the extension pack, `vue-web-extension` allows you to keep watching for new changes and hot reload the extension. To make use of this, you simply need to run `yarn watch:dev`.
