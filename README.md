# vite-react-ts

A Vite React template inspired by the folder structure of Next.js.  
TypeScript version. For the JavaScript version [click here](https://github.com/FADHsquared/vite-react).

## Using this template

Create a local copy of this template with this command:

```
npx degit FADHsquared/vite-react-ts your-project-name
```

## Notes

- Place static assets in `src/assets`, pages in `src/pages`, and styles in `src/styles`.
- Add folders to your liking, for example you can create a folder `src/components` for your components, `src/layouts` for your layouts, etc.
- Does not include auto routing. For that I'm waiting for [vite-plugin-pages](https://github.com/hannoeru/vite-plugin-pages) to exit experimental stage, but if you have other solutions please inform me.
- To fix a `Could not find a declaration file for module 'module-name'`, look for a @types package for that module. For example, you can install `@types/react-router-dom` for `react-router-dom`. (That's just an example though, I already included `@types/react-router-dom` in this template's `package.json`)

## Recommendations for Adding Things!

1. **Tailwind CSS**  
   Because Vite supports PostCSS configs by default, setting up Tailwind is very easy. First let's install Tailwind and Autoprefixer:

   ```
   npm install --save-dev tailwindcss autoprefixer
   ```

   Now generate a default Tailwind and PostCSS config file:

   ```
   npx tailwindcss init -p
   ```

   Now customize the `tailwind.config.js` file. Please visit <https://tailwindcss.com/docs/guides/vue-3-vite> for details about the configuration file. Here I will leave my recommended config with JIT enabled and dark mode set to 'class'.

   ```js
   module.exports = {
     mode: 'jit',
     purge: ['./index.html', './src/**/*.{vue,js,ts,jsx,tsx}'],
     darkMode: 'class', // or 'media' or 'class'
     theme: {
       extend: {},
     },
     variants: {
       extend: {},
     },
     plugins: [],
   };
   ```

   Last step is to overwrite the `src/globals.css` with the three default Tailwind directives:

   ```css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   ```

   Now Tailwind CSS is ready to use in your project!

## Manual Template Setup

Please refer to [the repo for the JavaScript version of this template](https://github.com/FADHsquared/vite-react) because the setup process is very similar, with some clear differences like choosing TypeScript instead of JavaScript when initializing ESLint.

However, there is additional setup required before performing "Folder Structure, Router and React Helmet Setup".

Install [eslint-config-airbnb-typescript](https://www.npmjs.com/package/eslint-config-airbnb-typescript):

```
npm install --save-dev eslint-config-airbnb-typescript
```

Now change `"airbnb"` to `"airbnb-typescript"` in your extends list in .eslintrc.json. Also let the ESLint parser know where your `tsconfig.json` file is:

```diff
- "extends": ["airbnb", "airbnb/hooks", "prettier"],
+ "extends": ["airbnb-typescript", "airbnb/hooks", "prettier"],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": 12,
+   "project": "./tsconfig.json",
    "sourceType": "module"
  }
```

That's it. You can now continue with the next steps of manual template setup.
