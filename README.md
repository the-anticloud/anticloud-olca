# OLCA

> Anticloud offline package — upstream: GreenDelta/olca-app @ `master`.

## What This Project Does

Source code of openLCA

**Topics:** eclipse-rcp, java, openlca

## Upstream README

# openLCA

This repository contains the source code of [openLCA](http://openlca.org).
openLCA is a Java application that runs on the Eclipse Rich Client Platform
(Eclipse RCP). The source code is structured in the following sub-projects:

* [olca-app](./olca-app): contains the source code of the openLCA RCP
  application.
* [olca-app-build](./olca-app-build): contains the build scripts creating the
  distribution packages for Windows, Linux, and macOS.
* [olca-app-html](./olca-app-html): contains the source code for the HTML views
  in openLCA (like the start page or the report views).
* [olca-refdata](./olca-refdata): contains the build scripts fro the reference
  databases (with units, flows, locatios, etc.) that are packaged with openLCA.

See also the README files of these sub-projects for more information.


## Running from source

In order to compile and run openLCA from source, you need to have the following
tools installed:

* a [Java Development Kit >= v25](https://adoptium.net)
* [Maven](http://maven.apache.org/)
* the [Eclipse package for RCP
  developers](https://www.eclipse.org/downloads/packages/)
* [Node.js](https://nodejs.org/)
* (Python and [uv](https://github.com/astral-sh/uv) in case you want to build
  the distribution packages )

When you have these tools installed, you can build and run the application with
the following steps:

#### Install the openLCA core modules

The core modules contain the application logic that is independent from the user
interface and can be also used in other applications. These modules are plain
Maven projects and can be installed via `mvn install`. See the
[olca-modules](https://github.com/GreenDelta/olca-modules) repository for more
information. Note that we also distribute the latest stable version of the
modules on the Maven Central repository. However, if you want to test the
current openLCA development branch, you probably need to install them first.
There is also a script for installing them when you put them next to the
`olca-app` folder:

```bash
./update_modules.sh
# or on Windows
./update_modules.bat
```

#### Building the HTML pages

To build the HTML pages of the user interface, navigate to the
[olca-app-html](./olca-app-html) and run the following commands:

```bash
cd olca-app/olca-app-html
# install the dependencies
npm install
# build and package the HTML pages for the app
npm run build
```

#### Prepare the Eclipse workspace

Download the current Eclipse package for RCP and RAP developers, start it and
create a workspace directory. Import the projects into Eclipse via `Import >
General > Existing Projects into Workspace` (select the `olca-app` directory).
You should now see the `olca-app`, `olca-app-build`, projects in your Eclipse
workspace.

#### Loading the target platform

The file `platform.target` in the `olca-app` project contains the definition of
the [target platform](https://help.eclipse.org/oxygen/index.jsp?topic=%2Forg.eclipse.pde.doc.user%2Fconcepts%2Ftarget.htm)
of 

## License

Upstream terms preserved in `THIRD_PARTY_LICENSES/`. Overlay licensed under Anticommons 0.1.0.

## Verification

Recompute the SHA3-256 of `BENCH.json` and compare to this package’s register. Any drift = invalid package.
