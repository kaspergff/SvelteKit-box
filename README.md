# SvelteKite Truffle Box

This box comes with everything you need to start using smart contracts from a [SvelteKit](https://kit.svelte.dev/) app. 

## Goal
The goal of this project was to create a base for building an Ethereum dapp using [Truffle](https://trufflesuite.com/) with a SvelteKit frontend.

### Truffle Box
[Truffle Boxes](https://trufflesuite.com/boxes) are helpful boilerplates that allow you to focus on what makes your dapp unique. 

### SvelteKit
[SvelteKit](https://kit.svelte.dev/) is an application framework powered by Svelte. Used for building web applications of all sizes, with a beautiful development experience and flexible filesystem-based routing.

## Installation

First ensure you are in a new and empty directory.

## Installation

1. Install Truffle globally.
    ```bash
    npm install -g truffle
    ```

2. Download the box. This also takes care of installing the necessary dependencies.
    ```bash
    truffle unbox kaspergff/SvelteKit-box
    ```

4. Compile and migrate the smart contracts..
    ```bash
    truffle compile
    truffle migrate
    ```

5. Run the next.js server for the front-end. Smart contract changes must be manually recompiled and migrated.
    ```bash
    // Change directory to the front-end folder
    cd client
    // Serves the front-end on http://localhost:3000
    npm run dev
    ```

6. Truffle can run tests written in Solidity or JavaScript against your smart contracts.
    ```bash
    truffle test
    ```

7. To build the application for production, use the build script. A production build will be in the client/build folder.
    ```bash
    // ensure you are inside the client directory when running this
    npm run build
    ```

