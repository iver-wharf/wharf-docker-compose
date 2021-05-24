# Wharf via Docker Compose

[![Codacy Badge](https://app.codacy.com/project/badge/Grade/7d9935f02bbb4aa38c76cd3bce7290af)](https://www.codacy.com/gh/iver-wharf/wharf-docker-compose/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=iver-wharf/wharf-docker-compose&amp;utm_campaign=Badge_Grade)

Run Wharf locally on your own machine using [Docker Compose](https://docs.docker.com/compose/)

For documentation on how to set this up, please visit
<https://iver-wharf.github.io/#/development/getting-started>

## Linting markdown

Requires Node.js (npm) to be installed: <https://nodejs.org/en/download/>

```sh
npm install

npm run lint

# Some errors can be fixed automatically. Keep in mind that this updates the
# files in place.
npm run lint-fix
```

---

Maintained by [Iver](https://www.iver.com/en).
Licensed under the [MIT license](./LICENSE).
