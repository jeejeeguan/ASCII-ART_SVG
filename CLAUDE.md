# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an ASCII Art SVG Generator - a Vue 3 web application that converts text into ASCII art using the figlet.js library and exports the results as SVG files. The app features real-time generation, multiple font styles, keyboard shortcuts for font navigation, and responsive design.

## Development Commands

```bash
# Install dependencies
npm install

# Development server with hot reload
npm run dev

# Build for production
npm run build

# Type checking only
npm run type-check

# Lint code with auto-fix
npm run lint

# Format code with prettier
npm run format

# Preview production build
npm run preview
```

## Architecture

### Core Structure
- **Vue 3** with Composition API and TypeScript
- **Vite** build system with hot module replacement
- **Vue Router** for single-page application routing
- **Pinia** for state management (though minimal usage)
- **TailwindCSS** for utility-first styling
- **figlet.js** for ASCII art generation

### Key Components
- `AsciiArtGenerator.vue` - Main component containing all ASCII art generation logic, font selection, keyboard navigation, and SVG export functionality
- `App.vue` - Root component with router outlet
- `HomeView.vue` - Simple wrapper for the main generator component

### Font System
The application supports 33+ ASCII fonts including Standard, Big, Block, Bubble, Digital, Doom, Ghost, Graffiti, and many others. Font navigation is handled through:
- Dropdown selection
- Previous/Next buttons
- Arrow key navigation (↑/↓)

### SVG Export Logic
Located in `AsciiArtGenerator.vue:285-328`, the export functionality:
- Calculates optimal SVG dimensions based on ASCII art content
- Handles XML character escaping
- Uses monospace font styling for consistent character spacing
- Generates downloadable SVG files with sanitized filenames

### Keyboard Shortcuts
- `↑` (Up Arrow): Switch to previous font
- `↓` (Down Arrow): Switch to next font

## File Structure Notes

- Main application logic is consolidated in `AsciiArtGenerator.vue` rather than split across multiple components
- Router configuration is minimal with home and about routes
- CSS styling is primarily handled through TailwindCSS utility classes
- TypeScript configuration spans multiple files (`tsconfig.json`, `tsconfig.app.json`, `tsconfig.node.json`)

## Development Notes

- The app uses `@` alias for `src/` directory imports
- Figlet fonts are hardcoded in the component rather than dynamically loaded
- SVG export creates inline styles for font consistency
- Error handling is implemented for figlet generation failures