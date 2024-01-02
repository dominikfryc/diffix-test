# Diffix - Web Components UI Library

[![Storybook](https://raw.githubusercontent.com/dominikfryc/diffix-test/next/docs/assets/storybook-button.svg)](https://www.diffix.dev)
[![GitHub](https://raw.githubusercontent.com/dominikfryc/diffix-test/next/docs/assets/github-button.svg)](https://github.com/dominikfryc/diffix-test)
[![npm](https://raw.githubusercontent.com/dominikfryc/diffix-test/next/docs/assets/npm-button.svg)](https://www.npmjs.com/package/diffix-test)

Diffix Web Components is a modern, performant, customizable, open-source UI library. Provides a set of reusable components to build web applications with consistent user experience.

- Build a modern, highly performant, and highly accessible web experience.
- Integrate with any JavaScript framework such as React, Vue, Angular, Svelte, etc.
- Build a standards-based user interface following W3C Web Component standards.
- Customize the design language for your project by modifying design tokens.
- Use the components out-of-the-box in existing front-end projects.

## Instalation

Ensure you have the latest [Node.js](https://nodejs.org/) installed on your machine. Use a package manager to install Diffix from [npm](https://www.npmjs.com/package/diffix-test):

```bash
npm install diffix-test
```

## Import components

Import the target component from `diffix-test/components/component-name`. Import automatically registers the Web Component (causes a side effect).

```ts
import 'diffix-test/components/button';
```

Or you can import all components at once:

```ts
import 'diffix-test';
```

## Import theme

To use the default theme, import the CSS file. There are two ways to do this:

1. Using an application bundler (Webpack, Rollup, Vite, etc.):

```ts
import 'diffix-test/themes/default.css';
```

2. Or using a `<link>` tag:

```html
<link href="/node_modules/diffix-test/dist/themes/default.css" rel="stylesheet" />
```

## Usage

Diffix components are designed to be used as Web Components. This means you import the target component in the script and then use it in the HTML.

```html
<dfx-button theme="primary" variant="filled">Button</dfx-button>
```

Form controls should be automatically detectable inside the `form` element. You can use the `FormData` to serialize data from the form. Client-side validation uses [Constraint Validation API](https://developer.mozilla.org/en-US/docs/Web/API/Constraint_validation). You can activate it using attributes such as `required`, `minlength`, `maxlength`, `pattern`, etc.

```html
<form>
  <dfx-input label="Name" name="name" required></dfx-input>
  <dfx-button type="submit" variant="filled">Submit</dfx-button>
</form>

<script>
  document.querySelector('form').addEventListener('submit', event => {
    event.preventDefault();
    const formData = new FormData(event.target);
    alert(JSON.stringify(Object.fromEntries(formData)));
  });
</script>
```

Components are published as ES modules so that they can be used in all modern browsers with no build step. That's good for prototyping, but for performance reasons, components in production should be bundled, tree-shaken, and optimized by individual applications using bundlers like Webpack, Rollup, or Vite.

There is a [simple demo](https://github.com/dominikfryc/diffix-test/tree/next/demo/) using Vite to showcase the usage of individual components.

## Attribution

Special thanks to the following projects that help make this project possible:

- Components are built with [Lit](https://lit.dev/), [Vite](https://vitejs.dev/), and [TypeScript](https://www.typescriptlang.org/).
- Component tests run on [Web Test Runner](https://modern-web.dev/docs/test-runner/overview/) and [Playwright](https://playwright.dev/).
- Documentation is built with [Storybook](https://storybook.js.org/) and hosted on [Netlify](https://www.netlify.com/).
- Components are linted with [ESLint](https://eslint.org/) and formatted with [Prettier](https://prettier.io/).
- Component metadata is generated by the [Custom Elements Manifest Analyzer](https://custom-elements-manifest.open-wc.org/).
- Components are published to [npm](https://www.npmjs.com/) with [Semantic Release](https://semantic-release.gitbook.io/semantic-release/) and [GitHub Actions](https://github.com/features/actions).

## Contribute

As an open-source project, all contributions are welcome! Feel free to report bugs and submit feature requests. Please read the [Contributing Guide](https://github.com/dominikfryc/diffix-test/blob/next/CONTRIBUTING.md) if you want to contribute to the code.

## License

Diffix was created by [Dominik Fryč](https://github.com/dominikfryc). It's available under the [MIT license](https://github.com/dominikfryc/diffix-test/blob/next/LICENSE.md). You can use it in any project, commercial or not, with or without attribution.
