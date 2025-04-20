# @qubit-ltd/config

[![npm package](https://img.shields.io/npm/v/@qubit-ltd/config.svg)](https://npmjs.com/package/@qubit-ltd/config)
[![License](https://img.shields.io/badge/License-Apache-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![English Document](https://img.shields.io/badge/document-English-blue.svg)](README.md)
[![CircleCI](https://dl.circleci.com/status-badge/img/gh/Haixing-Hu/js-config/tree/master.svg?style=shield)](https://dl.circleci.com/status-badge/redirect/gh/Haixing-Hu/js-config/tree/master)
[![Coverage Status](https://coveralls.io/repos/github/Haixing-Hu/js-config/badge.svg?branch=master)](https://coveralls.io/github/Haixing-Hu/js-config?branch=master)

[@qubit-ltd/config] 是一个为应用程序提供全局配置对象的JavaScript库。

## <span id="installation">安装</span>

使用npm:

```bash
npm install @qubit-ltd/config
```

使用yarn:

```bash
yarn add @qubit-ltd/config
```

## <span id="usage">使用方法</span>

```javascript
import config from '@qubit-ltd/config';

// 设置配置
config.set('app.name', 'My App');
config.set('app.version', '1.0.0');
config.set('database.host', 'localhost');
config.set('database.port', 3306);

// 获取配置
const appName = config.get('app.name');         // 'My App'
const dbConfig = config.get('database');        // { host: 'localhost', port: 3306 }
const apiKey = config.get('api.key', 'default'); // 如果api.key不存在，返回'default'

// 检查配置是否存在
const hasAppName = config.has('app.name');      // true
const hasApiKey = config.has('api.key');        // false

// 删除配置
config.remove('app.name');
const appNameAfterRemove = config.has('app.name'); // false

// 合并配置
config.merge({
  app: {
    name: 'New App Name',
    theme: 'dark'
  }
});

// 合并环境变量
// 例如：使用Node.js的环境变量
config.mergeEnv(process.env);
// 或者在Vite项目中使用
// config.mergeEnv(import.meta.env, 'VITE_');

// 清空所有配置
config.clear();
```

## <span id="api">API</span>

### `config.has(keyPath)`

检查指定路径的配置是否存在。

- `keyPath`: 字符串，配置的路径，支持点号和数组索引，如`'app.name'`或`'database.users[0].name'`。
- 返回：布尔值，表示配置是否存在。

### `config.get(keyPath, defaultValue)`

获取指定路径的配置值。

- `keyPath`: 字符串，配置的路径，支持点号和数组索引。
- `defaultValue`: 可选，如果配置不存在时返回的默认值。
- 返回：配置值，如果不存在且未提供默认值则返回`undefined`。

### `config.set(keyPath, value)`

设置指定路径的配置值。

- `keyPath`: 字符串，配置的路径，支持点号和数组索引。
- `value`: 要设置的值。

### `config.remove(keyPath)`

删除指定路径的配置。

- `keyPath`: 字符串，配置的路径，支持点号和数组索引。

### `config.clear()`

清空所有配置。

### `config.merge(cfg)`

合并配置对象。

- `cfg`: 对象，要合并的配置对象。

### `config.mergeEnv(env, removePrefix)`

合并环境变量。

- `env`: 对象，包含环境变量的对象，通常是`process.env`或`import.meta.env`。
- `removePrefix`: 可选，字符串，要从环境变量名中移除的前缀。

## <span id="contributing">贡献</span>

如果您发现任何问题或有改进建议，请随时在[GitHub仓库]开issue或提交pull request。

## <span id="license">许可证</span>

[@qubit-ltd/config]在Apache 2.0许可证下分发。
有关更多详细信息，请参见[LICENSE](LICENSE)文件。

[@qubit-ltd/config]: https://npmjs.com/package/@qubit-ltd/config
[GitHub仓库]: https://github.com/Haixing-Hu/js-config 