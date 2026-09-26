# nodeasy

nodeasy is an interactive CLI for scaffolding a Node.js project. Its `init` flow prompts for a module system, language, framework, database, and optional tools, then creates starter files and installs the selected packages.

## Try it locally

Install Node.js and npm, then run `npm ci` from this directory. Create an empty directory for the project you want to generate and invoke the CLI from there:

```bash
mkdir my-node-project
cd my-node-project
node /path/to/nodeasy/bin/index.js init
```

Alternatively, run `npm link` in the nodeasy directory, then run `nodeasy init` from the new project directory. The CLI writes into the **current working directory**, including `package.json`, `.env`, `.gitignore`, `nodeasy.config.js`, `src/index.js`, and `test/`; use a new directory to avoid overwriting existing files. It runs `npm install` for packages chosen in the prompts, so npm registry access is needed.

## Current behavior

The generated `package.json` has basic `start`, `dev`, and `test` scripts. `src/index.js` is a placeholder, so the generated application needs code before those scripts do useful work. The tool looks for a `nodeasy` configuration with `cosmiconfig`; its current schema accepts a numeric `port` field, but the scaffolding flow does not use that value yet.

| Path | Purpose |
| --- | --- |
| `bin/index.js` | CLI entry point and `init` command |
| `src/commands/start.js` | Prompts, file generation, and package installation |
| `src/config/` | Configuration loading and schema |
| `templates/` | Route, controller, and service templates for future use |

There is no automated test suite in this package yet.
