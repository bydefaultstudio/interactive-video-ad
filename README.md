# Interactive Video Display Ad - 300x600

A rich media display advertisement built with Google Web Designer, featuring an interactive video experience that showcases multiple products through synchronized cue points.

## Overview

This is a 300x600 pixel display ad that combines video playback with interactive product showcases. The ad automatically cycles through four different Fendi products as the video plays, with each product appearing at specific video timestamps (cue points).

## Key Features

- **Interactive Video Playback**: Autoplay, looped, muted video background
- **Dynamic Product Showcase**: Four products displayed sequentially based on video timing
- **Clickable Product Areas**: Each product has a clickable tap area linking to Fendi product pages
- **Transparent Background**: Allows seamless integration with publisher websites
- **CDN-Hosted Assets**: All media assets served via jsDelivr CDN for optimal performance

## Video Cue Points

The ad uses **video cue points** to synchronize product displays with specific moments in the video timeline. This is the core functionality of the interactive experience.

### Cue Point Timeline

#### Cue Point 1 (Start - 0:00)
- **Action**: 
  - Displays **Product 1** (product-1 div)
  - Activates **Tap Area 1** (taparea_1)
- **Product**: Mamma Baguette Medium Sea Garden Bag
- **Exit URL**: Links to Fendi product page for the coral red and camellia embroidered bag

#### Cue Point 2 (3.85 seconds)
- **Action**:
  - Hides **Product 1**
  - Displays **Product 2** (product-2 div)
  - Hides **Tap Area 1**
  - Activates **Tap Area 4** (taparea_4)
- **Product**: Baguette Coral Bandana Embroidered Lace Bag
- **Exit URL**: Links to Fendi product page for the summer bag

#### Cue Point 3 (5.77 seconds)
- **Action**:
  - Hides **Product 2**
  - Displays **Product 3** (product-3 div)
  - Hides **Tap Area 4**
  - Activates **Tap Area 2** (taparea_2)
- **Product**: Baguette Woven Bag with Sea Garden Embroideries
- **Exit URL**: Links to Fendi product page for the woven bag

#### Cue Point 4 (10.68 seconds)
- **Action**:
  - Hides **Product 3**
  - Displays **Product 4** (product-4 div)
  - Hides **Tap Area 2**
  - Activates **Tap Area 3** (taparea_3)
- **Product**: FF Diamonds White Acetate Sunglasses
- **Exit URL**: Links to Fendi product page for the sunglasses

### How Cue Points Work

1. **Video plays automatically** (muted, looping)
2. **At each cue point timestamp**, JavaScript event handlers are triggered
3. **Product visibility** is toggled using CSS `display: block/none`
4. **Tap areas** are activated/deactivated to enable clickable regions
5. **Metrics are tracked** when each cue point is reached
6. **When video loops**, the sequence repeats from the beginning

## Technical Architecture

### Components

- **gwd-video**: Main video player component with autoplay, loop, and muted attributes
- **gwd-cuepoint**: Defines timing markers in the video (4 cue points total)
- **gwd-image**: Displays product images and branding elements
- **gwd-taparea**: Creates clickable regions over products
- **gwd-google-ad**: Main ad container with Google Ad Manager integration

### Asset Structure

Each product display consists of:
- **Product Image** (`product_XX.jpg`): Main product photo
- **Product Info** (`product-info_XX.png`): Product details overlay
- **Tap Area**: Invisible clickable region positioned over the product

### Event Handlers

The ad uses Google Web Designer's event system:
- **Cue Point Events**: Triggered when video reaches specific timestamps
- **Tap Area Events**: Handle user clicks and exit to product pages
- **Metric Events**: Track engagement (cue point views, exits)

## Metrics & Tracking

The ad tracks the following events:
- **Cue Point Reached**: Fired when each of the 4 cue points is reached
- **Exit Clicks**: Tracked when users click on product tap areas
- **Video Engagement**: Standard video metrics via Google Ad Manager

## Asset Delivery

All assets are served via **jsDelivr CDN**:
- Base URL: `https://cdn.jsdelivr.net/gh/bydefaultstudio/interactive-video-ad@main/`
- Video: `vdo.mp4`
- Images: `product_XX.jpg`, `product-info_XX.png`
- Logos: `logo_fendi.svg`, `dianomi-interactive.svg`
- Poster: `poster.jpg`

## Browser Compatibility

Built with Google Web Designer 16.4.0, compatible with:
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile devices (iOS, Android)
- Google Ad Manager environments

## File Structure

```
├── index.html          # Main ad HTML file
├── vdo.mp4            # Video file (281KB)
├── poster.jpg         # Video poster image
├── product_01.jpg     # Product 1 image
├── product_02.jpg     # Product 2 image
├── product_03.jpg     # Product 3 image
├── product_04.jpg     # Product 4 image
├── product-info_01.png # Product 1 info overlay
├── product-info_02.png # Product 2 info overlay
├── product-info_03.png # Product 3 info overlay
├── product-info_04.png # Product 4 info overlay
├── logo_fendi.svg     # Fendi logo
└── dianomi-interactive.svg # Dianomi branding
```

## Customization

To modify cue point timings, edit the `time` attribute in the `gwd-cuepoint` elements:
```html
<gwd-cuepoint time="3.85" id="cue_point_2"></gwd-cuepoint>
```

To change product links, update the exit URLs in the tap area event handlers or `gwd-exit` elements.

## Notes

- The video loops continuously, creating a seamless product showcase cycle
- All products are initially hidden and shown only at their respective cue points
- Tap areas are synchronized with product visibility to ensure correct click targets
- The ad uses "polite load" to respect user bandwidth and page performance

