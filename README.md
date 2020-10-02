# QUICK
QUICK is an interactive software environment for space mission design.

## Overview
### History
* In 1973, I wrote Universe 1.0, my first multiplayer game, it ran on the Wang Statistical Computer at LSU and distracted the staff of the genetics lab. It was a three-body gravitational calculation of spaceflight.
* In 1985, I published Cluster Analysis in Comal Today and sold over 600 copies. It allowed nodal analysis and consolidation on any number of dimensions (yes, even 11 dimensions).
* Circa 1986 I published Universe 2.0 in Comal Today.
* In 1990, Clay Ratliff and Dr. Mark Hood Ph.D. assisted me with Universe 3.0 which was a multiplayer space simulation on Comal that ran on the Atari 5600 and the Amiga, Ken Williams arranged for me to write the first true color video driver for IBM so that it could be adapted to the IBM PC and my SGML server was sold to AT&T for later deployment by AOL. I was missing Daniel and was offered my dream job in Louisiana and left it behind, Atari and Commodore collapsed, my program was never published on the IBM.
* In 1991, I was serving part-time as an advisor to the board of directors of Research Astronautics and Mining Foundation which was developing technology to mine minerals in the asteroid belt. I wrote a Comal program called QUICK to do project planning. It was derived from Universe 2.0 which included the Cluster Analysis Package and worked quite well.
* In 1992, after showing my QUICK program to JPL during the Gateway training, they evaluated the program and found it useful although not entirely accurate. I presented it at the Aerospace Design Conference and it was published by the American Institute of Aeronautics and Astronautics, Inc.

### Description
QUICK is an interactive software environment for space mission design. Written as a stand-alone program, which was available on 14 different machine architectures, QUICK provides a programmable Fortran-like calculator interface to a wide range of both built-in and user-defined functions. QUICK also provides direct access to the operating systems on each of these machines.

My program would collapse the gravitational vectors into consolidated nodes that resulted in very rapid processing. Note that due to variations in lunar density causing perturbations in lunar orbits, NASA must use a multiple-vector model for the moon. My program was not so accurate that you could pilot a space ship, but it was close enough to plan a mission on a real-time basis and then submit the mission to the mainframe for final precise analysis and adjustment.

The original implementation in Comal used relative files with user defined fixed length fortran fields and import required Comal functions as separate packages.

### Project intent.
What I would like to do, is to recreate the QUICK program using Go 2.0 and deploy it as a tool used by gamers playing Universe 4.0 and hopefully present it at the 2022 Aerospace Design Conference in memorial to our fallen astronauts.

## Implementation
### Package Quick
Package Quick is an interactive environment for space mission design using dependency injection for IO.
### Commands
* Batch
* ConIo
* Gui
    * MacOs
    * Win
    * Linux
* Web
* QuickRpc
### Imports
* DavskIo
* ClusterAnalysis
* DavskUniverse

## Instructions for team members
Detailed instructions and install scripts will be provided.

# Under Construction. Needs revision.
## Installation
Install prerequisites first.

### Win10 Notes
#### Developers Mode.
Developer mode must be enable for mklink to create symbolic links.
* Press Start, search for develpers, setup enable Developers mode.

#### Enable Long Filenames on Git if using Windows10
``` bash
   git config --global core.longpaths true
```

### Clone repository

**Edit instructions for users cloning your repository to do maintenance.**

In your `Documents/GitHub/Davsk/' folder, execute each line in Git Bash.

``` bash
    git clone git@github.com:Davsk/Project-Online.git
    cd Project-Online
    scripts/init-subs.sh
