# Icon Assets

This directory contains icon assets for the application.

## Usage

Import icons in your Svelte components:

```svelte
<script lang="ts">
  import homeIcon from './assets/icons/home.svg'
  import userIcon from './assets/icons/user.svg'
</script>

<img src={homeIcon} alt="Home" class="icon" />
<img src={userIcon} alt="User" class="icon" />
```

## Recommended Formats

- **SVG** - Best for scalable icons
- **PNG** - For complex icons with transparency
- **WebP** - Modern format with good compression

## Organization

- `ui/` - UI icons (buttons, navigation, etc.)
- `social/` - Social media icons
- `brand/` - Brand-specific icons
- `system/` - System icons (settings, help, etc.)
