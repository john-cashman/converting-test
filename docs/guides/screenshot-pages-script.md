---
slug: "/screenshot-pages-script"
title: "Screenshots from URLs"
---

# Capture Screenshots from URLs

Efficiently capture web page screenshots across frameworks with Argos: A step-by-step guide for Playwright, Cypress, and Puppeteer integration.

## Using Playwright

Below is a step-by-step script for Playwright to take screenshots of specified pages. This script utilizes the Argos Playwright integration for streamlined screenshot capture:

```js
// screenshot-pages.spec.ts


const pages = [
   name: "homepage", path: "/" ,
   name: "faq", path: "/faq" ,
   name: "contact", path: "/contact-us" ,
   name: "pricing", path: "/pricing" ,
];

for (const  name, path  of pages) 
  test(`Run Argos on ${name ($path)`, async ( page ) => 
    await page.goto(path);
    await argosScreenshot(page, name);
  );
}
```

## Using Cypress

Here's how you can capture screenshots within Cypress. The script navigates to each page and uses the Argos Cypress command for screenshots:

```js
// screenshot-pages.spec.ts
const pages = [
   name: "homepage", path: "/" ,
   name: "faq", path: "/faq" ,
   name: "contact", path: "/contact-us" ,
   name: "pricing", path: "/pricing" ,
];

for (const  name, path  of pages) 
  it(`Run Argos on ${name ($path)`, () => 
    cy.visit(path);
    cy.argosScreenshot(name);
  );
}
```

## Using Puppeteer

or Puppeteer users, this script demonstrates how to capture page screenshots effectively. It employs Puppeteer for navigation and screenshot capture:

```js
// screenshot-pages.spec.ts


const baseUrl = "http://localhost:3000";
const pages = [
   name: "homepage", path: "/" ,
   name: "faq", path: "/faq" ,
   name: "contact", path: "/contact-us" ,
   name: "pricing", path: "/pricing" ,
];

(async () => 
  const browser = await puppeteer.launch();
  const page = await browser.newPage();

  for (const { name, path  of pages) 
    await page.goto(`${baseUrl$path`);
    await page.screenshot( path: `${name.png` });
  }

  await browser.close();
})();
```
