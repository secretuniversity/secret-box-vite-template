# Secret Box Template

This is a template to build a Secret Box, which is a dapp template that consists of a frontend (Vue + Vite) and 
secret contract (Rust + Secret CosmWasm).

## What is a Secret Box?

Secret Boxes are quickstarts or blueprints that contain everything you need to start developing on Secret Network, 
packaged in the form of a "container" which when launched via Gitpod or another sandbox development environment 
performs the following automated tasks:

- launch an instance of `LocalSecret` (developer Secret Network)
- build and deploy the secret contract to `LocalSecret`
- instantiates the secret contract
- installs dependencies and launches the frontend using Vite

![Secret Box Template Dapp](/docs/secret-box-template.png)

## TODO

- [ ] add Gitpod yaml configuration
- [ ] resolve issue with `make build-mainnet-reproducible` where it's referencing `secret-box-template-cw1`
- [ ] add tutorial content to illustrate the format
- [ ] have DDT review integration tests
