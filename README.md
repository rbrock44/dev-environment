# Dev Environment

> This project holds my editor and IDE configuration so a new machine can be set up the way I actually work <br/>

---

## 📚 Table of Contents

- [What's My Purpose?](#-whats-my-purpose)
- [How to Use](#-how-to-use)
  - [IntelliJ IDEA](#intellij-idea)
  - [Rider](#rider)
  - [VS Code](#vs-code)
- [Technologies](#-technologies)
- [Getting Started (Local Setup)](#-getting-started-local-setup)

---

## 🧠 What's My Purpose?

This project holds the IDE and editor settings I want to survive a reinstall — code styles, keymaps, inspection profiles, and editor preferences.

This is deliberately **not** machine setup. Shell config (`.bashrc`, `.bash_profile`), oh-my-posh, and `Setup-NewPC.ps1` live in [scripts](https://github.com/rbrock44/scripts). If it configures the OS or the shell, it goes there. If it configures an editor, it goes here.

AI tooling config (Claude Code settings, skills, agents) lives in [ai-config](https://github.com/rbrock44/ai-config).

---

## 🚦 How to Use

Copy the files into the matching config directory, then restart the IDE. Version numbers in the JetBrains paths change with each release — check what's actually installed before copying.

---

### IntelliJ IDEA

Target: `%APPDATA%\JetBrains\IntelliJIdea<version>\`

* `codestyles/Default.xml`
  * Kotlin official code style, Java continuation indent of 4
* `keymaps/Default Proper Redo.xml`
  * Custom keymap. Redo bound to `Ctrl+Shift+Z` / `Ctrl+Y`, unbinds `EditorDeleteLine`, adds tab-group movement and `Ctrl+Shift+F5` for Run Class
  * After copying, select it under Settings → Keymap — dropping the file in does not activate it
* `inspection/Default.xml`
  * Default inspection profile, kept so the slot exists when it grows
* `idea64.exe.vmoptions`
  * Heap bumped to 4089m
* `options/`
  * `editor.xml` — soft wrap for `*.md; *.txt; *.rst; *.adoc`, newline at EOF, ctrl+wheel font size
  * `editor-font.xml` / `terminal-font.xml` — 14pt
  * `colors.scheme.xml` — Dark scheme
  * `terminal.xml` — Git Bash as the built-in terminal shell
  * `filetypes.xml` — `.gradle.kts` / `.space.kts` / `.main.kts` as Kotlin, `.env.*` and `.ts` as plain text
  * `ide.general.xml` — new UI on, no startup tips, no new-project confirmation

---

### Rider

Target: `%APPDATA%\JetBrains\Rider<version>\`

Not installed on this machine yet, so nothing is captured. Rider shares the JetBrains layout, so `codestyles/`, `keymaps/`, and `options/` transfer over from the IntelliJ folder where the settings overlap.

---

### VS Code

Target: `%APPDATA%\Code\User\`

* `settings.json`
  * Auto-save after delay, auto-update imports on file move for TS/JS, Python format-on-type, confirmation dialogs disabled, Claude Code in terminal mode
* `keybindings.json`
  * Empty — defaults are fine, the file is here so overrides have a home
* `snippets/`
  * User snippets

---

## 🛠 Technologies

- IntelliJ IDEA
- Rider
- VS Code

---

## 🚀 Getting Started (Local Setup)

* Clone [repo](https://github.com/rbrock44/dev-environment)
* Close the IDE you are about to configure — JetBrains IDEs rewrite these files on exit and will overwrite what you just copied
* Copy the relevant folder into the target path above
* Reopen the IDE

---
