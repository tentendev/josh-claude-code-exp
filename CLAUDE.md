# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains production-ready HTML landing pages and email newsletter templates. All files are **self-contained** with inline CSS, requiring no build process or external dependencies (except Google Fonts).

**Key characteristic**: Files are designed to be copy-paste ready for deployment to any platform (web hosting, Mailchimp, email clients, etc.)

## Repository Structure

### Production Files (Root Directory)

- **`esen_mitochondrial_webflow_landing_2025-11-05.html`** - ĒSEN Medical landing page
  - Target client: https://www.esenmedical.com/
  - Language: Traditional Chinese (zh-TW)
  - CRO-optimized with Problem-Agitate-Solution framework
  - Conversational tone with personal pronouns and rhetorical questions

- **`neteon_newsletter_mailchimp_2025-11-05.html`** - Neteon AI newsletter
  - Mailchimp-compatible email template
  - Table-based layout for email client compatibility
  - Inline CSS required for email rendering

### Reference Materials

- **`/ref`** - Design screenshots and visual references
  - Source materials for recreating designs
  - Client brand guidelines and examples

- **`/code-ref`** - Webflow template library
  - Complete Webflow component system
  - Reusable layouts: `basic-layouts.html`, `inspired-layouts.html`, `components.html`
  - Styling system: `/css/esen-proposal-official.webflow.css`
  - ĒSEN brand assets in `/images`

## HTML File Architecture

### Design Principles

1. **Self-Contained Structure**
   - All CSS embedded in `<style>` tags within `<head>`
   - Minimal JavaScript inline for interactivity (FAQ accordions, smooth scrolling)
   - No external stylesheets or scripts except Google Fonts

2. **CSS Architecture**
   - CSS Custom Properties (variables) in `:root` for theming
   - Mobile-first responsive design with `@media` queries
   - Utility classes prefixed with component names (e.g., `.hero-`, `.btn-`, `.section-`)

3. **Responsive Grid System**
   - CSS Grid for major layouts (`grid-template-columns: repeat(auto-fit, minmax(...)`)
   - Flexbox for component-level alignment
   - Breakpoint: `@media (max-width: 768px)` for mobile

### Typography System

**Font Stack**:
- Primary: `'Noto Sans TC'` (body text, Chinese characters)
- Display: `'Noto Serif TC'` (headings)
- Secondary: `'Inter'` (English text)
- Fallback: `-apple-system, BlinkMacSystemFont, sans-serif`

**Font Loading**: Google Fonts via WebFont.js for performance and FOUT prevention

### Color Naming Convention

Variables use semantic naming:
- `--color-primary` - Main brand color
- `--color-secondary` - Supporting brand color
- `--color-accent` - Call-to-action highlights
- `--color-bg-light` / `--color-bg-dark` - Background variations
- `--color-text` / `--color-text-light` - Text hierarchy

## Content Strategy Patterns

### ĒSEN Landing Page Framework

**Structure follows CRO best practices**:
1. Hero Section - Value proposition with dual CTA
2. Problem Section - 6 pain points with emoji icons
3. Solution Section - Educational content about mitochondrial health
4. Benefits Section - 6 numbered outcomes
5. Process Section - 4-step timeline with visual indicators
6. Testimonials - Social proof with role/context
7. FAQ Section - Interactive accordion for objection handling
8. CTA Section - Final conversion push with urgency

**Copywriting Style**:
- Conversational tone ("累了嗎？" - "Tired yet?")
- Personal pronouns (你/我們)
- Rhetorical questions for engagement
- Analogies (粒線體 = 細胞發電廠)
- Active voice, brief paragraphs
- Emojis for visual breaks and emotional connection

### Email Newsletter Structure

**Mailchimp Compatibility Requirements**:
- Table-based layout (not CSS Grid/Flexbox for main structure)
- Inline CSS on all elements
- Max width: 600-650px for email clients
- Web-safe fonts with fallbacks
- Absolute URLs for all images (when deployed)

## File Naming Convention

