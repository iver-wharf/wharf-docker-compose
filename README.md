# Wharf via Docker Compose

[![Codacy Badge](https://app.codacy.com/project/badge/Grade/7d9935f02bbb4aa38c76cd3bce7290af)](https://www.codacy.com/gh/iver-wharf/wharf-docker-compose/dashboard?utm_source=github.com\&utm_medium=referral\&utm_content=iver-wharf/wharf-docker-compose\&utm_campaign=Badge_Grade)

Run Wharf locally on your own machine using [Docker Compose](https://docs.docker.com/compose/)

```console
$ docker-compose -f docker-compose.yml pull
Pulling proxy                ... done
Pulling api                  ... done
Pulling provider-gitlab      ... done
Pulling provider-github      ... done
Pulling provider-azuredevops ... done
Pulling db                   ... done

$ docker-compose -f docker-compose.yml up --abort-on-container-exit
Creating network "wharf_default" with the default driver
Creating wharf_provider-gitlab_1      ... done
Creating wharf_provider-azuredevops_1 ... done
Creating wharf_api_1                  ... done
Creating wharf_db_1                   ... done
Creating wharf_proxy_1                ... done
Creating wharf_provider-github_1      ... done
Attaching to wharf_provider-gitlab_1, wharf_provider-github_1, wharf_provider-azuredevops_1, wharf_db_1, wharf_api_1, wharf_proxy_1
```

The `-f docker-compose.yml` flag is necessary as the
`docker-compose.override.yml`, that's loaded in by default if no files are
specified with `-f`, contains instructions on building Wharf from source.

## Building from source

For documentation on how to set this up for development purposes, please visit
<https://iver-wharf.github.io/#/development/getting-started>

The gist is that you need to clone the other Git repositories next to this
repository, then link the `docker-compose.yml` and `docker-compose.override.yml`
files, and then run `docker-compose build`.

```console
$ cd ..

$ ls -1
wharf-api
wharf-docker-compose
wharf-provider-azuredevops
wharf-provider-github
wharf-provider-gitlab
wharf-web

$ ln -sfv wharf-docker-compose/docker-compose.yml docker-compose.yml
'docker-compose.yml' -> 'wharf-docker-compose/docker-compose.yml'

$ ln -sfv wharf-docker-compose/docker-compose.override.yml docker-compose.override.yml
'docker-compose.override.yml' -> 'wharf-docker-compose/docker-compose.override.yml'

$ docker-compose build
Building api
STEP 1: FROM golang:1.16.3 AS build
STEP 2: WORKDIR /src
--> Using cache b9ae911f531d8d3ffbdb0c228a7c70de134177a9c30e5dcc5010e0af7d5e77be
--> b9ae911f531
STEP 3: RUN go get -u github.com/swaggo/swag/cmd/swag@v1.7.0
--> Using cache 877cbea183468f7b01031df26efe1440c617855f2c46692292b1b8ec2501bd70
--> 877cbea1834
STEP 4: COPY go.mod go.sum /src/

// ...a lot of build logs

$ docker-compose up --abort-on-container-exit
Creating network "wharf_default" with the default driver
Creating wharf_provider-gitlab_1      ... done
Creating wharf_provider-azuredevops_1 ... done
Creating wharf_api_1                  ... done
Creating wharf_db_1                   ... done
Creating wharf_proxy_1                ... done
Creating wharf_provider-github_1      ... done
Attaching to wharf_provider-gitlab_1, wharf_provider-github_1, wharf_provider-azuredevops_1, wharf_db_1, wharf_api_1, wharf_proxy_1
```

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
