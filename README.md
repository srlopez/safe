# SAFE Stack Container

Dockerfile in https://github.com/srlopez/safe

To build image

`docker build -t safe:10.2.3 .`

I use as a console to develop SAFE apps with my user id, just to edit from outside the container with vscode.

`docker run --rm -it  --user $(id -u):$(id -g) -h SAFE --name SAFE -p 8080:8080 -e HOME=/app -v `pwd`:/app -w /app safe:10.2.3 bash`

Just to run first SAFE
```
dotnet new -i SAFE.Template
dotnet new SAFE --layout fulma-landing --communication remoting
```
Edit webpack.config.js and add host to publish devServer outside the container
```
  // Configuration for webpack-dev-server
    devServer: {
        host: '0.0.0.0',
        ...
    }
```

Build as 
```
fake build --target run
```
And then go to http://localhost:8080