Pattern: `[brand]_[content-type]_[framework]_[purpose]_[date].html`

Examples:
- `esen_mitochondrial_webflow_landing_2025-11-05.html`
- `neteon_newsletter_mailchimp_2025-11-05.html`

Date format: `YYYY-MM-DD`

## Creating New Landing Pages

### When using `/code-ref` templates:

1. **Extract component patterns** from:
   - `basic-layouts.html` - Section structures, grid systems
   - `components.html` - Buttons, cards, forms
   - `styles.html` - Typography and spacing utilities

2. **Preserve Webflow CSS conventions**:
   - Grid system with `.row` / `.col` classes
   - Utility classes (`.u-mb-0`, `.u-text-center`)
   - Component naming (`.btn-primary`, `.card-body`)

3. **Copy inline, not link**:
   - Extract CSS from `/css/esen-proposal-official.webflow.css`
   - Embed in new file's `<style>` tag
   - Remove unused classes for file size optimization

### Brand-Specific Customization

**ĒSEN Medical Brand**:
- Colors: Green palette (#2D5F4C primary, #7FA68D secondary, #D4A574 accent)
- Fonts: Noto Serif TC for headings, Noto Sans TC for body
- Tone: Medical professionalism with conversational warmth
- Cultural: Traditional Chinese (Taiwan) localization

**Neteon AI Brand**:
- Colors: Bold, venture capital aesthetic (purple gradients, vibrant accents)
- Fonts: Inter, strong geometric sans-serif
- Tone: Tech-forward, innovative, professional
- Attribution: Link to https://neteon.ai/ in footer

## Deployment Workflow

### For Landing Pages (Direct Hosting)
1. File is production-ready as-is
2. Upload to web host or CDN
3. Update any placeholder images/content
4. Test responsive breakpoints

### For Email Newsletters (Mailchimp)
1. Copy entire HTML content
2. Paste into Mailchimp's "Code Your Own" template editor
3. Replace image URLs with absolute CDN paths
4. Send test email to verify rendering across clients
5. Check: Gmail, Outlook, Apple Mail, Yahoo Mail

## Browser/Client Support Testing

**Landing Pages**: Chrome, Firefox, Safari, Edge (latest), Mobile browsers
**Email Templates**: Gmail, Outlook (desktop/web), Apple Mail, Mailchimp preview

## Common Modifications

### Changing Colors
Update CSS custom properties in `:root`:
```css
:root {
  --color-primary: #NEW_COLOR;
  --color-secondary: #NEW_COLOR;
  --color-accent: #NEW_COLOR;
}
```

### Adding Sections
1. Copy section structure from `/code-ref/basic-layouts.html`
2. Maintain `.section` wrapper with `.container` inside
3. Follow existing spacing patterns (`padding: var(--spacing-xl) 0`)
4. Ensure mobile breakpoint styles

### Localizing Content
- Preserve Chinese typography settings (`lang="zh-TW"`)
- Maintain `'Noto Sans TC'` / `'Noto Serif TC'` for Chinese characters
- Keep line-height at 1.7+ for Chinese readability

## Performance Considerations

- **Inline CSS**: Increases HTML size but eliminates render-blocking requests
- **Google Fonts**: Only external dependency, loaded asynchronously via WebFont.js
- **Images**: Use placeholders in templates, replace with optimized WebP/AVIF in production
- **JavaScript**: Minimal vanilla JS, no frameworks required

## Quality Checklist for New Files

- [ ] All CSS is inline (no external stylesheets except fonts)
- [ ] Responsive design tested at 320px, 768px, 1200px+ widths
- [ ] Meta tags include title, description, OG tags, Twitter cards
- [ ] Language attribute matches content (`lang="zh-TW"` or `lang="en"`)
- [ ] Footer includes proper attribution (client brand + Neteon AI credit)
- [ ] CTAs are clearly visible and functional
- [ ] FAQ accordion works without errors
- [ ] Smooth scroll navigation functions properly
- [ ] File naming follows convention: `brand_type_framework_purpose_date.html`
