# Reproduction for Env bug

When an `.env` file contains a self-reference assignment (e.g. `FOO=$FOO`), the storybook process bails. This happens because of a bug in dotenv-expand that was fixed in v11.0.0 - however Storybook's own env loading dependency uses an older version.alert

Fixed in https://github.com/storybookjs/lazy-universal-dotenv/pull/5

To reproduce:

Note the `.env.` file in this repo that has:

```
FOO=$FOO
```

To observe the error run:

```
npm run storybook
```

See full bug https://github.com/storybookjs/storybook/issues/33466
