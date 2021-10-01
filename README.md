# Verdaccio component sharing boilerplate

## Tools:

- Verdaccio
- Docker
- npm or yarn

<br />

## Verdaccio setup on server side:

1. Install Verdaccio (run on `0.0.0.0:4873` by default)

```zsh
npm i -g verdaccio
verdaccio
```

p.s. for install vim inside an alpine container

```zsh
apk update
apk add vim
```

2. You have to change config, for restrict other users
   /path/to/config/verdaccio/config.yaml

```yaml
uplinks:
  npmjs:
    url: https://registry.npmjs.org/
    # I prefer to disable cache from npmjs.org
    cache: false
---
htpasswd:
  file: ./htpasswd
  # You can set this to -1 to disable registration.
  max_users: -1
---

---
"@clientscope/*":
  # scoped packages
  access: $authenticated
  publish: $authenticated
  unpublish: $authenticated
  proxy: npmjs
```

3. Add users, go here https://hostingcanada.org/htpasswd-generator/ and generate credentials, then add this credentials to /path/to/config/verdaccio/htpasswd

## Client site plug in
