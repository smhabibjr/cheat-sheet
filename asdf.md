# ASDF Cheat Sheet

## General Commands
- **List all installed plugins**:  
  ```bash
  asdf plugin-list
  ```
  Example:
  ```bash
  asdf plugin-list
  ```
- **See all available plugins**:  
  ```bash
  asdf plugin-list-all
  ```
  Example:
  ```bash
  asdf plugin-list-all
  ```

---

## Plugin Management
- **Install a plugin**:  
  ```bash
  asdf plugin add <plugin-name>
  ```
  Example:  
  ```bash
  asdf plugin add nodejs
  ```
- **Remove a plugin**:  
  ```bash
  asdf plugin remove <plugin-name>
  ```
  Example:  
  ```bash
  asdf plugin remove nodejs
  ```

---

## Popular Plugins
- **Node.js**: `nodejs`  (React.js, Vue.js requires Node.js, no separate plugin exists)
- **Ruby**: `ruby`
- **Java**: `java`
- **Python**: `python`

Other popular plugins:  
- **Go**: `golang`  
- **Elixir**: `elixir`  
- **Erlang**: `erlang`  
- **Rust**: `rust`  
- **PHP**: `php`  
- **Docker Compose**: `docker-compose`  
- **Terraform**: `terraform`  
- **Kubectl**: `kubectl`  

---

## Version Management
- **Install a specific version of a package**:  
  ```bash
  asdf install <plugin-name> <version>
  ```
  Example:  
  ```bash
  asdf install nodejs 18.17.0
  ```
- **Install the latest stable version**:  
  ```bash
  asdf install <plugin-name> latest
  ```
  Example:  
  ```bash
  asdf install nodejs latest
  ```
- **Uninstall a version**:  
  ```bash
  asdf uninstall <plugin-name> <version>
  ```
  Example:  
  ```bash
  asdf uninstall nodejs 18.17.0
  ```

---

## Setting Versions
- **Set a version globally**:  
  ```bash
  asdf global <plugin-name> <version>
  ```
  Example:  
  ```bash
  asdf global nodejs 18.17.0
  ```
- **Set a version locally (specific to a directory)**:  
  ```bash
  asdf local <plugin-name> <version>
  ```
  Example:  
  ```bash
  asdf local nodejs 18.17.0
  ```

---

## Version Information
- **See current global version**:  
  ```bash
  asdf global
  ```
  Example:  
  ```bash
  asdf global
  ```
- **See current local version**:  
  ```bash
  asdf local
  ```
  Example:  
  ```bash
  asdf local
  ```
- **List all installed versions for a plugin**:  
  ```bash
  asdf list <plugin-name>
  ```
  Example:  
  ```bash
  asdf list nodejs
  ```

---

## Node.js-Specific Use Cases
- **Install Node.js**:  
  ```bash
  asdf install nodejs <version>
  ```
  Example:  
  ```bash
  asdf install nodejs 18.17.0
  ```
- **Install the latest stable Node.js**:  
  ```bash
  asdf install nodejs latest
  ```
  Example:  
  ```bash
  asdf install nodejs latest
  ```
- **Install a Node.js package locally**:  
  ```bash
  npm install <package-name>
  ```
  Example:  
  ```bash
  npm install lodash
  ```
- **Install a Node.js package globally**:  
  ```bash
  npm install -g <package-name>
  ```
  Example:  
  ```bash
  npm install -g typescript
  ```
- **Uninstall Node.js locally**:  
  ```bash
  asdf uninstall nodejs <version>
  ```
  Example:  
  ```bash
  asdf uninstall nodejs 18.17.0
  ```
- **Uninstall Node.js globally**:  
  ```bash
  asdf uninstall nodejs <version>
  ```
  Example:  
  ```bash
  asdf uninstall nodejs 18.17.0
  ```

---

## Utilities
- **See all available versions for a plugin**:  
  ```bash
  asdf list all <plugin-name>
  ```
  Example:  
  ```bash
  asdf list all nodejs
  ```
- **Check current Node.js version**:  
  ```bash
  node -v
  ```
  Example:  
  ```bash
  node -v
  ```

---

## Notes
1. **Refresh `asdf` after adding a plugin**:  
   ```bash
   asdf reshim <plugin-name>
   ```
   Example:  
   ```bash
   asdf reshim nodejs
   ```
2. **For Node.js plugin**: Ensure to trust the Node.js release team’s GPG key before installing.  
   ```bash
   bash ~/.asdf/plugins/nodejs/bin/import-release-team-keyring
   ```
