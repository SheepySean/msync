# msync

[![Build Status](https://travis-ci.org/philcockfield/msync.svg?branch=master)](https://travis-ci.org/philcockfield/msync)

Manages building and syncing multiple node modules in a flexibly defined workspace.



## Install

    npm install -g msync



## Usage
Create a `sync.yaml` file to define the modules within your workspace.

```yaml
modules:
  - ./sample/*/package.json
  - ./sample/libs/*/package.json
```

Run the command line using `ms` within your workspace folder to list, sync or build the modules:

![Image](https://cloud.githubusercontent.com/assets/185555/25547887/d81a8f00-2cbd-11e7-98f7-730138032c3f.png)

Use the `--help` (`-h`) flag to see the options for each command, eg:

    ms sync --help

# Ignore
You can ignore file `paths` and module `names` by declaring an `ignore` block in the `sync.yaml` definition:


```yaml
ignore:
  paths:
    - ./sample/**/ignore-folder
  names:
    - 'module-4'

```




# API
All command-line options can be programatically invoked:

```js
import { ls, sync } from 'msync';
```

### ls (list)
List modules in dependency order.

```js
await ls();
await ls({ deps: 'local' });
await ls({ deps: 'all' });
```

### sync
Syncs each module's dependency tree locally.

```js
await sync();
```



## Next Steps

- `sync:watch`
- `build` (Typescript)
- `build:watch`
