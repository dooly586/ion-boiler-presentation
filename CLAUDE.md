# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Korean presentation website for 이온히팅보일러 (Ion Heating Boiler) technology showcase. It's a fullscreen presentation system with 5 slides demonstrating the technology, performance metrics, and case studies.

## Architecture

### Core Structure
- **index.html** - Fullscreen presentation system with adaptive scaling
- **page_1.html to page_5.html** - Individual presentation slides (1280x720px)
- **Responsive Scaling System** - Automatic scaling to fit any screen size while maintaining aspect ratio

### Key Components

#### Main Presentation System (index.html)
- **Fullscreen Display**: Slides scale to fit viewport while preserving 1280x720 aspect ratio
- **Overlay Navigation**: Floating controls that don't interfere with slide content
- **Multi-Input Navigation**: Arrow keys, mouse wheel, touch gestures, keyboard shortcuts
- **Deep Linking**: Hash-based URL navigation (#p=1, #p=2, etc.)
- **Presentation-Ready**: Optimized for fullscreen presentation mode

#### Slide Architecture
All slides follow consistent structure:
- **Fixed Dimensions**: 1280x720px (presentation format)
- **Styling Framework**: TailwindCSS + custom CSS
- **Icon System**: Font Awesome 6.0.0-beta3
- **Background Pattern**: Grid-based design with animated elements
- **Color Scheme**: Teal/green gradient theme (#009688 primary)

#### Navigation Controls
- **Arrow Controls**: Left/right arrows with hover scaling effects
- **Jump Controls**: "처음" (first) and "끝" (last) buttons in bottom corners  
- **Page Indicator**: Current slide counter at bottom center
- **Keyboard Support**: Arrow keys, spacebar, Home/End keys
- **Touch/Scroll**: Swipe gestures and mouse wheel navigation

#### Visual System
- **Background**: Radial gradient with grid pattern overlay
- **Scaling Logic**: CSS transform scaling maintains crisp presentation quality
- **Smooth Transitions**: Fade transitions between slides with proper z-index layering

## Development Commands

### Local Development
```bash
# Start a local server (Python 3)
python -m http.server 8000

# Start a local server (Node.js)
npx http-server

# Start a local server (PHP)
php -S localhost:8000
```

### Testing Navigation
- **Arrow Keys**: ← → for navigation
- **Special Keys**: Home (first slide), End (last slide), Space (next slide)
- **Mouse Wheel**: Scroll up/down to navigate
- **Touch Gestures**: Swipe left/right or up/down
- **Deep Links**: Test `#p=1` through `#p=5`
- **Responsive Scaling**: Test different viewport sizes

## Content Structure

### Slide Topics
1. **page_1.html** - Title slide with main branding
2. **page_2.html** - Korean enterprise case studies (현대자동차 아산공장)
3. **page_3.html** - KCL certification test results
4. **page_4.html** - Technical specifications and performance data
5. **page_5.html** - Summary and contact information

### Styling Conventions
- **Korean Typography**: System fonts with Korean fallbacks
- **Color Palette**: Primary #009688, gradients from #f0f9ff to #e6f7ef
- **Component Classes**: `.title-box`, `.content-card`, `.stat-card`, `.icon-circle`
- **Animation**: Pulse effects, hover transforms, CSS transitions

### Data Visualization
- **D3.js v7**: Used for charts on performance metrics
- **Chart Types**: Bar charts, comparison visualizations
- **Data Format**: Embedded JavaScript objects with Korean labels

## File Management

### Adding New Slides
1. Create new HTML file following existing page structure (1280x720px)
2. Add new `.slide-wrap` container with iframe in index.html
3. Update `totEl.textContent = wraps.length` in JavaScript
4. Ensure proper sequencing in DOM order

### Modifying Content
- **Text Updates**: Direct HTML editing in individual page files
- **Styling Changes**: Update embedded `<style>` sections
- **Data Updates**: Modify JavaScript data objects in D3.js sections
- **Image Updates**: Replace external URLs with new sources

### External Dependencies
- **TailwindCSS**: Loaded via CDN
- **Font Awesome**: v6.0.0-beta3 via CDN
- **D3.js**: v7 via CDN for data visualization
- **External Images**: Various sources, ensure CORS compliance

## Browser Compatibility

### Supported Features
- Modern CSS Grid and Flexbox
- ES6+ JavaScript features
- CSS Custom Properties
- Transform and Animation properties

### Fallback Considerations
- Mobile viewport handling at 640px breakpoint
- Touch navigation support
- Graceful degradation for older browsers
- ARIA accessibility attributes where applicable

## Technical Notes

### Presentation System Architecture
- **Scaling Algorithm**: `Math.min(vw/1280, vh/720)` maintains aspect ratio without cropping
- **Event Handling**: Debounced wheel events (40ms), touch gesture detection with 50px threshold
- **Performance**: CSS `will-change: transform` for smooth scaling, passive event listeners
- **Navigation Logic**: Circular navigation with hash-based state persistence

### Key JavaScript Functions
- **`show(n)`**: Core navigation function with hash update
- **`scaleAll()`**: Responsive scaling for all slide frames
- **`fromHash()`**: Deep-link initialization and hash change handling

### Styling Architecture
- **CSS Grid Layout**: Centered slide positioning with `display: flex; align-items: center; justify-content: center`
- **Fixed Positioning**: All UI controls use `position: fixed` for overlay behavior
- **Transform Scaling**: CSS `transform: scale()` applied to iframe elements for crisp scaling

### Maintenance
- Test scaling across different screen sizes and orientations
- Verify touch gesture sensitivity on various devices
- Monitor CDN availability for external dependencies
- Validate Korean text rendering across different systems