```

## Company specific layout decisions

AppEngine Services are defined in their respective directorories in /cmd

Hugo sites are defined in their respective directories in /website

# Standard Go Project Layout

Translations:

* [한국어 문서](README_ko.md)
* [中文文档](README_zh.md)

## Overview

This is a basic layout for Go application projects. It's not an official standard defined by the core Go dev team; however, it is a set of common historical and emerging project layout patterns in the Go ecosystem. Some of these patterns are more popular than others. It also has a number of small enhancements along with several supporting directories common to any large enough real world application.

If you are trying to learn Go or if you are building a PoC or a toy project for yourself this project layout is an overkill. Start with something really simple (a single `main.go` file is more than enough). As your project grows keep in mind that it'll be important to make sure your code is well structured otherwise you'll end up with a messy code with lots of hidden dependencies and global state. When you have more people working on the project you'll need even more structure. That's when it's important to introduce a common way to manage packages/libraries. When you have an open source project or when you know other projects import the code from your project repository that's when it's important to have private (aka `internal`) packages and code. Clone the repository, keep what you need and delete everything else! Just because it's there it doesn't mean you have to use it all. None of these patterns are used in every single project. Even the `vendor` pattern is not universal.

With Go 1.14 [`Go Modules`](https://github.com/golang/go/wiki/Modules) are finally ready for production. Use [`Go Modules`](https://blog.golang.org/using-go-modules) unless you have a specific reason not to use them and if you do then you don’t need to worry about $GOPATH and where you put your project. The basic `go.mod` file in the repo assumes your project is hosted on GitHub, but it's not a requirement. The module path can be anything though the first module path component should have a dot in its name (the current version of Go doesn't enforce it anymore, but if you are using slightly older versions don't be surprised if your builds fail without it). See Issues [`37554`](https://github.com/golang/go/issues/37554) and [`32819`](https://github.com/golang/go/issues/32819) if you want to know more about it.  

This project layout is intentionally generic and it doesn't try to impose a specific Go package structure.

This is a community effort. Open an issue if you see a new pattern or if you think one of the existing patterns needs to be updated.

If you need help with naming, formatting and style start by running [`gofmt`](https://golang.org/cmd/gofmt/) and [`golint`](https://github.com/golang/lint). Also make sure to read these Go code style guidelines and recommendations:
* https://talks.golang.org/2014/names.slide
* https://golang.org/doc/effective_go.html#names
* https://blog.golang.org/package-names
* https://github.com/golang/go/wiki/CodeReviewComments
* [Style guideline for Go packages](https://rakyll.org/style-packages) (rakyll/JBD)

See [`Go Project Layout`](https://medium.com/golang-learn/go-project-layout-e5213cdcfaa2) for additional background information.

More about naming and organizing packages as well as other code structure recommendations:
* [GopherCon EU 2018: Peter Bourgon - Best Practices for Industrial Programming](https://www.youtube.com/watch?v=PTE4VJIdHPg)
* [GopherCon Russia 2018: Ashley McNamara + Brian Ketelsen - Go best practices.](https://www.youtube.com/watch?v=MzTcsI6tn-0)
* [GopherCon 2017: Edward Muller - Go Anti-Patterns](https://www.youtube.com/watch?v=ltqV6pDKZD8)
* [GopherCon 2018: Kat Zien - How Do You Structure Your Go Apps](https://www.youtube.com/watch?v=oL6JBUk6tj0)

A Chinese Post about Package-Oriented-Design guidelines and Architecture layer
* [面向包的设计和架构分层](https://github.com/danceyoung/paper-code/blob/master/package-oriented-design/packageorienteddesign.md)

## Go Directories

### `/cmd`

Main applications for this project.

The directory name for each application should match the name of the executable you want to have (e.g., `/cmd/myapp`).

Don't put a lot of code in the application directory. If you think the code can be imported and used in other projects, then it should live in the `/pkg` directory. If the code is not reusable or if you don't want others to reuse it, put that code in the `/internal` directory. You'll be surprised what others will do, so be explicit about your intentions!

It's common to have a small `main` function that imports and invokes the code from the `/internal` and `/pkg` directories and nothing else.

See the [`/cmd`](cmd/README.md) directory for examples.

### `/internal`

Private application and library code. This is the code you don't want others importing in their applications or libraries. Note that this layout pattern is enforced by the Go compiler itself. See the Go 1.4 [`release notes`](https://golang.org/doc/go1.4#internalpackages) for more details. Note that you are not limited to the top level `internal` directory. You can have more than one `internal` directory at any level of your project tree.

You can optionally add a bit of extra structure to your internal packages to separate your shared and non-shared internal code. It's not required (especially for smaller projects), but it's nice to have visual clues showing the intended package use. Your actual application code can go in the `/internal/app` directory (e.g., `/internal/app/myapp`) and the code shared by those apps in the `/internal/pkg` directory (e.g., `/internal/pkg/myprivlib`).

### `/pkg`

Library code that's ok to use by external applications (e.g., `/pkg/mypubliclib`). Other projects will import these libraries expecting them to work, so think twice before you put something here :-) Note that the `internal` directory is a better way to ensure your private packages are not importable because it's enforced by Go. The `/pkg` directory is still a good way to explicitly communicate that the code in that directory is safe for use by others. The [`I'll take pkg over internal`](https://travisjeffery.com/b/2019/11/i-ll-take-pkg-over-internal/) blog post by Travis Jeffery provides a good overview of the `pkg` and `internal` directories and when it might make sense to use them.

