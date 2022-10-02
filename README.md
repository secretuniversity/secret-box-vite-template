# Secret Box Template

[![Gitpod ready-to-code](https://img.shields.io/badge/Gitpod-ready--to--code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/secretuniversity/secret-box-vite-template)

The Secret Box Template is a Gitpod-enabled quickstart for dapp development on [Secret Network](https://scrt.network).
It consists of a frontend (Vue + Vite + Typescript) and a secret contract (Rust + Secret CosmWasm), based on the [secret counter template](https://github.com/secretuniversity/secret-template-cw1).

## What is a Secret Box?

Secret Boxes are quickstarts or blueprints that contain everything you need to start developing on Secret Network. 
They are intended to be run in a developer sandbox so you don't have to worry about installing various tooling, 
frameworks, etc.

Launching via Gitpod will create an environment that automatically starts `localsecret` (dockerized Secret Network),
and exposes the ports for application development.

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/secretuniversity/secret-box-vite-template)

When launched the following automated tasks are kicked off:

- launch an instance of `localsecret`
- build and deploy the secret contract to `localsecret`
- instantiate the secret contract
- install dependencies and launch the frontend using Vite

![Secret Box Template Dapp](/docs/secret-box-template.png)

## Creating a Secret Box

Creating a Secret Box involves one part coding and one part technical writing.

Each Secret Box has an accompanying tutorial hosted on the Secret University website. The tutorial is written in Markdown and can be found in the [tutorial](/tutorial/) directory of this repo.

### Setup Your Local Developer Environment

This [Setting Up Your Environment](https://docs.scrt.network/secret-network-documentation/development/getting-started/setting-up-your-environment) guide will help you get going on your journey developing a Secret Box.

In addition to the Secret Contract setup, you will also need to install `Nodejs` and `yarn` for the integration 
tests and frontend app.

#### Install Nodejs

Use the installer for your environment [here](https://nodejs.dev/en/download).

#### Install Yarn

You can find information on installing `yarn`, getting started, advanced topics and more [here](https://yarnpkg.com).

### Writing Your Guide

Secret Box tutorials are written using Markdown and require specific pieces of front matter to display properly 
on the website.

#### Secret Box Front Matter

Each post should have a front matter section at the top of the markdown file that looks something like this.

```
title: Part 1: Hello World
description: The first thing you’ll need to do to start developing secret contracts in your local environment is install and launch a Secret Network blockchain.
index: 1
lottie: https://assets5.lottiefiles.com/private_files/lf30_0vbtxqrd.json
box: {
    title: Hello World,
    description: "Use this tutorial to learn about launching a local Secret blockchain, modifying the secret contract, runing unit tests, and viewing debug messages in the node log.",
    prelude: A fun way for developers to quickly learn about working with secret contracts.,
    difficulty: Beginner,
    image: /illustrations/hello-world.svg,
    gitpod: https://gitpod.io/#https://github.com/secretuniversity/secret-box-hello-world
}
```

##### Post-Specific Front Matter

* `title` Title for the specific tutorial (**required**)
* `description`: Description for the specific tutorial (**required**)
* `index`: A Secret Box can be split up between many different posts. This index indicates the ordering for each post and **begins at index 1** (**required**)
* `lottie`: Refers to a lottie animation url (*optional*)

##### Box-Specific Front Matter

Each tutorial post must also include information about the Secret Box it pertains to. Noted by the `box` object of the example. Currently all `box` variables are **required,** but they can be copy and pasted for posts pertaining to the same box.

* `title` Title of the Secret Box
* `description` Description of the Secret Box
* `prelude` A short one-sentence description of the Secret Box
* `difficulty` One of three options: Beginner, Intermediate, Advanced
* `image` An image for the Secret Box
* `gitpod` A gitpod deployment URL

#### Speciality Markdown Components

Because the Secret Boxes website is built using Astro, our tutorials can utilized reactive JavaScript components within our markdown files. For example,

```
setup: |
  import MarkdownImage from '@components/MarkdownImage.svelte'
title: Hello World Design
description: This is a UML diagram illustrating the secret box components and how they interact.
...
```

If we include a setup variable in our Frontmatter we are allowed to import framework specific components into our Markdown and use them like so:

```html
<MarkdownImage
  client:visible
  alt="UML diagram image of the Hello World secret box"
  image="/tutorial/illustrations/hello-world-design.jpg"></MarkdownImage>
```

This `MarkdownImage` component allows us to create a special `img` component which when clicked on the website will display a modal with the option for the user to download the image.

More details on the available components built for Secret Boxes tutorials will be listed here.

### 🚀 Project Structure

```
/
.
├── app
│   ├── public
│   └── src
│       ├── assets
│       └── components
├── docs
├── examples
├── schema
├── src
├── target
│   ├── debug
│   ├── release
│   └── wasm32-unknown-unknown
│       └── release
├── tests
└── tutorial
    ├── content
    └── illustrations
```
### 🧞 Commands & Usage

#### Secret Contract

After cloning the repo, the following commands are run from the root of the project, from a terminal and apply
to the secret contracts:

| Command                | Action                                                    |
|:---------------------  |:--------------------------------------------------------  |
| `make build`           | Compiles the secret contract                              |
| `make schema`          | Generates the JSON schema for messages and state files    |
| `make test`            | Runs the secret contract unit tests                       |
| `make localsecret`     | Launches the dockerized `localsecret` developer instance  |
| `make deploy`          | Stores the compiled/optimized contract on `localsecret`   |

### Integration Tests

The integration tests are located under the `tests` directory and uses `secret.js` to interact with the
deployed secret contract. These are great examples of interacting with the Secret Network and can be used
to bootstrap frontend development.

```
npx ts-node integration.ts
```

#### Frontend App

These commands apply to the frontend of the Secret Box and are run from the `app` directory:


| Command           | Action                                       |
|:----------------  |:-------------------------------------------- |
| `yarn`         | Installs dependencies                        |
| `yarn dev`     | Starts local Vite dev server at `http://localhost:5173`  |
| `yarn build`   | Build your production site to `./dist/`      |
| `yarn preview` | Preview your build locally, before deploying |


#### Connecting from outside Gitpod

To connect, prepend the port number with the gitpod url. e.g. if the workspace is at
`https://secretunive-secretboxvi-zyc1kppqbvk.ws-us69.gitpod.io` then you can connect to the LCD service at
`https://1317-secretunive-secretboxvi-zyc1kppqbvk.ws-us69.gitpod.io`.

## Resources
- [Secret Network docs](https://docs.scrt.network)
- [Secret IDE](https://www.digiline.io/)

## Contributors
- Laura Weindorf [Github](https://github.com/secetchaingirl)
- Alex (sinplea) [Github](https://github.com/sinplea)
- DDT5 [Github](https://github.com/DDT5)

## TODO
- [ ] add Gitpod yaml configuration
- [ ] add tutorial content to illustrate the format
- [ ] have DDT review integration tests
