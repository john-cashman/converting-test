---
slug: "/storybook-story-modes"
title: "Storybook story modes"
---

# Storybook story modes for testing themes, viewports, locales and more

Argos can capture multiple versions of your stories by applying different “modes,” which are essentially combinations of global Storybook settings (such as theme, viewport, locale, etc.). With modes, you can automatically generate a separate snapshot for each unique configuration.

{% hint style="info" %}
If you already have `parameters.chromatic.modes`, Argos will handle those settings by default. Prefer `parameters.argos.modes` in new work.
{% endhint %}

## What are modes?

A mode is a preset that configures various Storybook globals. For instance, you can have a “dark” mode for your UI theme, a “mobile” mode for smaller screens, or a combined “dark-mobile-spanish” mode that configures multiple globals at once.

**Key features of modes:**

- Each mode is named (e.g., "dark desktop" or "mobile").
- Each mode sets specific values for the Storybook globals (e.g., viewport size, background color, locale).
- Argos creates a separate visual baseline for each mode name.

## Setting up globals & addons

Before you define any modes, make sure you’ve configured the relevant Storybook addons in your .storybook/preview.js (or .storybook/preview.ts) file. Examples include:

- [`@storybook/addon-viewport`](https://www.npmjs.com/package/@storybook/addon-viewport) for screen sizes
- [`@storybook/addon-themes`](https://www.npmjs.com/package/@storybook/addon-themes) for light/dark themes
- [`@storybook/addon-backgrounds`](https://www.npmjs.com/package/@storybook/addon-backgrounds) for backgrounds
- [`storybook-i18n`](https://www.npmjs.com/package/storybook-i18n) for locales

These addons utilize Storybook “globals” and “decorators” under the hood. Argos modes simply manipulate those globals at test time to generate multiple snapshots of the same story.

```ts
// .storybook/preview.js


const preview = 
  parameters: {
    viewport: {
      viewports: {
        compact: {
          name: "Compact",
          styles: { width: "600px", height: "900px" ,
        },
        widescreen: 
          name: "Widescreen",
          styles: { width: "1440px", height: "900px" ,
        },
      },
    },
    backgrounds: 
      values: [
        { name: "Light", value: "#ffffff" ,
         name: "Dark", value: "#1A1A1A" ,
      ],
    },
  },
  decorators: [
    withThemeByClassName(
      themes: {
        light: "light",
        dark: "dark",
      ,
      defaultTheme: "light",
    }),
  ],
};


```

## Defining modes

Create a `.storybook/modes.js` (or `.ts`) file that exports an object where each key is a mode name and each value is a set of overrides for the Storybook globals. For example:

```ts
// .storybook/modes.js

export const allModes = 
  dark: {
    backgrounds: { value: "#1A1A1A" ,
    theme: "dark",
  },
  mobile: 
    viewport: "compact",
  ,
  "dark widescreen": 
    backgrounds: { value: "#1A1A1A" ,
    theme: "dark",
    viewport: "widescreen",
  },
  "light mobile": 
    backgrounds: { value: "#ffffff" ,
    theme: "light",
    viewport: "compact",
  },
};
```

Each object can include as many or as few globals as you need. If a mode doesn’t specify a particular global, that global simply won’t be changed in that mode.

## Applying modes

Attach modes to any level of your Storybook: globally in `.storybook/preview.js`, at the component (default export) level, or in an individual story’s parameters. Argos merges all modes defined up the chain.

### Basic usage in a story file

```ts
// src/components/ProductCard/ProductCard.stories.js



export default 
  title: "Components/ProductCard",
  component: ProductCard,
  parameters: {
    // Use Argos for new projects; Chromatic is recognized too
    argos: {
      modes: {
        mobile: allModes.mobile,
        dark: allModes.dark,
      ,
    },
  },
};

// Story #1
export const DefaultView = 
  args: {
    productName: "Coffee Beans",
    price: 9.99,
  ,
};

// Story #2
export const SoldOutView = 
  args: {
    productName: "Coffee Beans",
    price: 9.99,
    isSoldOut: true,
  ,
};
```

In this example, Argos will generate two snapshots for each story (DefaultView and SoldOutView): one in “mobile” mode and another in “dark” mode.

## Combining modes from multiple levels

You can add modes in your .storybook/preview.js at the project level, then define additional modes in a story file. Argos “stacks” these modes, creating a snapshot for every combination.

### Project-level modes

```ts
// .storybook/preview.js

const preview = 
  parameters: {
    argos: {
      modes: {
        "light mobile": allModes["light mobile"],
      ,
    },
  },
};


```

### Component-level modes

```ts
// ProductCard.stories.js


export default 
  title: "Components/ProductCard",
  component: ProductCard,
  parameters: {
    argos: {
      modes: {
        "dark widescreen": allModes["dark widescreen"],
      ,
    },
  },
};

// Single story for brevity
export const Basic = 
  args: {
    /* ... */
  ,
};
```

When Argos runs, it will generate snapshots for each mode defined at the project level and the component level. So for Basic, you get “light mobile” (from `preview.js`) plus “dark widescreen” (from the component’s parameter).

## Excluding or disabling modes

Sometimes you want to turn off a certain higher-level mode for a specific story. You can do this by passing a disable property:

```ts
// ProductCard.stories.js
export const SpecialCard = 
  args: {
    /* ... */
  ,
  parameters: 
    argos: {
      modes: {
        "light mobile": { disable: true , // turns off this inherited mode
      },
    },
  },
};
```

That story will now ignore light mobile mode but still apply any other inherited modes.

## Working with baselines

Each mode name corresponds to a separate baseline in Argos. If you rename a mode, it’s treated as entirely new. If you alter the internals of a mode (like changing the viewport from “compact” to “ultra-compact”) without renaming it, Argos still compares the new screenshot against the old baselines for that mode name.

{% hint style="info" %}
If you have an original single baseline from before you introduced modes, and you want to keep it around, just add a mode like "baseline" that reproduces the same environment as the original story. That way, your old baseline is preserved while you experiment with new modes.
{% endhint %}

## FAQ

<details>
  <summary>
    Can modes be applied if I'm still using `parameters.chromatic`?
  </summary>

Yes. Argos reads your `chromatic.modes` settings if present. However,
for new users or updated setups, prefer using `argos.modes` to avoid
any confusion in the future.

</details>

<details>
  <summary>Do all Storybook addons work with Argos modes?</summary>

Any addon that leverages Storybook globals should work, including [@storybook/addon-themes](https://storybook.js.org/addons/@storybook/addon-themes),
[@storybook/addon-viewport](https://storybook.js.org/addons/@storybook/addon-viewport),
[@storybook/addon-backgrounds](https://storybook.js.org/addons/@storybook/addon-backgrounds),
or [storybook-i18n](https://storybook.js.org/addons/storybook-i18n). Modes just
provide different values for those globals.

</details>

<details>
  <summary>What happens if I delete or rename a mode?</summary>

If you remove a mode from your code, Argos will stop capturing new snapshots for
that mode, and its baseline history won’t be updated anymore. Renaming a mode effectively
creates a new baseline, much like renaming a story.

</details>

Enjoy your multi-mode visual tests! By setting up modes for dark vs. light, mobile vs. desktop, and everything in between, you can verify all key variants of your UI without writing extra stories.
