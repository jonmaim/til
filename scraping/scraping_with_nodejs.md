# Scraping with NodeJS

## Puppeteer

Allows to screenshot websites by rendering them through a headless Chromium instance.

`npm install puppeteer --save`

Starting from v3.0.0 Puppeteer starts to rely on Node 10.18.1+.

Puppeteer sets an initial page size to 800×600px, here is how to setup a bigger viewport:

```javascript
const puppeteer = require('puppeteer');

const browser = await puppeteer.launch({headless: false});
const page = await browser.newPage();

await page.setViewport({
  width: 1200,
  height: 1024,
  deviceScaleFactor: 1,
});
```
### Immprove scraping speedd by blocking ads

Intercepting url requests before they are executed allow us to be able to abort requests to ad domains. 

First step is to download a list of ad domain:

`wget http://winhelp2002.mvps.org/hosts.txt`

Here is how to populate our list of ad hosts:

```javascript
const hosts = {};

function setupAdBlock() {
  const hostFile = fs.readFileSync('hosts.txt', 'utf8').split('\n');
  for (let i = 0; i < hostFile.length; i++) {
    const frags = hostFile[i].split(' ');
    if (frags.length > 1 && frags[0] === '0.0.0.0') {
      hosts[frags[1].trim()] = true;
    }
  }
}
```
Here is how to ad-block each page:
```javascript
async function adBlock(page) {
  try {
    await page.setRequestInterception(true)
  } catch (err) { throw err; }

  page.on('request', request => {
    console.log(request.url());
    let domain = null;
    const frags = request.url().split('/');
    if (frags.length > 2) {
      domain = frags[2];
    }
    if (hosts[domain]) {
      request.abort();
    } else {
      request.continue();
    }
  });
}
// ...
adBlock(page);
```
