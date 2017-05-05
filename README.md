# Ng-Docker

A Dockerfile to create and run an Angular application using [Docker](https://www.docker.com/) and the latest [Node](https://nodejs.org/), [NPM](https://www.npmjs.com/) and [Angular CLI](https://cli.angular.io/).

## How to use

1. First of all, install Docker and Docker Compose;

2. If running on Windows, enable the Shared Drivers on Docker Settings;

3. Clone this repo;

4. Run the following command to create the project using Angular CLI (answer 'n' when asked to overwrite `README.md`):

```
docker-compose run --rm web ng new --skip-install --directory ./ --skip-commit --routing app_name
```

Change `app_name` with your application's name.

5. Edit the `.angular-cli.json` file. Add the following line to the 'defaults' section:

```
"poll":1000
```

It will looks like this:

```
"defaults": {
  "styleExt": "css",
  "component": {},
  "poll": 1000
}
```

6. Edit the `package.json` file. 

Change the line:
```
"start": "ng serve",
```

To:
```
"start": "ng serve --host 0.0.0.0",
```

7. Run `docker-compose up -d`;

8. Run `docker logs ng-web -f` and see the magic happening.

9. After seeing the `webpack: Compiled successfully` message, open `http://localhost:4200` in your browser.

## Considerations

1. The default `docker-compose.yml` config will open the `4200` port and map it to the same host port.

2. It will also open and map the `49153` port. This is needed for Live Reloading to work.

3. The `init.sh` script will delete the `node_modules` folder and reinstall all dependencies always when you start the container. This can take some time before the app become available.

## Contributions

If you want to contribute, open an issue or send me a pull request. ;)
