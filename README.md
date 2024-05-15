# template-react-app

A template appropriate for publishing a react application, with a step-by-step guide of how it has been built

## Using the template

Clone this repository.

Then from within the repo, create a react app using Vite, install the npm dependencies, and you're ready to go...

```bash
npm create vite@latest ./ -- --template react
npm install
```

### Installing Vitest for testing

These [instructions](https://www.robinwieruch.de/vitest-react-testing-library/) explain how to setup Vitest, the key stages summarised below.

1. Install vitest as a development dependency

```bash
npm install --save-dev vitest
```

2. Add a test script in **package.json**

```js
 "scripts": {
    "test": "vitest",
  },
```

3. Install jsdom to enable testing of HTML in Vitest.

```bash
npm install --save-dev jsdom
```

4. Include it in **vite.config.js**.

```js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  test: {
    environment: "jsdom",
  },
});
```

5. Install the React Testing Library.

```bash
npm install @testing-library/react @testing-library/jest-dom --save-dev
```

6. (MAY REPLACE WITH NON GENERIC STUFF) Add a test setup file in tests/setup.js with the following content:

```js
import { expect, afterEach } from "vitest";
import { cleanup } from "@testing-library/react";
import * as matchers from "@testing-library/jest-dom/matchers";

expect.extend(matchers);

afterEach(() => {
  cleanup();
});
```

7. (MAY REPLACE WITH NON GENERIC STUFF) Add the test setup in **vite.config.js**.

```js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  test: {
    globals: true,
    environment: "jsdom",
    setupFiles: "./tests/setup.js",
  },
});
```

8. A final install...

```bash
npm install @testing-library/user-event --save-dev
```

## REVIEWING AND DELETING IF NOT NECESSARY

Follow these [instructions](https://gist.github.com/cobyism/4730490), with the following stages:
