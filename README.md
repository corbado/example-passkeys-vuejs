# Passkey-First Authentication with Vue.js and Corbado

This is a sample implementation of the Corbado web component being integrated into a web application built with Vue.js.

Please see the [full blog post](https://www.corbado.com/blog/vuejs-passkeys) to understand the detailed steps needed to integrate passkeys into Vue.js apps.

## File structure

- `src/router/index.js`: routing for the Vue.js web app
- `src/views/HomeView.vue`: component for the sign up / login screen
- `src/views/ProfileView.vue`: component for the user profile information that is shown after successful authentication

## Setup

### Prerequisites

Please follow the steps in [Getting started](https://docs.corbado.com/overview/getting-started) to create and configure
a project in the [Corbado developer panel](https://app.corbado.com/signin#register).

You need to have [Node](https://nodejs.org/en/download) and `npm` installed to run it.

## Usage

Run

```bash
npm i
```

to install all dependencies.

Finally, you can run the project locally with

```bash
npm run dev
```
