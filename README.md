# Curator

Curator is lightweight client-server library that lets developers remotely control devices with custom commands.

## Install
> There are no external dependencies for curator, it's using only standard library

```bash
go get github.com/gelidus/curator-server # server library

go get github.com/gelidus/curator-client # client library
```

## Getting started

Curator consists of so-called **pipelines**, which let you execute more commands in an order. These pipelines are made of **commands**. You are not forced to use pipeline-ing, you can simply send just one command. You can also specify **middleware** if you want to do something for all commands and pipelines.

### Initializing server

```go
package main

import curator "github.com/gelidus/curator-server"

func main() {
  // create new curator server
  server := curator.New()

  // add middleware

  // add commands

  // add pipelines

  // run server on port 8888 for anyone
  server.run(":8888")
}
```

### Command

We will start by creating simple command **package**. Package is archive (zip, tar.gz, ...) which must consist of script called *run*. This may be bash, python or whatever you want.

#####1.) We will go for simple shell script:
```bash
#!/bin/sh

echo "Hello Curator"
```

#####2.) Archive our script into the archive package called *hello.zip*:
```bash
zip hello run # zip `run` into the `hello.zip` archive
```

> Move this folder into your project folder under folder commands/

#####3.) Create *Command* inside curator

```go
helloCommand := curator.NewCommand("commands/hello.zip")

server.AddCommand(helloCommand)
```

### Pipeline

Now, let's create pipeline that will use our command.

```go

```

### Middleware

> coming soon
