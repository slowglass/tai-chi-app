# Image Assets

This directory contains image assets that are processed by Vite and imported in your Svelte components.

## Usage

Import images in your Svelte components:

```svelte
<script lang="ts">
  import logo from './assets/images/logo.png'
  import heroImage from './assets/images/hero.jpg'
</script>

<img src={logo} alt="Logo" />
<img src={heroImage} alt="Hero" />
```

## Supported Formats

- PNG, JPG, JPEG, GIF, SVG, WebP
- Images are optimized during build
- Automatic file hashing for cache busting

## Organization

- `logos/` - Company/brand logos
- `backgrounds/` - Background images
- `illustrations/` - Illustrations and graphics
- `photos/` - Photographs
- `ui/` - UI elements and icons
