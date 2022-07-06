# base16-builder (node.js) <img alt="Base16" src="./base16.png" xwidth="300" align="right" style="padding-top:0.6rem;">

[![latest version](https://badgen.net/npm/v/base16-builder-node?label=latest)](https://www.npmjs.com/package/base16-builder-node)
[![license](https://badgen.net/badge/license/MIT/cyan)](https://github.com/joshgoebel/base16-builder-node/blob/main/LICENSE)
[![open issues](https://badgen.net/github/open-issues/joshgoebel/base16-builder-node)](https://github.com/base16-project/base16-builder-node/issues)
[![vulnerabilities](https://badgen.net/snyk/base16-project/base16-builder-node)](https://snyk.io/test/github/base16-project/base16-builder-node?targetFile=package.json)
<!-- ![build and CI status](https://badgen.net/github/checks/joshgoebel/base16-builder-node/main?label=build) -->
<!-- [![code quality](https://badgen.net/lgtm/grade/g/joshgoebel/base16-builder-node/js?label=code+quality)](https://lgtm.com/projects/g/joshgoebel/base16-builder-node/?mode=list) -->


A builder for schemes and templates based on of the [base16 specification](https://github.com/base16-project/base16) by [Chris Kempson](https://github.com/chriskempson).

**Features**

- Supports both `base16` and `base24` schemes/templates
   - Base16 builder v0.10.1 spec
   - Base16 v0.2 styling spec
   - Base24 ([5625d94](https://github.com/Base24/base24/commit/5625d94c0720c38cc7a0703766d61131a6bda5a6)) styling spec
- Builds all installed templates/schemes in one quick pass


**What is Base16?**

[Base16](https://github.com/base16-project/base16) is an architecture for crafting color schemes and easily translating them to your favorite apps - based on carefully chosen syntax highlighting using a base of sixteen colors.


## Install

```
npm install -g base16-builder-node
```

This package provides a `base16` console command.  Invoke it from any directory you want to build your themes, templates, and schemes in.


## Basic Usage

Your working directory will need the following substructure:

- `base16/schemes`
- `base16/templates`

If your running directly from a GitHub checkout you'll find `base16/schemes` already populated with a submodule of all schemes.  If you've installed via `npm` or `yarn` you'll need to setup a working directory yourself.


```sh
$ cd working_dir
$ mkdir -p base16/templates && cd base16
$ git clone https://github.com/base16-project/base16-schemes.git schemes
$ cd templates
$ git clone [your template of choice]
$ git clone [another template of choice]
$ base16 build
```

Builds all templates found in `base16/templates` using all scheme files from `base16/schemes`.


### Build Assets

The theme files will be generated inside every template directory in the
subdirectory specified by that template's configuration.

For example: `textmate`. The built files would be found at:

 `./templates/textmate/Themes`,


### If you are a template maintainer

The easiest thing is to simply maintain your template repository inside your base16-build working folder (or symlink it).

You could facilitate this easily (from inside your template dir) with a tiny build script, etc:

```shell
#!/bin/bash
cd ../../..
base16 build
```
