# TypeScript SDK Installation

## Prerequisites

To follow this tutorial, ensure you have Node version 20 or later and npm version 8 or higher installed in your environment. You can download the latest LTS (Long Term Support) version from the [Node.js official website](https://nodejs.org/).

If you need to upgrade Node to version 20 or higher, we recommend using nvm (Node Version Manager). To upgrade npm to the latest version, use the following command:

```sh
npm install -g nvm
```

## Create a Node Project
First, create a folder named `kor-ts-example`:

```sh
mkdir kor-ts-example
```

Navigate into the folder and run `npm init` to initialize the project:

```sh
cd kor-ts-example/
npm init
```

You can accept all default values by pressing the enter key when prompted for package name, version, description, etc. After running the command, you will see a file named `package.json` in the directory.

## Install the Dependencies
While in the `kor-ts-example` folder, install the Kor Protocol SDK node package,

You can use any of the following package managers to install the dependencies:

```sh 
npm install --save @kor-protocol/core-sdk 
```
or
```sh
pnpm add @kor-protocol/core-sdk 
```
or
```sh
yarn add @kor-protocol/core-sdk 
```






