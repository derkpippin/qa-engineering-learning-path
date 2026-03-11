# Phase 3: Getting Started with Playwright

## Installation
To install Playwright, you can use npm, the package manager for JavaScript. Run the following command in your terminal:

```bash
npm install -D playwright
```

This command installs Playwright and its dependencies. You can also install specific browsers:

```bash
npx playwright install
```

## First Test
Once you have installed Playwright, you can write your first test. Create a file called `firstTest.spec.js` and add the following code:

```javascript
const { test, expect } = require('@playwright/test');

test('basic test', async ({ page }) => {
  await page.goto('https://example.com');
  const title = await page.title();
  expect(title).toBe('Example Domain');
});
```

To run the test, use the command:

```bash
npx playwright test firstTest.spec.js
```

## Selectors
Playwright supports various selector types. Here are a few examples:
- CSS Selectors: `await page.click('button#submit');`
- Text Selectors: `await page.click('text=Submit');`
- XPath Selectors: `await page.click('//button[text()=\'Submit\']');`

## Basic Automation Examples
1. **Filling out a form:**
   ```javascript
   await page.fill('input[name="username"]', 'myUsername');
   await page.fill('input[name="password"]', 'myPassword');
   await page.click('button#login');
   ```

2. **Taking a screenshot:**
   ```javascript
   await page.screenshot({ path: 'example.png' });
   ```

3. **Navigating through multiple pages:**
   ```javascript
   const [newPage] = await Promise.all([
     context.waitForEvent('page'),
     page.click('a#newPage')
   ]);
   ```

Cascading your tests will become important as you build more complex flows. Happy testing!