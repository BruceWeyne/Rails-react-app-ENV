# Docker Environment Build for Ruby on Rails & React with API

## 1. FIle set
docker-compose.yml
api
- Dockerfile
- entrypoint.sh
- Gemfile
- Gemfile.lock

front
- Dockerfile

## 2. Set up projrct name
Replace all written by "{project-name}" with your own.

## 3. Execute build
```
$ docker-compose run api rails new . --force --no-deps --database=postgresql --api
$ docker-compose build
$ docker-compose run --rm front sh -c "npm install -g create-react-app && create-react-app rails-react-app"
```

## 4. Alter api/config/database.yml
```
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password: postgres
  pool: 5
```

## 5. Create Database
```
$ docker-compose run api rake db:create
$ docker-compose run api rake db:migrate
```

## 6. Launch server
```
$ docker-compose up
```

### Then, you'll see with,
```
Rails: localhost:3001
React: localhost:8000
```