# Vue Firebase Composition Api

Powered by Vite

Also checkout a fork [Firebase Composition for Nuxt](https://github.com/razbakov/nuxt-firebase-composition)

## Usage

```html
<template>
  <div>UID: {{ uid }}</div>
  <pre>{{ accounts }}</pre>
  <button @click="signInWithGoogle">Sign In with Google</button>
  <button @click="createAccount({ name: 'Join' })">Add</button>
</template>

<script>
  import { initFirebase, useAuth, useCollection, useDoc } from 'vca-firebase'
  import firebaseConfig from './firebase.config.js'

  export default {
    setup() {
      initFirebase(firebase, firebaseConfig)

      const { uid, signInWithGoogle } = useAuth()
      const { docs: accounts } = useCollection('accounts')
      const { create: createAccount } = useDoc('accounts')

      return {
        signInWithGoogle,
        uid,
        accounts,
        createAccount,
      }
    },
  }
</script>
```

## Setup

```bash
yarn create vite-app test-vca-firebase
cd test-vca-firebase
yarn add firebase
yarn add vca-firebase
```

Create `firebase.config.js`:

- Generate `config` object in Firebase Console.
- Enable/disable plugins, i.e. `analytics`.

```js
export default {
  config: {
    apiKey,
    authDomain,
    databaseURL,
    projectId,
    storageBucket,
    messagingSenderId,
    appId,
    measurementId,
  },
  analytics: false,
}
```

## Development

Setup project and run:

```bash
yarn dev
```

See the power of Vite! Project is available in less than 1 second!
