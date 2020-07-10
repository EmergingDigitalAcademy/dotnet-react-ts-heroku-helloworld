# Experiments with dotnet core

This project is basically the standard template project generated with `dotnet new reactredux`, which is a fake WeatherForecast API with a react+redux app, written in typescript.

This project has also been updated to include a proxy from the webapp to the api, and vice versa (both work!). It is implied that you will run the client and server separately: `dotnet run` and `cd ClientApp && npm start`

There is also a `package.json` in the root folder which lets us easily deploy the whole thing to heroku:

```
heroku create --buildpack https://github.com/jincod/dotnetcore-buildpack.git
heroku buildpacks:set jincod/dotnetcore
heroku config:set ASPNETCORE_ENVIRONMENT=Production

# Then to deploy, just commit and push:
git push heroku master
```

Heroku will build the react app (with `npm run build` in the ClientApp folder) and start the kestrel server (with `./react-redux-helloworld`). The whole thing works really well!

Demo currently up here: https://young-escarpment-60497.herokuapp.com/
