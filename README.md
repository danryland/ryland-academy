# Ryland Academy (ryland-academy)

Open source school

## Install the dependencies

```bash
yarn
# or
npm install
```

### Start the app in development mode (hot-code reloading, error reporting, etc.)

```bash
quasar dev
```

### Lint the files

```bash
yarn lint
# or
npm run lint
```

### Format the files

```bash
yarn format
# or
npm run format
```

### Icons

#### Favicon

```bash
icongenie generate -i src/assets/img/icon-ryland-academy-ios.png --quality 12
icongenie generate -i src/assets/img/icon-ryland-academy-android.png --quality 12
```

#### Splashscreen

```bash
icongenie generate -i src/assets/img/icon-ryland-academy-android-splash.png --quality 12 --splashscreen-color 201940 --splashscreen-icon-ratio 20
```

### Build the app for production

```bash
quasar build
```

### Customize the configuration

See [Configuring quasar.config.js](https://v2.quasar.dev/quasar-cli-vite/quasar-config-js).
