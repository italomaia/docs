# What is Python?

Lua is an interpreted, interactive, embeddable, lightweight, multi-paradigm, open-source programming language. It incorporates modules, error handling, dynamic typing, coroutines and first class functions. 

> [wikipedia.org/wiki/Lua_(programming_language)](https://en.wikipedia.org/wiki/Lua_%28programming_language%29)

%%LOGO%%

# How to use this image

## Create a `Dockerfile` in your Python app project

```dockerfile
FROM %%IMAGE%%:5

WORKDIR /root

RUN luarocks install busted

COPY . .

CMD [ "lua", "./your-daemon-or-script.lua" ]
```

You can then build and run the Docker image:

```console
$ docker build -t my-lua-app .
$ docker run -it --rm --name my-running-app my-lua-app
```

## Run a single Lua script

For single file projects, you may find it inconvenient to write a complete `Dockerfile`. In such cases, you can run a Lua script by using the Lua Docker image directly:

```console
$ docker run -it --rm --name my-running-script -v "$PWD":/root -w /root %%IMAGE%%:5 lua your-daemon-or-script.lua
```
