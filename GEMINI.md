# GEMINI Instructions

## Important: Git Commands Directory

**CRITICAL**: Always run git commands in the project directory: `D:\Projects\Phone\Tai Chi`

### Why This Matters
- Git commands must be executed from the project root directory
- Running `git init` or other git commands from the wrong directory (like user home) will create repositories in the wrong location
- The project directory contains all the source code and configuration files

### Correct Workflow
1. **Always navigate to project directory first**:
   ```powershell
   cd "D:\Projects\Phone\Tai Chi"
   ```

2. **Then run git commands**:
   ```powershell
   git status
   git add .
   git commit -m "message"
   git push
   ```

### What Happened Before
- When `git init` was run from `C:/Users/chris/`, it created a repository in the wrong location
- This caused confusion and required reinitializing in the correct directory
- Always verify you're in the project directory before running git commands

### Verification
Before running any git command, verify you're in the correct directory:
```powershell
Get-Location
# Should show: D:\Projects\Phone\Tai Chi
```

### Project Structure
The project directory contains:
- `package.json` - Node.js dependencies
- `src/` - Svelte source code
- `android/` - Android project files
- `.github/` - GitHub Actions workflows
- `capacitor.config.json` - Capacitor configuration
- All other project files

**Remember**: Git commands only work correctly when run from the project root directory!

## Coding Style Guide

### TypeScript/Svelte Style
- **Indentation**: 2 spaces (no tabs)
- **Quotes**: Single quotes for strings, double quotes for JSX attributes
- **Semicolons**: Always use semicolons
- **Line Length**: Maximum 100 characters
- **Trailing Commas**: Use trailing commas in objects and arrays
- **Types**: Explicit typing for function parameters and return values
- **Interfaces**: Use interfaces for object shapes and data structures

### Svelte Component Structure
```svelte
<script lang="ts">
  // Imports first
  import { onMount } from 'svelte'
  import Component from './Component.svelte'
  
  // Type definitions
  interface Props {
    title: string
    count?: number
  }
  
  // Props and variables
  export let prop: string = 'default'
  let localVar: string = ''
  
  // Reactive statements
  $: computed: string = prop + localVar
  
  // Functions
  function handleClick(): void {
    // function body
  }
  
  // Lifecycle
  onMount(() => {
    // initialization
  })
</script>

<!-- HTML template -->
<div class="container">
  <h1>{title}</h1>
  <button on:click={handleClick}>
    Click me
  </button>
</div>

<style>
  /* Scoped styles */
  .container {
    padding: 1rem;
  }
</style>
```

### File Naming
- **Components**: PascalCase (e.g., `HomePage.svelte`)
- **Utilities**: camelCase (e.g., `formatDate.js`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `API_ENDPOINTS.js`)

### CSS Style
- **Class Names**: kebab-case (e.g., `.home-container`)
- **Properties**: Alphabetical order when possible
- **Values**: Use meaningful units (rem, em, %)

## Styling Strategy
- **Responsive Design**: The application is designed to be responsive without relying on `@media` queries for different screen sizes. A single set of styles applies across all devices, ensuring a consistent look and feel.

## Release Process
To release a new version, follow these steps:
1.  Update Changelog with a summary of the changes that have been made.
2.  Update version from `x.y.z-SNAPSHOT` to `x.y.z` in `package.json`.
3.  Commit changes to Git with a summary as the commit message (e.g., `chore(release): release vX.Y.Z`).
4. Create and push tag `vX.Y.Z` to GitHub. Ensure the tag message includes the relevant changelog entries and the standard release description.
5.  Update version from `x.y.z` to `x.y.(z+1)-SNAPSHOT` in `package.json`.
6.  Commit version update and push to GitHub (e.g., `chore(release): begin vX.Y.(Z+1) development`).

Please always include at the bottom of the release description: ```
## Installation
1. Download the APK file
2. Enable "Install from unknown sources" on your Android device
3. Install the APK

### System Requirements
- Android 5.1 (API level 22) or higher


**Full Changelog**: https://github.com/slowglass/tai-chi-app/blob/main/CHANGELOG.md
```

### Git Commit Messages
- **Format**: `type(scope): description`
- **Types**: feat, fix, docs, style, refactor, test, chore
- **Examples**:
  - `feat(ui): add navigation component`
  - `fix(android): resolve build configuration issue`
  - `docs(readme): update installation instructions`
