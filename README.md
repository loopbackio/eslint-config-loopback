# eslint-config-loopback

LoopBack's ESLint shareable configs.

## Requirements

- ESLint 9.x or higher
- Node.js 18.18.0 or higher

## Usage

Add `eslint` and `eslint-config-loopback` to `devDependencies`:

```bash
npm install -D eslint eslint-config-loopback
```

In your project root, create `eslint.config.js` (or `eslint.config.mjs`):

```javascript
import loopbackConfig from 'eslint-config-loopback';

export default [
  ...loopbackConfig,
];
```

Or if using CommonJS:

```javascript
module.exports = (async () => {
  const loopbackConfig = await import('eslint-config-loopback');
  return [
    ...loopbackConfig.default,
  ];
})();
```

Then in `package.json`, set your run script:

```json
{
  "scripts": {
    "lint": "eslint ."
  }
}
```

That's it. Try it out by running:

```bash
npm run lint
```

> It is recommended to set a `posttest` run script to auto lint after
> running tests:
>
> ```json
> {
>   "scripts": {
>     "lint": "eslint .",
>     "test": "mocha",
>     "posttest": "npm run lint"
>   }
> }
> ```

## Overriding rules

To override a particular rule, modify the configuration:

```javascript
import loopbackConfig from 'eslint-config-loopback';

export default [
  ...loopbackConfig,
  {
    rules: {
      'comma-dangle': 'off',
    },
  },
];
```

While adopting ESLint in existing projects, there may be too many errors to fix
at once. In such cases, it may be desirable to modify the [`rule setting`](https://eslint.org/docs/latest/use/configure/rules)
of individual rules:

- `"off"` - Turn the rule off
- `"warn"` - Turn the rule on as a warning (doesn't affect exit code)
- `"error"` - Turn the rule on as an error (exit code is 1 when triggered)

## Migrating from ESLint 8.x

If you're upgrading from an older version of this package that used ESLint 8.x:

1. Update your ESLint dependency to version 9.x or higher
2. Replace your `.eslintrc` or `.eslintrc.json` file with `eslint.config.js` as shown above
3. Update any custom rules to use the new flat config format

For more information about ESLint's flat config format, see the [ESLint configuration migration guide](https://eslint.org/docs/latest/use/configure/migration-guide).
