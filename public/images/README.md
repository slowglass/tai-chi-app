# Public Images

This directory contains images that are served directly without processing.

## Usage

Reference images directly in HTML or CSS:

```html
<img src="/images/logo.png" alt="Logo" />
```

```css
.hero {
  background-image: url('/images/hero-bg.jpg');
}
```

## When to Use

- Large images that don't need optimization
- Images referenced in CSS
- Static assets that don't change often
- Favicon and app icons

## Organization

- `favicon/` - Favicon and app icons
- `backgrounds/` - Large background images
- `static/` - Static images that don't need processing
