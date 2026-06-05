# Dev Setup

Personal Mac development environment setup — starting with Homebrew.

---

## Homebrew

[Homebrew](https://brew.sh) is a package manager for macOS that installs command-line tools, languages, and GUI apps.

### Installation

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installing, follow the **"Next steps"** output in your terminal. On Apple Silicon Macs you need to add Homebrew to your PATH:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Verify the install:

```bash
brew --version
brew doctor
```

---

## Core Commands

### Installing Packages

```bash
brew install <package>        # install a CLI tool or library
brew install --cask <app>     # install a GUI app (e.g. VS Code, Chrome)
```

### Searching

```bash
brew search <name>            # search available packages
brew info <package>           # show details, version, dependencies
```

### Updating

```bash
brew update                   # fetch latest package definitions
brew upgrade                  # upgrade all outdated packages
brew upgrade <package>        # upgrade a specific package
```

### Removing

```bash
brew uninstall <package>      # remove a package
brew autoremove               # remove unused dependencies
brew cleanup                  # delete old versions and cached downloads
```

### Listing

```bash
brew list                     # all installed formulae (CLI tools)
brew list --cask              # all installed casks (GUI apps)
brew outdated                 # packages with available upgrades
```

---

## Useful Extras

```bash
brew leaves                   # packages not depended on by anything else (your "top-level" installs)
brew deps --tree <package>    # show dependency tree for a package
brew pin <package>            # lock a package at its current version
brew unpin <package>          # unlock it again
```

---

## Backing Up & Restoring Packages

Homebrew can export your installed packages to a `Brewfile` so you can restore everything on a new machine.

**Export:**
```bash
brew bundle dump --file=Brewfile --force
```

**Restore on a new machine:**
```bash
brew bundle install --file=Brewfile
```

Commit the `Brewfile` to this repo to keep it in sync.

---

## Installed Packages

> Update this section as you add packages. Run `brew bundle dump --file=Brewfile --force` to keep the Brewfile in sync.

### Formulae (CLI tools)

| Package | Install | Purpose |
|---------|---------|---------|
| `git` | `brew install git` | Version control |
| `gh` | `brew install gh` | GitHub CLI — create repos, PRs, issues from terminal |
| `node` | `brew install node` | Node.js runtime + npm |
| `pnpm` | `brew install pnpm` | Fast Node package manager |
| `python@3.12` | `brew install python@3.12` | Python runtime |
| `postgresql@16` | `brew install postgresql@16` | PostgreSQL database |
| `redis` | `brew install redis` | In-memory cache / message broker |
| `docker` | `brew install docker` | Container CLI (pairs with Docker Desktop) |
| `kubectl` | `brew install kubectl` | Kubernetes CLI |
| `terraform` | `brew install terraform` | Infrastructure as code |
| `awscli` | `brew install awscli` | AWS CLI |
| `jq` | `brew install jq` | JSON processor for the terminal |
| `wget` | `brew install wget` | File downloader |
| `htop` | `brew install htop` | Interactive process viewer |
| `tree` | `brew install tree` | Print directory trees |

### Casks (GUI apps)

| Package | Install | Purpose |
|---------|---------|---------|
| `visual-studio-code` | `brew install --cask visual-studio-code` | Code editor |
| `docker` | `brew install --cask docker` | Docker Desktop (GUI + daemon) |
| `tableplus` | `brew install --cask tableplus` | Database GUI (Postgres, MySQL, Redis) |
| `postman` | `brew install --cask postman` | API testing |
| `iterm2` | `brew install --cask iterm2` | Terminal emulator |
| `google-chrome` | `brew install --cask google-chrome` | Browser |

---

## Tips

- Run `brew doctor` if something seems broken — it diagnoses common issues.
- Use `brew list | grep <name>` to check if something is already installed.
- Prefer `brew install --cask` for GUI apps so Homebrew can manage updates.
