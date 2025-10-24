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

### JavaScript/Svelte Style
- **Indentation**: 2 spaces (no tabs)
- **Quotes**: Single quotes for strings, double quotes for JSX attributes
- **Semicolons**: Always use semicolons
- **Line Length**: Maximum 100 characters
- **Trailing Commas**: Use trailing commas in objects and arrays

### Svelte Component Structure
```svelte
<script>
  // Imports first
  import { onMount } from 'svelte'
  import Component from './Component.svelte'
  
  // Props and variables
  export let prop = 'default'
  let localVar = ''
  
  // Reactive statements
  $: computed = prop + localVar
  
  // Functions
  function handleClick() {
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

### Git Commit Messages
- **Format**: `type(scope): description`
- **Types**: feat, fix, docs, style, refactor, test, chore
- **Examples**:
  - `feat(ui): add navigation component`
  - `fix(android): resolve build configuration issue`
  - `docs(readme): update installation instructions`
