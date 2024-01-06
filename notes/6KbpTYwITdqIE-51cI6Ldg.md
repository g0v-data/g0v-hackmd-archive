---
tags: cofacts
GA: UA-98468513-3
---

Running Cofacts on Laptop: README
====

Video Intro
{%youtube vAym6ABz0og%}

## Prerequisite

- [`git`](https://git-scm.com/downloads) for cloning repositories
- [`Node.js >= 8`](https://nodejs.org/en/download/package-manager/#nvm) for schema & seed
- [`docker`](https://store.docker.com/search?type=edition&offering=communityd) & [`docker-compose`](https://docs.docker.com/compose/install/#install-compose)
- 2GB memory in prod env

## Steps

### Clone repositories

Please clone these 2 repositories:

```bash
$ git clone https://github.com/cofacts/rumors-deploy.git
$ git clone https://github.com/cofacts/rumors-db.git
```

The README of these directories are still under work. After the finishing touches, README of all repositories should share a same strucutre.

#### `cofacts/rumors-deploy`

This repository contains the deploy scripts (docker-compose.yml) that actually runs the components of Cofacts.

There are 2 `docker-compose` YML files:

- `docker-compose.sample.yml`: Minimal setup to get all Cofacts service running on a single computer.
- `docker-compose.production.yml`: The actual setup (with secrets redacted) that is running on cofacts.g0v.tw . The differences are:
    - We run productin LINE bot service on heroku, thus there is no `line-bot` and `redis` in `docker-compose.production.yml`
    - Additionally, `nginx` is added as a reverse-proxy and serves https certificates.

To run Cofacts on laptop, we can just use `docker-compose.sample.yml`.

Run the following to create `docker-compose.yml` from the sample file so that we don't need to add extra arguments when invoking `docker-compose`.

```bash
$ cd rumors-deploy

rumors-deploy $ cp docker-compose.sample.yml docker-compose.yml
```

#### `cofacts/rumors-db`

### Inspecting logs

It will be handy if we keep a terminal that shows logs of the following operations.

Run the following in a *separate* terminal to 

```bash
rumors-deploy $ docker-compose logs -f
```

### Start DB

You need to prepare the permissions

```bash
rumors-deploy $ docker-compose up -d db
```

:::warning
### Caveats

If your are running into memory issue:

Try changing kernel settings: https://www.elastic.co/guide/en/elasticsearch/reference/6.3/docker.html#docker-cli-run-prod-mode

If all your elasticsearch indexes became read-only, :
https://stackoverflow.com/a/34911897
:::

:::success
You should be seeing the DB up and running here:
http://localhost:62222/
:::

### Initialize DB


This repository contains the database mapping and the setup scripts.

```bash
$ cd rumors-db

$ npm i
```
Before we run any scripts, we will need to specify the url of elasticsearch database. Please open up the editor of your choice and edit `.env` to  replace `localhost:62223` with `localhost:62222` :

```bash
# In rumors-db's directory:
#
$ vim .env

# Change localhost:62223 to localhost:62222
```
 
Now we can run the scripts (remember to run `npm install` beforehand):

```bash
# In rumors-db's directory:
#

$ npm run schema # creates Elasticsearch index & mappings
$ npm run seed
```

### Start other services

[<img src="https://docs.google.com/drawings/d/1VfooYFnEb_mVx9Yso_u9evYD-nq-Y-mDSwsIlg7oDlw/pub?w=846&amp;h=467">](https://docs.google.com/drawings/d/1VfooYFnEb_mVx9Yso_u9evYD-nq-Y-mDSwsIlg7oDlw/edit)

```bash
# In rumors-deploy's directory:
#
$ docker-compose up -d url-resolver # Run on localhost:4000
$ docker-compose up -d api # Run on localhost:5000
$ docker-compose up -d site # Run on localhost:3000
```

### Update `/etc/hosts`

To connect API server and the site within docker network, we are using the hostname "`api`". Since the URL will go to the browser as well, we will need to teach the laptop about this hostname:

```
# /etc/hosts
# Add the following line:

127.0.0.1 api
```

### Get the LINE bot running!

#### Get channel ID and secret for LINE chatbot

Please follow the [official guide](https://developers.line.me/en/docs/messaging-api/getting-started/) to:
- register LINE via email
- register as a developer
- create a "channel"
- get channel access token https://developers.line.me/en/docs/messaging-api/building-bot/

#### Fill in tokens

Edit `docker-compose.yml` in `rumors-deploy` to fill in:

```yml
  - LINE_CHANNEL_SECRET=<paste LINE@'s channel secret here>
  - LINE_CHANNEL_TOKEN=<paste LINE@'s channel token here>
```
## Running on production machine

### Machine planning

As explained when we introduce `docker-compose.production.yml`, we do not host rumors-line-bot on the same machine with other components. If you want to separate components to different machines, we suggest:

- Put database and `rumors-api` together / as near as possible
- `rumors-site` can be served in separate machine
- `rumors-line-bot` can be served in separate machine
- `url-resolver` can be served in separate machine

### Log management

Choose one of the following:

- [Using logrotated](https://sandro-keil.de/blog/logrotate-for-docker-container/)
- [Using docker built-in log-rotate mechanism](https://medium.freecodecamp.org/how-to-setup-log-rotation-for-a-docker-container-a508093912b2)

### HTTPS
