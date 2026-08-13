# Yingsheng HEP Codex Marketplace

Public Codex marketplace index for private high-energy-physics plugins. The repository exposes plugin names and pinned Git commit identifiers, but the plugin source remains in authenticated private submodules.

## Install on another Windows PC

Authenticate GitHub, clone the private submodules, and register the resulting local marketplace:

```powershell
gh auth login
gh auth setup-git
git clone --recurse-submodules https://github.com/Turgon-Aran-Gondolin/codex-hep-marketplace.git
Set-Location codex-hep-marketplace
codex plugin marketplace add (Get-Location).Path
codex plugin add latex-paper-writing@yingsheng-hep
codex plugin add hep-amplitude-computation@yingsheng-hep
```

Start a new Codex task after installation.

## Update

From the cloned marketplace directory:

```powershell
git pull --ff-only
git submodule update --init --recursive
codex plugin add latex-paper-writing@yingsheng-hep
codex plugin add hep-amplitude-computation@yingsheng-hep
```

## Layout

- `.agents/plugins/marketplace.json` defines the `yingsheng-hep` marketplace.
- `plugins/latex-paper-writing` pins the paper-writing plugin repository.
- `plugins/hep-amplitude-computation` pins the amplitude-computation plugin repository.

Codex marketplace entries resolve repository-local plugin paths. Git authentication is therefore required before initializing or updating the private submodules.
