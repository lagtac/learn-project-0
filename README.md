# Learn Modern Web Dev

Being overwhelmed by the complexity of modern web dev tooling we decided to start a JS project from scratch to see where it goes.

To do this we created a new profile on VS Code with no extensions, apart from git history. You can check the User settings later in this article.

Starting our project from scratch, it goes like this:

```
> mkdir [project name]
> cd [project name]
> yarn init --yes
> touch jsconfig.json # see https://code.visualstudio.com/docs/languages/jsconfig
```

We initialize jsconfig.json with the following:

```
// jsconfig.json

{
  "compilerOptions": {
    "module": "ESNext",
    "target": "ESNext",
    "checkJs": true
  },
  "include": [
    "./src/**/*"
  ],
  "typeAcquisition": {
    "enable": true
  },
  "compileOnSave": true
}
```

See https://code.visualstudio.com/docs/languages/jsconfig


## Git

After that we git it:

```
> echo node_modules > .gitignore
> git init
> git add -A
> git commit "First commit."
```

Also, following good practice we make sure the branch name defaults to main. In case we use git version < 2.28, we have to manually rename the master branch.

```
> git branch -m master main
```

On version > 2.28, git has enabled a default branch name setting, which can be set like so:

```
> git config --global init.defaultBranchName main
```

See https://superuser.com/questions/1419613/change-git-init-default-branch-name


## ESLint

Following the recommended instructions we do:

```
> npm init @eslint/config # answer a bunch of questions
```

This results in the following configuration:

```
// .eslintrc.js

module.exports = {
    "env": {
        "browser": true,
        "es2021": true
    },
    "extends": "standard-with-typescript",
    "overrides": [
        {
            "env": {
                "node": true
            },
            "files": [
                ".eslintrc.{js,cjs}"
            ],
            "parserOptions": {
                "sourceType": "script"
            }
        }
    ],
    "parserOptions": {
        "ecmaVersion": "latest",
        "sourceType": "module"
    },
    "rules": {
    }
}
```

See https://eslint.org/docs/latest/use/getting-started


## VS Code

We created a new blank profile in VS Code titled "Web Dev - Plain". This removes any extensions except WSL. We also installed Git History. For starters, We tweaked some *User settings*:

```
{
    "editor.formatOnSave": true,
    "diffEditor.codeLens": true,
    "editor.screenReaderAnnounceInlineSuggestion": false,
    "files.trimTrailingWhitespace": true,
    "files.trimFinalNewlines": true,
    "editor.tabCompletion": "on",
    "editor.tabSize": 2,
    "emmet.triggerExpansionOnTab": true,
    "css.lint.boxModel": "warning",
    "css.lint.compatibleVendorPrefixes": "warning",
    "html.format.preserveNewLines": false,
    "html.format.templating": true,
    "javascript.inlayHints.functionLikeReturnTypes.enabled": true,
    "javascript.inlayHints.parameterNames.enabled": "literals",
    "javascript.inlayHints.parameterTypes.enabled": true,
    "javascript.inlayHints.propertyDeclarationTypes.enabled": true,
    "javascript.inlayHints.variableTypes.enabled": true,
    "javascript.referencesCodeLens.enabled": true,
    "javascript.suggest.completeFunctionCalls": true,
    "js/ts.implicitProjectConfig.checkJs": true,
    "js/ts.implicitProjectConfig.experimentalDecorators": true
}
```

We now have to install the ESLint extension and make some *Workspace* configuration. Also we need to understand which setting are best kept in the workspace.


# TODO

- Install ESLint extension from:

  https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint

- Figure out linting and formatting:

  https://eslint.org/docs/latest/use/getting-started

- Write scripts for building, watching and serving.
- Write some code ffs!
