---
title: Overview
category: Basic
order: 1
---

Before we start you need to install:
1. golang
2. Get these *gas* packages:
    * `go get github.com/gascore/gas`
    * `go get github.com/gascore/gas-web`
    * `go get github.com/gascore/gas-router`
    * `go get github.com/gascore/gas-store`
3. Install gopherjs `go get -u github.com/gopherjs/gopherjs`
4. Get api wrapper for gopherjs and wasm `go get github.com/gopherjs/gopherwasm`
5. Get dom bindings library `go get github.com/noartem/dom`
6. Install wasm-go (tool for easy wasm running) `go get -u github.com/swissChili/go-wasm`
7. For windows: Install mingw
8. Install gasx `go get -u github.com/gascore/gasx`


## Your first app

gasx provides command generating new projects. 
Run this command for create new project named foo: `gasx new full foo`. 
More about [new command](https://gascore.github.io/ecosystem/cli/#new-command).

> If you're developing not in your $GOPATH you need to fix imports

And run `run.sh` script: `sh run.sh gojs`.

Open [localhost:8080](http://localhost:8080).