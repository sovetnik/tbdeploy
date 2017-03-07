## Deployment

Implementation of Single sign on [service](https://github.com/sovetnik/tbauth) and [client](https://github.com/sovetnik/tbclient).
We have two apps, and want it running on one docker host.
To achive this, we added them as submodules and provide common configuration.

```bash
git clone https://github.com/sovetnik/tbdeploy.git
cd tbdeploy
git submodule update --init --recursive
```

## Run in development
In `tbdeploy`, `tbauth` and `tbclient` create `dev.env` files from `dev.env.sample`.
```bash
docker-compose up --build
docker-compose run auth_app rails db:create db:migrate
curl localhost:3000
```
You'll see client on http://localhost:4000/ and auth service on http://localhost:3000/

## Run in production

First, create `.env` files from samples and set production variables:
- auth.env
- client.env
- prod.env

Set domain name in `auth.conf` and `client.conf`

Run Docker-compose
```bash
docker-compose -f docker-compose-production.yml up --build
```
and one time 
```bash
docker-compose -f docker-compose-production.yml exec auth_app rails db:create db:migrate
```
