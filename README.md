# my-vscode-extension
Minimal skeleton JavaScript VS Code extension that does not use Yoeman

## Structure
Recreate this skeletal extension as detailed below:

### With GitHub 
1. Create GitHub repo with a README and the MIT license
1. Clone repo
1. `CD` into directory 

### Without GitHub
1. Create directory
1. `CD` into directory

### Initialise
1. Run `npm init -y`
1. Run `npm install --save-dev @types/vscode`

### Create `extension.js`
Create `extension.js` with the following content:
```javascript
const vscode = require('vscode');

function activate(context) {
    console.log('Extension is now active!');

    let disposable = vscode.commands.registerCommand('extension.helloWorld', function () {
        vscode.window.showInformationMessage('Hello World from My Extension!');
    });

    context.subscriptions.push(disposable);
}

function deactivate() {}

module.exports = {
    activate,
    deactivate
}
```

### Update `package.json`
Update the `package.json` file with the following content:
```json
{
  "name": "my-vscode-extension",
  "displayName": "My VS Code Extension",
  "description": "A simple VS Code extension",
  "version": "0.0.1",
  "license": "MIT",
  "engines": {
    "vscode": "^1.95.0"
  },
  "categories": [
    "Other"
  ],
  "activationEvents": [
    "onCommand:extension.helloWorld"
  ],
  "main": "./extension.js",
  "contributes": {
    "commands": [{
      "command": "extension.helloWorld",
      "title": "Hello World"
    }]
  },
  "scripts": {
    "vscode:prepublish": "npm run compile",
    "compile": "tsc -p ./",
    "watch": "tsc -watch -p ./",
    "pretest": "npm run compile && npm run lint",
    "lint": "eslint src --ext ts",
    "test": "node ./out/test/runTest.js"
  },
  "devDependencies": {
    "@types/vscode": "^1.95.0",
    "@types/node": "14.x"
  }
}
```

> Update the various version numbers, extension name and other information as appropriate.

### Create `.vscodeignore`
Create `.vscodeignore` file with the following content:
```
.vscode/**
.vscode-test/**
node_modules/**
.gitignore
```

### Create `.gitignore`
Create `.gitignore` file with the following content:
```
node_modules
.vscode-test
```

### Debugging
1. Open the `extension.js` file and press F5
1. Open the Command Palette in the launched Code instance
1. Run the `Hello World` command 

### Next Steps
Modify the code and `package.json` as required to implement the desired behaviour.