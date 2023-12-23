# Git Submodule Workflow

## Create Projects and Add Submodules

### Create Modules

1. Clone Module A:

```
   git clone <module-a-url>
```

2. Clone Module B:

```
   git clone <module-b-url>
```

3. Add Module B as a submodule to Module A:

```
   git submodule add <module-b-url> path/to/module-a
```

4. Check status and diff for submodules:

```
   git status
   git diff --cached --submodule
```

### Remove Modules (for testing)

- Using command line:

```

rm -rf path/to/module-a

```

- Using PowerShell:

```

rm -r -fo .\path\to\module-a\

```

## Clone a Project with Submodule

1. Clone the project:

```

git clone <project-url>

```

2. Update and initialize submodules:

```

git submodule update --init --recursive

```

Or use the following command:

```
git clone --recurse-submodules <repo-url>
```

## Pulling Changes

- Update all submodules to the latest remote version:

```bash
  git submodule update --remote
```

- Update a specific submodule to the latest remote version or a specific commit:

```bash
  cd path/to/submodule
  git fetch origin
  git checkout <desired-branch-or-tag>
  git pull origin <desired-branch-or-tag>
```

For a specific commit:

```bash
cd path/to/submodule
git fetch origin
git checkout <commit-hash>
```

- Update parent repository after submodule update:

```bash
  cd path/to/parent_repository
  git add path/to/submodule
  git commit -m "Update submodule to specific version/commit"
  git push origin main
```

## Working on a Submodule

Update submodule with remote changes:

```bash
git submodule update --remote --merge
```

Or update submodule with rebase:

```bash
git submodule update --remote --rebase
```

## Pushing Changes

- Push changes, checking submodules:

```bash
  git push --recurse-submodules=check
```

- Make it default:

```bash
  git config push.recurseSubmodules check
```

- Push changes of submodules before pushing the main project:

```bash
  git push --recurse-submodules=on-demand
```
