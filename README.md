# nodeasy

nodeasy is an interactive CLI for creating a starter Node.js project. Run `nodeasy init` in a new directory, answer prompts about the module system and packages you want, and it will write the starter files and install your selections.

## Requirements

- Node.js 22 (version 22.13 or later) or 24, and npm
- Access to the npm registry if you select packages to install

## Get started

Install the CLI dependencies from this repository:

```bash
cd nodeasy
npm ci
```

Then create an **empty** directory for your new project and run the CLI from there:

```bash
mkdir ../my-node-project
cd ../my-node-project
node ../nodeasy/bin/index.js init
```

You can also run `npm link` inside `nodeasy/` to make the `nodeasy` command available locally, then run `nodeasy init` from the new project directory. Use `nodeasy --help` to see the available command.

The CLI writes to the **current working directory** and can replace files with the same names. It prompts for a project name, CommonJS or ES modules, JavaScript or TypeScript dependencies, and optional framework, database, testing, API, and development packages. Selected packages are installed with `npm install`.

## Generated project

`init` creates:

```text
my-node-project/
├── .env
├── .gitignore
├── nodeasy.config.js
├── package.json
├── src/
│   └── index.js
└── test/
```

The generated `package.json` includes `npm start`, `npm run dev`, and `npm test` scripts. `src/index.js` contains only a placeholder comment, so add your application code before using the start and dev scripts. Choosing TypeScript installs TypeScript packages, but the generated entry point and scripts still use JavaScript; TypeScript setup is left to you. Choosing a framework or other package installs it without generating framework specific application code.

`nodeasy.config.js` contains a `port` value. The CLI can read and validate a numeric `port` from a nodeasy configuration file, but the generated application does not currently use it.

## Repository layout

| Path | Purpose |
| --- | --- |
| `nodeasy/bin/index.js` | CLI entry point and `init` command |
| `nodeasy/src/commands/start.js` | Interactive prompts, file creation, and package installation |
| `nodeasy/src/config/` | Configuration loading and validation |
| `nodeasy/templates/` | Route, controller, and service templates; not used by `init` yet |
| `testProject/` | Example project based on the generated structure |

The CLI package currently has no automated test suite. See [nodeasy/README.md](nodeasy/README.md) for package level notes.
