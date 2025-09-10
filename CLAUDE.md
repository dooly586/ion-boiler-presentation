# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a multilingual presentation website for 이온히팅보일러 (Ion Heating Boiler) technology showcase. It features a language-selection landing page that routes to localized fullscreen presentation systems in Korean and English, demonstrating the technology, performance metrics, and case studies.

## Architecture

### Core Structure
- **index.html** - Language selection landing page with animated interface and hidden speaker access
- **ko/** - Korean presentation system (7 slides)
  - **ko/index.html** - Korean fullscreen presentation controller
  - **ko/page_1.html to page_7.html** - Individual Korean presentation slides
- **en/** - English presentation system (6 slides) 
  - **en/index.html** - English fullscreen presentation controller
  - **en/page_1.html to page_6.html** - Individual English presentation slides
- **gallery.html** - Full-screen image slideshow with installation photos
- **gallery-grid.html** - Grid-based photo gallery with modal lightbox
- **image_installation/** - Directory containing installation photos
- **scripts/** - Multilingual speaker presentation scripts system
  - **ko/** - Korean presentation scripts (28 files total)
    - **slide_1_script.txt to slide_7_script.txt** - Korean presentation scripts for each slide (full versions)
    - **slide_N_short.txt, slide_N_medium.txt, slide_N_long.txt** - Multiple script length variants for each slide
  - **en/** - English presentation scripts (24 files total)
    - **slide_1_script.txt to slide_6_script.txt** - English presentation scripts for each slide (full versions)
    - **slide_N_short.txt, slide_N_medium.txt, slide_N_long.txt** - Multiple script length variants for each slide
  - **script-viewer.html** - Main presentation script viewer with language selection (popup window)
  - **script-selector.html** - Alternative script selection interface
- **Responsive Scaling System** - Automatic scaling to fit any screen size while maintaining 1280x720 aspect ratio

### Key Components

#### Language Landing Page (index.html)
- **Language Selection**: Animated interface for choosing Korean or English
- **Corporate Branding**: Ion Heating Boiler logo and company information
- **Gallery Access**: Direct links to slideshow and grid gallery views
- **Hidden Speaker Access**: Secret presentation script access for speakers (Korean presentation only)
  - **Activation**: `Ctrl + Shift + S` keyboard shortcut or triple-click logo
  - **Popup Script Viewer**: Opens scripts/script-selector.html in optimized popup window
  - **Clean Presentation**: No visible UI elements for screen sharing in meetings
- **Responsive Design**: Mobile-optimized with fade-in animations
- **Navigation**: Routes to `/ko/index.html`, `/en/index.html`, `gallery.html`, and `gallery-grid.html`

#### Presentation Systems (ko/index.html, en/index.html)
- **Fullscreen Display**: Slides scale to fit viewport while preserving 1280x720 aspect ratio
- **Overlay Navigation**: Floating controls that don't interfere with slide content
- **Multi-Input Navigation**: Arrow keys, mouse wheel, touch gestures, keyboard shortcuts
- **Deep Linking**: Hash-based URL navigation (#p=1, #p=2, etc.)
- **Language Switching**: Cross-language navigation between Korean and English versions
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

#### Gallery Systems (gallery.html, gallery-grid.html)
- **Full-Screen Slideshow**: gallery.html provides immersive photo viewing experience
- **Grid Gallery**: gallery-grid.html offers overview with modal lightbox functionality
- **Installation Photos**: Showcases real-world boiler installations and case studies
- **Navigation Controls**: Keyboard, touch, and mouse navigation support
- **Responsive Design**: Optimized for both desktop and mobile viewing

#### Speaker Presentation System (scripts/script-viewer.html + scripts/)
- **Multilingual Script Viewer**: Dedicated window for Korean and English presentation scripts
- **Language Toggle**: Real-time switching between Korean and English scripts with 🌐/🇰🇷 button
- **Multiple Script Lengths**: Short, medium, long, and full versions for each slide
- **Script Library**: 28 Korean scripts (7 slides × 4 versions) + 24 English scripts (6 slides × 4 versions)
- **Automatic Slide Mapping**: Korean slide 7 → English slide 6 automatic mapping
- **Presentation Tools**: Built-in timer, font size control, dark mode toggle
- **Multi-Modal Navigation**: Keyboard arrows, tab buttons, touch swipe support
- **Script Selection Interface**: Alternative selector (script-selector.html) for choosing script variants
- **Optimized for Screen Sharing**: Designed for Google Meet/Zoom tab sharing workflows
- **Auto-Positioning**: Popup opens on screen right to avoid overlapping shared content

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
- **Landing Page**: Test language selection buttons, responsive design, gallery access buttons
- **Speaker Access**: Test `Ctrl + Shift + S` and logo triple-click for script viewer access (Korean presentation only)
- **Presentations**: 
  - **Arrow Keys**: ← → for navigation within presentations
  - **Special Keys**: Home (first slide), End (last slide), Space (next slide)
  - **Mouse Wheel**: Scroll up/down to navigate
  - **Touch Gestures**: Swipe left/right or up/down
  - **Deep Links**: Test `#p=1` through `#p=7` (Korean), `#p=1` through `#p=6` (English)
  - **Language Switching**: Test language switcher in presentation overlay
- **Script Viewer**:
  - **Popup Opening**: Verify popup opens in correct position (screen right, 600x800px)
  - **Script Loading**: Confirm all 52 script files load correctly from scripts/ directory (28 Korean + 24 English)
  - **Language Toggle**: Test real-time switching between Korean and English scripts
  - **Script Variants**: Test short/medium/long/full script versions and selection interface
  - **Slide Mapping**: Verify Korean slide 7 correctly maps to English slide 6
  - **Navigation**: Test keyboard arrows, tab buttons, touch swipe for slide switching
  - **Tools**: Test timer start/stop, font size controls, dark mode toggle
  - **Browser Compatibility**: Ensure popup works across different browsers
- **Gallery Systems**:
  - **Slideshow**: Test keyboard navigation, auto-advance, manual controls
  - **Grid Gallery**: Test thumbnail clicks, modal lightbox, zoom functionality
  - **Mobile Gallery**: Test touch gestures, responsive layout, photo quality
- **Responsive Scaling**: Test different viewport sizes across all components

## Content Structure

### Slide Content Structure

#### Korean Version (ko/, 7 slides)
1. **page_1.html** - Title slide with main branding
2. **page_2.html** - Korean enterprise case studies (현대자동차 아산공장)
3. **page_3.html** - KCL certification test results
4. **page_4.html** - Technical specifications and performance data
5. **page_5.html** - Summary and benefits
6. **page_6.html** - Additional technical details
7. **page_7.html** - Contact information and conclusion

#### English Version (en/, 6 slides)  
1. **page_1.html** - Title slide with main branding
2. **page_2.html** - Enterprise case studies
3. **page_3.html** - Certification and test results
4. **page_4.html** - Technical specifications
5. **page_5.html** - Performance benefits
6. **page_6.html** - Contact information

#### Multilingual Presentation Scripts (scripts/ko/, scripts/en/, 52 files total)

**Korean Scripts (28 files)** - Each slide has 4 script variants (full, short, medium, long):
1. **slide_1_script.txt + variants** - Company introduction and technology overview
2. **slide_2_script.txt + variants** - Hyundai Motor Asan Plant and other enterprise case studies
3. **slide_3_script.txt + variants** - CES 2025 Innovation Award achievement
4. **slide_4_script.txt + variants** - Heating system performance comparison data explanation
5. **slide_5_script.txt + variants** - Core technology features and benefits
6. **slide_6_script.txt + variants** - Additional technical specifications and ion heating technology
7. **slide_7_script.txt + variants** - Demonstration test proposal and Q&A session transition

**English Scripts (24 files)** - Professional translations for international presentations:
1. **slide_1_script.txt + variants** - Company introduction and technology overview
2. **slide_2_script.txt + variants** - Hyundai Motor case studies and enterprise implementations
3. **slide_3_script.txt + variants** - CES 2025 Honoree Award recognition
4. **slide_4_script.txt + variants** - KCL testing results and performance validation
5. **slide_5_script.txt + variants** - Core technology principles and advantages
6. **slide_6_script.txt + variants** - Validation testing proposal and Q&A session transition

### Styling Conventions
- **Typography**: Inter + Noto Sans KR for multilingual support
- **Color Palette**: Primary #009688 (teal), gradients from #e8f5e9 to #e0f2f1
- **Landing Page**: Animated fadeInUp effects, glass morphism buttons
- **Presentation UI**: Fixed positioning overlays, backdrop-filter blur effects
- **Component Classes**: `.title-box`, `.content-card`, `.stat-card`, `.icon-circle`
- **Animation**: CSS transitions, hover transforms, smooth scaling

### Data Visualization
- **D3.js v7**: Used for charts on performance metrics
- **Chart Types**: Bar charts, comparison visualizations
- **Data Format**: Embedded JavaScript objects with Korean labels

## File Management

### Adding New Slides
1. Create new HTML file following existing page structure (1280x720px) in appropriate language directory
2. Add new `.slide-wrap` container with iframe in respective `ko/index.html` or `en/index.html`
3. Update `totEl.textContent = wraps.length` in JavaScript (auto-calculated from DOM)
4. Ensure proper sequencing in DOM order within language-specific presentation
5. Consider adding corresponding slide to other language version for consistency
6. **For new slides**: Create corresponding script files in both language directories:
   - **Korean**: `scripts/ko/slide_N_script.txt`, `slide_N_short.txt`, `slide_N_medium.txt`, `slide_N_long.txt`
   - **English**: `scripts/en/slide_N_script.txt`, `slide_N_short.txt`, `slide_N_medium.txt`, `slide_N_long.txt`
7. **Update Script Viewer**: Language toggle automatically handles new scripts with proper mapping
8. **Translation**: Ensure professional English translations maintain technical accuracy and presentation flow

### Modifying Content
- **Text Updates**: Direct HTML editing in individual page files
- **Styling Changes**: Update embedded `<style>` sections
- **Data Updates**: Modify JavaScript data objects in D3.js sections
- **Image Updates**: Replace external URLs with new sources
- **Script Updates**: Edit corresponding .txt files in both scripts/ko/ and scripts/en/ directories
- **Language-Specific Updates**: Maintain consistency between Korean and English script versions
- **Slide Mapping**: Remember Korean slide 7 maps to English slide 6 for final content

### External Dependencies
- **TailwindCSS**: 2.2.19 via CDN (landing page)
- **Font Awesome**: 6.4.0 via CDN (landing page icons)
- **Google Fonts**: Inter + Noto Sans KR for multilingual typography
- **D3.js**: v7 via CDN for data visualization in slides
- **External Images**: Various sources, ensure CORS compliance

## Browser Compatibility

### Supported Features
- Modern CSS Grid and Flexbox
- ES6+ JavaScript features
- CSS Custom Properties
- Transform and Animation properties

### Fallback Considerations
- Mobile viewport handling at 768px breakpoint (480px for very small screens)
- Touch navigation support with 50px gesture threshold
- Language-specific mobile optimizations (different mobile scaling per language)
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
- Test language selection and navigation between Korean/English versions  
- Test scaling across different screen sizes and orientations on both presentations
- Verify touch gesture sensitivity on various devices
- Monitor CDN availability for external dependencies
- Validate Korean and English text rendering across different systems
- Check language switcher functionality within presentations
- Test deep linking across both language versions
- **Speaker System Maintenance**:
  - Verify script viewer popup functionality across browsers
  - Test speaker access shortcuts (Ctrl+Shift+S, triple-click logo)
  - Validate script file loading from scripts/ko/ and scripts/en/ directories (52 total files)
  - Test language toggle functionality and real-time switching
  - Test script variant selection and switching functionality
  - Verify slide mapping (Korean slide 7 → English slide 6)
  - Check timer accuracy and controls functionality
  - Test presentation workflow with screen sharing tools (Google Meet, Zoom)

## Speaker Presentation Workflow

### Live Presentation Setup
1. **Preparation**: Open Korean presentation (ko/index.html) in browser, ensure popup blockers are disabled
2. **Access Scripts**: Use `Ctrl + Shift + S` or triple-click logo to open script selector popup
3. **Script Selection**: Choose desired script length (short/medium/long) for each slide
4. **Screen Sharing**: Share main browser tab (not entire screen) in Google Meet/Zoom
5. **Clean Interface**: No visible speaker UI elements shown to audience during screen sharing
6. **Navigation**: Use hidden script viewer while navigating presentation with arrow keys or mouse

### Script Viewer Controls
- **Language Toggle**: Switch between Korean and English scripts in real-time with 🌐/🇰🇷 button
- **Script Selection**: Choose between short, medium, long, or full script versions
- **Timer**: Track presentation time with start/stop/reset functionality
- **Font Size**: Adjust readability with +/- controls
- **Dark Mode**: Reduce eye strain during long presentations
- **Slide Sync**: Manually navigate to match current presentation slide with automatic mapping
- **Touch Support**: Swipe gestures for mobile/tablet use
- **Alternative Interface**: Use script-selector.html for different script management approach