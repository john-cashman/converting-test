---
slug: "/viewports"
title: "Responsive Viewports"
---

# Configuring Responsive Viewports

Master responsive testing with Argos: Easily configure viewports for Playwright, Cypress, and Puppeteer, ensuring your app looks great on any device.

## Prerequisites

This advanced feature integrates smoothly with [Playwright](/playwright), [Cypress](/cypress), and [Puppeteer](/puppeteer) to enhance your testing capabilities.

## Viewport Configuration

Adjust the `argosScreenshot()` command in your test scripts to capture responsive screenshots. You can specify exact dimensions or use device presets to mimic real-world scenarios:

```js
await argosScreenshot(..., 
  viewports: [
    "iphone-4", // Use device preset
    { width: 800, height: 600 , // Specify dimensions directly
     preset: "ipad-2", orientation: "landscape" , // Device preset with orientation
  ],
});
```

## Available Presets

List of available device presets with their respective dimensions:

| Preset        | Width (px) | Height (px) |
| ------------- | ---------- | ----------- |
| macbook-16    | 1536       | 960         |
| macbook-15    | 1440       | 900         |
| macbook-13    | 1280       | 800         |
| macbook-11    | 1366       | 768         |
| ipad-2        | 768        | 1024        |
| ipad-mini     | 768        | 1024        |
| iphone-xr     | 414        | 896         |
| iphone-x      | 375        | 812         |
| iphone-6+     | 414        | 736         |
| iphone-se2    | 375        | 667         |
| iphone-8      | 375        | 667         |
| iphone-7      | 375        | 667         |
| iphone-6      | 375        | 667         |
| iphone-5      | 320        | 568         |
| iphone-4      | 320        | 480         |
| iphone-3      | 320        | 480         |
| samsung-s10   | 360        | 760         |
| samsung-note9 | 414        | 846         |

## Troubleshooting and Best Practices

To ensure accurate rendering, always set the viewport size with `page.setViewportSize()` before navigating to the target page, as many sites do not dynamically adapt to changes in viewport size after the page has loaded. For comprehensive testing, consider running your tests across all intended viewports to validate responsive behavior across the board.
