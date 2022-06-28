# Setup WSL Development Environment

## ~~Method 1: Interactive~~
```bash
~~curl -o- https://raw.githubusercontent.com/p1n2o/wsl-env-setup/master/wsl-env-setup.sh | bash~~
```
## Method 2: Manual Install

### 00. Update Linux Packages
```bash
sudo apt update && sudo apt upgrade -y
```

### 01. Install / Update Version Control System — Git Setup
#### 01.01. Add Git PPA + Update Git
```bash
sudo add-apt-repository ppa:git-core/ppa -y && sudo apt update && sudo apt upgrade -y
```
#### 01.02. Configure Git
```bash
git config --global user.name "Manuel Pinto" #Configure Git User Name
```
```bash
git config --global user.email manuel@pinto.dev #Configure Git User Email
```
```bash
git config --global init.defaultBranch main #Set 'main' as default branch
```
```bash
git config --global core.fsmonitor true #Use inbuilt filesystem monitor
```
#### 01.03. Generate SSH Key
```bash
ssh-keygen -t rsa -f "$HOME/.ssh/id_rsa" -P "" && cat $HOME/.ssh/id_rsa.pub
```
#### 01.04. Generate GPG Key
```bash
gpg --full-gen-key
```
```bash
gpg --list-secret-keys --keyid-format LONG manuel@pinto.dev
```
```bash
gpg --armor --export 0123456789
```
```bash
git config --global user.signingkey 01234567890123456789
```
---
### 02. Install Node Version Manager — Node + NPM Setup
#### 02.01. Install / Update NVM
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```
#### 02.02. Install Node (LTS)
```bash
nvm install --lts
```
##### Replace ```--lts``` with ```node``` to install latest node version
##### Append ```--reinstall-packages-from=default``` to update while preserving global packages
##### Append ```--latest-npm``` to install / update to latest NPM version
##### Execute ```nvm install-latest-npm``` to only update NPM to latest version
---
### 03. Terminal — ZSH Setup
#### 03.01. Install ZSH
```bash
sudo apt install zsh -y
```
#### 03.02. Install Oh My ZSH!
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
#### 03.03. Install OMZ Plugins
Auto Suggestions
```bash
git clone --depth=1 https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
Syntax Highlighting
```bash
git clone --depth=1 https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
Power Level 10K Theme
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```
#### 03.04. Configure ZSH
```bash
nano ~/.zshrc
```
```bash
# Use Powerlevel10k theme
ZSH_THEME="powerlevel10k/powerlevel10k"
```
```bash
# Use plugins
plugins=(debian git nvm node npm ng python pip zsh-autosuggestions zsh-syntax-highlighting)
```
---
### [04] Code Editor - VS Code Setup
Launch VS Code Quick Open (Ctrl+P) and paste the below commands:
#### Install VS Code Extension - ESLint
```bash
ext install dbaeumer.vscode-eslint
```
#### Install VS Code Extension - Prettier
```bash
ext install esbenp.prettier-vscode
```
#### Install VS Code Extension - GitLens
```bash
ext install eamodio.gitlens
```
#### Install VS Code Extension - Code Spell Checker
```bash
ext install streetsidesoftware.code-spell-checker
```
#### Install VS Code Extension - One Dark Pro
```bash
ext install zhuangtongfa.material-theme
```
#### Install VS Code Extension - Material Icon Theme
```bash
ext install PKief.material-icon-theme
```
#### Install VS Code Extension - Angular Language Service
```bash
ext install angular.ng-template
```
------
### VS Code Settings (Optional)
```jsonc
{
  // Workbench
  "workbench.startupEditor": "newUntitledFile",
  "workbench.colorTheme": "One Dark Pro",
  "workbench.iconTheme": "material-icon-theme",
  // Editor
  "editor.fontFamily": "'Fira Code Retina', Consolas, 'Courier New', monospace",
  "editor.fontSize": 16,
  "editor.wordWrapColumn": 240,
  "editor.formatOnType": true,
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,
  "editor.minimap.enabled": true,
  "editor.renderControlCharacters": true,
  "editor.cursorBlinking": "smooth",
  "editor.cursorSmoothCaretAnimation": true,
  "editor.fontLigatures": true,
  "editor.inlineSuggest.enabled": true,
  "editor.codeActionsOnSave": {
    "source.fixAll": true,
    "source.organizeImports": true
  },
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[html]": {
    "editor.defaultFormatter": "HookyQR.beautify"
  },
  "css.lint.duplicateProperties": "warning",
  "git.autofetch": true,
  "git.confirmSync": false,
  "git.enableSmartCommit": true,
  "explorer.confirmDelete": false,
  // "emmet.triggerExpansionOnTab": true,
  "angular.log": "off",
  "terminal.external.windowsExec": "C:\\Users\\manuel_pinto\\AppData\\Local\\Microsoft\\WindowsApps\\wt.exe",
  "http.proxyStrictSSL": false,
  "terminal.integrated.copyOnSelection": true,
  "terminal.integrated.tabs.enabled": true,
  "terminal.integrated.cursorBlinking": true,
  "telemetry.enableCrashReporter": false,
  "telemetry.enableTelemetry": false,
  "terminal.integrated.experimentalUseTitleEvent": false,
  "workbench.editor.scrollToSwitchTabs": true,
  "json.maxItemsComputed": 99999,
  "js/ts.implicitProjectConfig.experimentalDecorators": true,
  "editor.linkedEditing": true,
  "eslint.alwaysShowStatus": true,
  "explorer.confirmDragAndDrop": false,
  "diffEditor.ignoreTrimWhitespace": false,
  "typescript.disableAutomaticTypeAcquisition": true,
  "files.autoSave": "onWindowChange",
  "cSpell.allowCompoundWords": true,
  "cSpell.userWords": ["mixins", "ngsw"],
  "angular.experimental-ivy": true,
  "diffEditor.maxComputationTime": 0,
  "javascript.updateImportsOnFileMove.enabled": "always",
  "scm.alwaysShowRepositories": true,
  "extensions.ignoreRecommendations": true,
  "git.autoStash": true,
  "terminal.integrated.defaultProfile.linux": "zsh",
  "terminal.integrated.cursorStyle": "underline",
  "terminal.integrated.enableBell": true,
  "prettier.printWidth": 120,
  "prettier.singleQuote": true,
  "prettier.requireConfig": true,
  "prettier.useTabs": true,
  "terminal.integrated.fontFamily": "\"MesloLGS NF\"",
  "typescript.suggest.paths": false,
  "workbench.list.multiSelectModifier": "alt",
  "workbench.panel.defaultLocation": "bottom",
  "quokka.showStartViewOnFeatureRelease": false,
  "cSpell.enableFiletypes": [
    "!properties"
  ],
  "security.workspace.trust.untrustedFiles": "open",
  "typescript.enablePromptUseWorkspaceTsdk": true,
  
  "github.copilot.autocomplete.enable": true,
  "typescript.updateImportsOnFileMove.enabled": "always",
  "github.copilot.autocomplete.count": 5,
  "github.copilot.inlineSuggest.count": 5,
  "github.copilot.list.count": 15
}
```
---
### [05] Project - Angular Setup
#### Install Angular CLI (Globally)
```bash
npm i -g @angular/cli
```
#### Project - Install ESLint and Prettier (with add-ons)
```bash
npm i -D eslint prettier eslint-plugin-prettier eslint-config-prettier
# npm install -D eslint @typescript-eslint/eslint-plugin eslint-plugin-prettier eslint-plugin-angular prettier prettier-eslint eslint-config-prettier
```
#### Project - Generate ESLint Config. Files
Generate ".eslintrc"
```bash
touch .eslintrc
```
```jsonc
{
  "parser": "@typescript-eslint/parser",
  "extends": ["plugin:angular/johnpapa", "plugin:@typescript-eslint/recommended", "prettier"],
  "parserOptions": {
    "ecmaVersion": 11,
    "sourceType": "module"
  },
  "settings": {
    "angular": {
      "version": "detect"
    }
  },
  "root": true,
  "env": {
    "node": true,
    "jest": true
  },
  "rules": {
    "@typescript-eslint/interface-name-prefix": "off",
    "@typescript-eslint/explicit-function-return-type": "off",
    "@typescript-eslint/no-explicit-any": "off"
  },
  "ignorePatterns": ["/*.*"]
}
```
Generate ".eslintignore"
```bash
touch .eslintignore
```
```
karma.conf.js
dist
```
#### [4.3] Generate Prettier Config. Files
Generate ".prettierrc"
```bash
touch .prettierrc
```
```jsonc
{
  "semi": true,
  "trailingComma": "none",
  "singleQuote": true,
  "printWidth": 120,
  "tabWidth": 2
}
```
Generate ".prettierrcignore"
```bash
touch .prettierrcignore
```
```
package.json
package-lock.json
dist
```
#### [4.X] Replace Default Lint Command in package.json (Optional)
###### Replace `ng lint` to `./node_modules/.bin/tsc --noEmit && ./node_modules/.bin/eslint . --ext js,ts,json --fix`
------



















------
### [7] Increase Max. User Watches (fix for WSL)
```bash
sudo sysctl -w fs.inotify.max_user_watches=524288
```





















# Install WSL
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# Enable Virtual Machine Platform
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Use WSL2 per default
wsl --set-default-version 2

install linux distro

"commandline": "wsl.exe ~"

"fontFace": "MesloLGS NF"

sudo apt install zsh
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

$ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
$ git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k


nano ~/.zshrc

# Use Powerlevel10k theme
ZSH_THEME="powerlevel10k/powerlevel10k"

# Use plugins
plugins=(git nvm zsh-autosuggestions zsh-syntax-highlighting)
