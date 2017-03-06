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
In `tbdeploy`, `tbauth` and `tbclient` create `dev.env` files from `sample.env`.
```bash
docker-compose up --build
docker-compose run auth_app rails db:create
docker-compose run auth_app rails db:migrate
curl localhost:3000
```
You'll see client on http://localhost:4000/ and auth service on http://localhost:3000/
