# Vue Banner Component Case Study

A responsive banner component system built with Vue 3 and Vite, featuring adaptive layouts and mobile-first carousel functionality.

## Project Overview

This project implements a versatile banner component that supports:
- **Square mode**: Grid-based layout with carousel option on mobile
- **Rectangle mode**: Full-width background images with overlaid CTAs
- **Responsive design**: Adaptive layouts for desktop and mobile devices
- **Component architecture**: Modular Vue 3 components with props-based configuration

## Features

### Banner Modes
1. **Square Mode**: Displays content in a 3-column grid (desktop) or single-column (mobile)
   - Optional carousel functionality on mobile devices
   - Support for both image and CTA components
   - Thumbnail navigation for carousel slides

2. **Rectangle Mode**: Full-width banner with background images
   - Desktop: Large background image with overlaid CTA
   - Mobile: Stacked layout with square image and CTA

### Technical Implementation
- **Vue 3 Composition API**: Using `<script setup>` syntax for modern Vue development
- **Responsive Design**: CSS Grid and Flexbox with mobile-first approach
- **Media Query Integration**: JavaScript `matchMedia` API for responsive behavior
- **Component Props**: Flexible configuration through Vue props system

## Component Structure

```
src/
├── components/
│   ├── BannerComponent.vue    # Main banner component
│   ├── BannerImage.vue        # Image display component
│   └── BannerCTA.vue          # Call-to-action component
├── styles/
│   └── globals.css            # Global styles and CSS variables
└── App.vue                    # Main application with demo data
```

## Development Process & Thought Process

### Research Phase
1. **Vue + Vuetify Documentation**: Studied carousel implementations and component prop patterns
2. **YouTube Tutorials**: Researched mobile responsiveness best practices
3. **Technical Documentation**: Explored Vue 3 Composition API and lifecycle hooks

### Implementation Challenges & Solutions

#### 1. Mobile Responsiveness
**Challenge**: Creating truly responsive components that adapt to different screen sizes
**Solution**:
- Implemented JavaScript-based media query detection using `matchMedia` API
- Used CSS Grid with fallbacks and responsive breakpoints
- Applied mobile-first design principles

#### 2. Vuetify Installation Issues
**Challenge**: Difficulties with Vuetify setup and limited helpful tutorials
**Solution**:
- Pivoted to vanilla CSS implementation with CSS variables
- Created custom responsive grid system
- Implemented carousel functionality without external carousel library

#### 3. Lifecycle Management
**Challenge**: Understanding Vue 3's `onMounted` and `onUnmounted` hooks
**Process**:
- Initial research on Vue lifecycle hooks
- AI assistance for implementing media query listeners
- Testing and iteration to understand proper cleanup patterns

#### 4. Carousel Thumbnails
**Challenge**: Implementing thumbnail navigation for carousel
**Process**:
- AI assistance for scroll-based navigation logic
- Custom implementation using `scrollIntoView` API
- Manual testing and refinement for smooth behavior

### AI-Assisted Development

#### Global Styling (styles/globals.css)
**Process**:
- Provided Banner component documentation to Claude AI
- Requested global styling recommendations with mobile responsiveness
- Iteratively built upon AI-generated foundation
- Customized and refined styles based on project needs

**AI Contributions**:
- CSS variable system for consistent theming
- Responsive grid layouts
- Aspect ratio utilities
- Mobile-responsive breakpoints

#### Technical Implementation Support
- **Media Query Integration**: AI guidance on `matchMedia` API usage
- **Carousel Logic**: AI-generated scroll navigation functions
- **Component Architecture**: AI recommendations for Vue component structure

### Key Technical Decisions

1. **No External UI Framework**: Chose vanilla CSS over Vuetify for better control and learning
2. **Composition API**: Used Vue 3's modern `<script setup>` syntax throughout
3. **Mobile-First**: Designed for mobile devices first, then enhanced for desktop
4. **Modular Components**: Separated concerns into distinct, reusable components
5. **CSS Variables**: Implemented theming system for consistent styling

## Getting Started

### Prerequisites
- Node.js (latest LTS)
- npm or yarn

### Installation
```bash
npm install
```

### Development
```bash
npm run dev
```

### Build
```bash
npm run build
```

## Dependencies
- **Vue 3**: Modern JavaScript framework
- **Vite**: Fast build tool and development server
- **Swiper**: Carousel functionality (if needed for future enhancements)
