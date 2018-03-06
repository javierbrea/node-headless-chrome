# Node Headless Chrome

Headless Chrome installed in a container created from node 8.9.4, for Puppeteer usage.

[![Docker Pulls](https://img.shields.io/docker/pulls/javierbrea/node-headless-chrome.svg)](https://hub.docker.com/r/javierbrea/node-headless-chrome/)

## Usage

This image is intended to be used as a dependency for docker images that need to run [Puppetter](https://www.npmjs.com/package/puppeteer) in order to execute end-to-end tests, for example.

> For further info: https://github.com/GoogleChrome/puppeteer/blob/master/docs/troubleshooting.md

It does not include Puppeteer dependency installed, it only installs the dependencies that the bundled Chromium that Puppeteer installs is missing.

It does not configure nor provide an specific user to run Headless Chrome, it just simply install the required dependencies to make Puppeteer work.

Inside your nodejs code, when running puppeteer, you'll need to pass arguments to Headless Chrome in order to run it without sandbox.

```js
const puppeteer = require('puppeteer')

puppeteer.launch({
  args: [
    '--no-sandbox',
    '--disable-setuid-sandbox'
  ]
})
```

> Warning: running without the sandbox is not recommended due to security reasons! So, use it only for making request to trusted sources, such as your own developed services that are going to be tested using Puppeteer.