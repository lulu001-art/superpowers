# Installing Superpowers for Codex

Enable the skills through Codex native skill discovery. Use this repository as the canonical source; do not keep a second active Superpowers clone or symlink.

## Prerequisites

- Git

## Installation

1. **Clone this repository:**
   ```bash
   git clone https://github.com/lulu001-art/superpowers.git ~/.codex/superpowers
   ```

   If `~/.codex/superpowers` already exists, verify its origin before continuing:
   ```bash
   git -C ~/.codex/superpowers remote get-url origin
   ```

   If it points somewhere else, either archive that clone and replace it with this repository, or intentionally keep the other source and do not activate this one. Only one Superpowers source should be active in Codex discovery.

2. **Create the skills symlink:**
   ```bash
   mkdir -p ~/.agents/skills
   ln -s ~/.codex/superpowers/skills ~/.agents/skills/superpowers
   ```

   **Windows (PowerShell):**
   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
   cmd /c mklink /J "$env:USERPROFILE\.agents\skills\superpowers" "$env:USERPROFILE\.codex\superpowers\skills"
   ```

3. **Restart Codex** to discover the skills.

## Migrating from old bootstrap

If you installed Superpowers before native skill discovery:

1. Update or replace the clone so the active source is intentional and unique.
2. Create the skills symlink from step 2.
3. Remove any old `superpowers-codex bootstrap` block from `~/.codex/AGENTS.md`; native skill discovery makes that block unnecessary.
4. Restart Codex.

## Verify

```bash
git -C ~/.codex/superpowers remote get-url origin
ls -la ~/.agents/skills/superpowers
```

Expected origin:

```text
https://github.com/lulu001-art/superpowers.git
```

The `superpowers` entry should point to `~/.codex/superpowers/skills`.

## Updating

```bash
git -C ~/.codex/superpowers pull --ff-only
```

## Uninstalling

```bash
rm ~/.agents/skills/superpowers
```

Optionally archive or delete `~/.codex/superpowers` after confirming it is not used elsewhere.
