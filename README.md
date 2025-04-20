# @qubit-ltd/config

[![npm package](https://img.shields.io/npm/v/@qubit-ltd/config.svg)](https://npmjs.com/package/@qubit-ltd/config)
[![License](https://img.shields.io/badge/License-Apache-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![中文文档](https://img.shields.io/badge/文档-中文版-blue.svg)](README.zh_CN.md)
[![CircleCI](https://dl.circleci.com/status-badge/img/gh/Haixing-Hu/js-config/tree/master.svg?style=shield)](https://dl.circleci.com/status-badge/redirect/gh/Haixing-Hu/js-config/tree/master)
[![Coverage Status](https://coveralls.io/repos/github/Haixing-Hu/js-config/badge.svg?branch=master)](https://coveralls.io/github/Haixing-Hu/js-config?branch=master)

[@qubit-ltd/config] is a JavaScript library providing a global configuration object for Apps.

## <span id="installation">Installation</span>

Using npm:

```bash
npm install @qubit-ltd/config
```

Using yarn:

```bash
yarn add @qubit-ltd/config
```

## <span id="usage">Usage</span>

```javascript
import config from '@qubit-ltd/config';

// Set configurations
config.set('app.name', 'My App');
config.set('app.version', '1.0.0');
config.set('database.host', 'localhost');
config.set('database.port', 3306);

// Get configurations
const appName = config.get('app.name');         // 'My App'
const dbConfig = config.get('database');        // { host: 'localhost', port: 3306 }
const apiKey = config.get('api.key', 'default'); // returns 'default' if api.key doesn't exist

// Check if configuration exists
const hasAppName = config.has('app.name');      // true
const hasApiKey = config.has('api.key');        // false

// Remove a configuration
config.remove('app.name');
const appNameAfterRemove = config.has('app.name'); // false

// Merge configurations
config.merge({
  app: {
    name: 'New App Name',
    theme: 'dark'
  }
});

// Merge environment variables
// For example, with Node.js environment variables
config.mergeEnv(process.env);
// Or with Vite
// config.mergeEnv(import.meta.env, 'VITE_');

// Clear all configurations
config.clear();
```

## <span id="api">API</span>

### `config.has(keyPath)`

Checks if a configuration exists at the specified path.

- `keyPath`: String, the path to the configuration, supports dot notation and array indices, e.g., `'app.name'` or `'database.users[0].name'`.
- Returns: Boolean, indicating whether the configuration exists.

### `config.get(keyPath, defaultValue)`

Gets the configuration value at the specified path.

- `keyPath`: String, the path to the configuration, supports dot notation and array indices.
- `defaultValue`: Optional, the default value to return if the configuration doesn't exist.
- Returns: The configuration value, or `undefined` if it doesn't exist and no default value is provided.

### `config.set(keyPath, value)`

Sets the configuration value at the specified path.

- `keyPath`: String, the path to the configuration, supports dot notation and array indices.
- `value`: The value to set.

### `config.remove(keyPath)`

Removes the configuration at the specified path.

- `keyPath`: String, the path to the configuration, supports dot notation and array indices.

### `config.clear()`

Clears all configurations.

### `config.merge(cfg)`

Merges a configuration object.

- `cfg`: Object, the configuration object to merge.

### `config.mergeEnv(env, removePrefix)`

Merges environment variables.

- `env`: Object containing environment variables, typically `process.env` or `import.meta.env`.
- `removePrefix`: Optional string, a prefix to remove from environment variable names.

## <span id="contributing">Contributing</span>

If you find any issues or have suggestions for improvements, please feel free
to open an issue or submit a pull request to the [GitHub repository].

## <span id="license">License</span>

[@qubit-ltd/config] is distributed under the Apache 2.0 license.
See the [LICENSE](LICENSE) file for more details.

[@qubit-ltd/config]: https://npmjs.com/package/@qubit-ltd/config
[GitHub repository]: https://github.com/Haixing-Hu/js-config
