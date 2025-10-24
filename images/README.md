# Leo's Coffee - Image Assets

## Directory Structure

```
images/
├── source/          # Original high-resolution images (1920x1080)
├── optimized/       # WebP optimized versions for web use
├── thumbnails/      # Thumbnail versions (400x300)
├── image-manifest.json  # Complete image metadata and usage guide
└── README.md        # This file
```

## Image Inventory

**Total Images: 10**

### Hero Images (2)
- `hero-exterior-1.jpg` - Main exterior storefront view
- `hero-exterior-2.jpg` - Alternative exterior entrance view

### Gallery Images (8)

**Interior Views (4):**
- `gallery-interior-1.jpg` - Seating and ambiance
- `gallery-interior-2.jpg` - Decor details
- `gallery-interior-3.jpg` - Third interior perspective
- `gallery-seating-1.jpg` - Customer seating area

**Product Images (2):**
- `gallery-coffee-1.jpg` - Specialty coffee drinks
- `gallery-coffee-2.jpg` - Artisan beverages

**Staff Images (1):**
- `gallery-barista-1.jpg` - Barista at work

**Food Images (1):**
- `gallery-food-1.jpg` - Pastries and food items

## Usage Guidelines

### Web Implementation

1. **Hero Section**: Use `hero-exterior-1.jpg` or `hero-exterior-2.jpg`
2. **Gallery Section**: All `gallery-*` images
3. **About Section**: Interior images
4. **Menu Section**: Coffee and food images

### Optimization Requirements

**Hero Images:**
- Format: WebP
- Max dimensions: 1920x1080
- Quality: 85%
- Lazy loading: No (above fold)

**Gallery Images:**
- Format: WebP
- Max dimensions: 1200x800
- Quality: 80%
- Lazy loading: Yes

**Thumbnails:**
- Format: WebP
- Max dimensions: 400x300
- Quality: 75%
- Purpose: Preview/grid views

## Next Steps

1. Optimize images to WebP format using tools like:
   - `cwebp` (Google's WebP encoder)
   - ImageMagick
   - Sharp (Node.js)

2. Generate responsive versions:
   - Desktop: 1920w
   - Tablet: 1200w
   - Mobile: 768w

3. Implement lazy loading for gallery images

4. Add proper `srcset` and `sizes` attributes for responsive images

## Source

All images downloaded from Google Places API on 2025-10-24.
Original resolution: 1920x1080 pixels.

## SEO & Accessibility

Each image in `image-manifest.json` includes:
- Descriptive filenames
- Alt text for screen readers
- Usage context
- Category classification

Refer to `image-manifest.json` for complete metadata.
