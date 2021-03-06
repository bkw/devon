# devon
Lightweight Development HTTP Server written in nodejs

## Usage
If you installed devon global, you only have to switch to your project directory and type in your terminal `devon`, hit enter and have fun.

## Arguments

Set the argument followed by an equal sign and the value, like `--port=9090`.

Argument       |Content        |Description               |Default
---------------|---------------|--------------------------|-------
-h, --help     |none           |shows a short help message|
-p, --port     |number         |port number               |8080
-s, --silent   |none or boolean|prevents the log messages |false

## Document location
Some note to where devon loads files: In the directory where you start, devon will take this as document location and all paths in the URL are relative to that.

## Directory Indexing
If devon looks on a directory, you will get a simple HTML list from files and directories in there.

## Proxy
Devon has a simple reverse proxy handling. Add a `.proxy`-named file to the document location with content like this (example):

```
{
  "^\/couchdb(.*)$": {
    "host": "127.0.0.1",
    "port": 5984
  }
}
```

The top-level keys are regular expressions. And the objects to them are the target for the proxy. The content of the first braces is the new request url for the target. So in this example (if you come from `localhost:8080`) you will get `http://localhost:8080/couchdb/foodb` to `http://127.0.0.1:5984/foodb`. 

## Installation
Just install devon via npm (don't forget the global flag):

```
npm install devon -g
```

## Warning
Please do not(!) use this server in production mode. It has no security features and it will be easy to get secret data from your server. It's really only for local (max. office or something like that) development.

## License
(The MIT License)

Copyright (c) 2009-2013 André Kussmann <zoddy@zoddy.de>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

