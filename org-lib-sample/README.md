# How to publish

1. name your package @clientscope/somepackagename
2. npm adduser --registry `http://0.0.0.0:4873/`
   pass your credentials, which are created and saved in htpasswd
3. npm publish --registry `http://0.0.0.0:4873/`

Would be better to include 2 and 3 steps into CI

Also, do not forger to include auto-version update, using next script:

```zsh
npm version patch
# https://docs.npmjs.com/updating-your-published-package-version-number
```

Or, you can add registry into config:
https://docs.npmjs.com/cli/v7/using-npm/registry