It's also a way to group Go code in one place when your root directory contains lots of non-Go components and directories making it easier to run various Go tools (as mentioned in these talks: [`Best Practices for Industrial Programming`](https://www.youtube.com/watch?v=PTE4VJIdHPg) from GopherCon EU 2018, [GopherCon 2018: Kat Zien - How Do You Structure Your Go Apps](https://www.youtube.com/watch?v=oL6JBUk6tj0) and [GoLab 2018 - Massimiliano Pippi - Project layout patterns in Go](https://www.youtube.com/watch?v=3gQa1LWwuzk)).

See the [`/pkg`](pkg/README.md) directory if you want to see which popular Go repos use this project layout pattern. This is a common layout pattern, but it's not universally accepted and some in the Go community don't recommend it. 

It's ok not to use it if your app project is really small and where an extra level of nesting doesn't add much value (unless you really want to :-)). Think about it when it's getting big enough and your root directory gets pretty busy (especially if you have a lot of non-Go app components).

### `/vendor`

Application dependencies (managed manually or by your favorite dependency management tool like the new built-in [`Go Modules`](https://github.com/golang/go/wiki/Modules) feature). The `go mod vendor` command will create the `/vendor` directory for you. Note that you might need to add the `-mod=vendor` flag to your `go build` command if you are not using Go 1.14 where it's on by default.

Don't commit your application dependencies if you are building a library.

Note that since [`1.13`](https://golang.org/doc/go1.13#modules) Go also enabled the module proxy feature (using [`https://proxy.golang.org`](https://proxy.golang.org) as their module proxy server by default). Read more about it [`here`](https://blog.golang.org/module-mirror-launch) to see if it fits all of your requirements and constraints. If it does, then you won't need the `vendor` directory at all.

## Service Application Directories

### `/api`

OpenAPI/Swagger specs, JSON schema files, protocol definition files.

See the [`/api`](api/README.md) directory for examples.

## Web Application Directories

### `/web`

Web application specific components: static web assets, server side templates and SPAs.

## Common Application Directories

### `/configs`

Configuration file templates or default configs.

Put your `confd` or `consul-template` template files here.

### `/init`

System init (systemd, upstart, sysv) and process manager/supervisor (runit, supervisord) configs.

### `/scripts`

Scripts to perform various build, install, analysis, etc operations.

These scripts keep the root level Makefile small and simple (e.g., [`https://github.com/hashicorp/terraform/blob/master/Makefile`](https://github.com/hashicorp/terraform/blob/master/Makefile)).

See the [`/scripts`](scripts/README.md) directory for examples.

### `/build`

Packaging and Continuous Integration.

Put your cloud (AMI), container (Docker), OS (deb, rpm, pkg) package configurations and scripts in the `/build/package` directory.

Put your CI (travis, circle, drone) configurations and scripts in the `/build/ci` directory. Note that some of the CI tools (e.g., Travis CI) are very picky about the location of their config files. Try putting the config files in the `/build/ci` directory linking them to the location where the CI tools expect them (when possible).

### `/deployments`

IaaS, PaaS, system and container orchestration deployment configurations and templates (docker-compose, kubernetes/helm, mesos, terraform, bosh). Note that in some repos (especially apps deployed with kubernetes) this directory is called `/deploy`.

### `/test`

Additional external test apps and test data. Feel free to structure the `/test` directory anyway you want. For bigger projects it makes sense to have a data subdirectory. For example, you can have `/test/data` or `/test/testdata` if you need Go to ignore what's in that directory. Note that Go will also ignore directories or files that begin with "." or "_", so you have more flexibility in terms of how you name your test data directory.

See the [`/test`](test/README.md) directory for examples.

## Other Directories

### `/docs`

Design and user documents (in addition to your godoc generated documentation).

See the [`/docs`](docs/README.md) directory for examples.

### `/tools`

Supporting tools for this project. Note that these tools can import code from the `/pkg` and `/internal` directories.

See the [`/tools`](tools/README.md) directory for examples.

### `/examples`

Examples for your applications and/or public libraries.

See the [`/examples`](examples/README.md) directory for examples.

### `/third_party`

External helper tools, forked code and other 3rd party utilities (e.g., Swagger UI).

### `/githooks`

Git hooks.

### `/assets`

Other assets to go along with your repository (images, logos, etc).

### `/website`

This is the place to put your project's website data if you are not using GitHub pages.

See the [`/website`](website/README.md) directory for examples.

## Directories You Shouldn't Have

### `/src`

Some Go projects do have a `src` folder, but it usually happens when the devs came from the Java world where it's a common pattern. If you can help yourself try not to adopt this Java pattern. You really don't want your Go code or Go projects to look like Java :-)

Don't confuse the project level `/src` directory with the `/src` directory Go uses for its workspaces as described in [`How to Write Go Code`](https://golang.org/doc/code.html). The `$GOPATH` environment variable points to your (current) workspace (by default it points to `$HOME/go` on non-windows systems). This workspace includes the top level `/pkg`, `/bin` and `/src` directories. Your actual project ends up being a sub-directory under `/src`, so if you have the `/src` directory in your project the project path will look like this: `/some/path/to/workspace/src/your_project/src/your_code.go`. Note that with Go 1.11 it's possible to have your project outside of your `GOPATH`, but it still doesn't mean it's a good idea to use this layout pattern.


## Badges

* [Go Report Card](https://goreportcard.com/) - It will scan your code with `gofmt`, `go vet`, `gocyclo`, `golint`, `ineffassign`, `license` and `misspell`. Replace `github.com/golang-standards/project-layout` with your project reference.

* ~~[GoDoc](http://godoc.org) - It will provide online version of your GoDoc generated documentation. Change the link to point to your project.~~

* [Pkg.go.dev](https://pkg.go.dev) - Pkg.go.dev is a new destination for Go discovery & docs. You can create a badge using the [badge generation tool](https://pkg.go.dev/badge).

* Release - It will show the latest release number for your project. Change the github link to point to your project.

[![Go Report Card](https://goreportcard.com/badge/github.com/davsk/quick?style=flat-square)](https://goreportcard.com/report/github.com/davsk/quick)
[![Go Doc](https://img.shields.io/badge/godoc-reference-blue.svg?style=flat-square)](http://godoc.org/github.com/davsk/quick)
[![PkgGoDev](https://pkg.go.dev/badge/github.com/davsk/quick)](https://pkg.go.dev/github.com/davsk/quick)
[![Release](https://img.shields.io/github/release/golang-standards/project-layout.svg?style=flat-square)](https://github.com/golang-standards/project-layout/releases/latest)

## Notes

A more opinionated project template with sample/reusable configs, scripts and code is a WIP.

