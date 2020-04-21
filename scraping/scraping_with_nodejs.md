# Scraping with NodeJS

## Puppeteer

Allows to screenshot websites by rendering them through a headless Chromium instance.

`npm install puppeteer --save`

Starting from v3.0.0 Puppeteer starts to rely on Node 10.18.1+.

Puppeteer sets an initial page size to 800×600px, here is how to setup a bigger viewport:

```
const puppeteer = require('puppeteer');

const browser = await puppeteer.launch({headless: false});
const page = await browser.newPage();

await page.setViewport({
  width: 1200,
  height: 1024,
  deviceScaleFactor: 1,
});
```
