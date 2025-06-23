# ASCII Art SVG Generator

A modern web application for creating ASCII art from text and exporting it as high-quality SVG files with advanced pixel-to-shape conversion.

[中文版本](./README_zh.md) | [English Version](./README.md)

## Features

- 🎨 **Real-time ASCII Art Generation** - Type text and see ASCII art instantly
- 🔤 **Massive Font Library** - 295 different ASCII art fonts with dynamic loading
- ⚡ **Quick Font Navigation** - Use arrow keys (↑/↓) or buttons to quickly switch fonts
- 🎛️ **Character Width Control** - Fine-tune spacing with 5 different width options
- 📥 **Advanced SVG Export** - Export with pixel-to-shape conversion for optimal quality
- 🚀 **Dynamic Font Loading** - Fonts load on-demand for better performance
- 📱 **Responsive Design** - Works perfectly on desktop and mobile devices
- 🎯 **User-Friendly Interface** - Clean, modern design with font loading indicators
- 🔄 **Font Status Tracking** - Visual checkmarks show which fonts are loaded

## Technologies Used

- **Vue 3** - Progressive JavaScript framework with Composition API
- **Vite** - Fast build tool and development server with dynamic imports
- **TailwindCSS** - Utility-first CSS framework for styling
- **TypeScript** - Type-safe JavaScript development
- **figlet.js** - ASCII art text generator library with dynamic font loading
- **HTML5 Canvas** - High-resolution rendering for precise SVG conversion

## Getting Started

### Prerequisites

- Node.js 18+ and npm

### Installation

1. Clone the repository:

```sh
git clone https://github.com/jeejeeguan/ASCII-ART_SVG.git
cd ASCII-ART_SVG/ascii-art-svg
```

2. Install dependencies:

```sh
npm install
```

3. Start the development server:

```sh
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

## Usage

1. **Enter Text**: Type your desired text in the input field
2. **Choose Font**: Select from 295 available fonts in the dropdown
3. **Control Width**: Adjust character spacing with width options (Full, Fitted, Smushing, etc.)
4. **Quick Navigation**: Use ↑/↓ arrow keys to quickly switch between fonts
5. **Export**: Click "Export as SVG" to download your ASCII art as an optimized SVG file

## Character Width Options

- **Full**: Maximum character spacing
- **Fitted**: Minimal character spacing
- **Controlled Smushing**: Controlled character overlap with specific rules
- **Universal Smushing**: Universal character overlap rules
- **Default**: Standard figlet spacing

## Keyboard Shortcuts

- `↑` (Up Arrow): Switch to previous font
- `↓` (Down Arrow): Switch to next font

## Font Library

The application includes **295 ASCII art fonts** with dynamic loading, including:

- **Classic Fonts**: Standard, Big, Block, Bubble, Digital, Doom
- **Artistic Fonts**: Ghost, Graffiti, Star Wars, Rammstein, Hollywood
- **Technical Fonts**: Binary, Hex, Morse, Computer, Electronic
- **Decorative Fonts**: Flower Power, Heart Left/Right, Hieroglyphs
- **3D Fonts**: 3-D, 3D Diagonal, Banner3-D, Isometric series
- **Script Fonts**: Cursive, Calvin S, Script, Caligraphy
- **And 270+ more fonts!**

Fonts are loaded dynamically when selected, optimizing initial load time and memory usage.

## Development Commands

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Type-Check Only

```sh
npm run type-check
```

### Lint with ESLint

```sh
npm run lint
```

### Format with Prettier

```sh
npm run format
```

### Preview Production Build

```sh
npm run preview
```

## Advanced Features

### Dynamic Font Loading

- Fonts are loaded on-demand using Vite's dynamic imports
- Initial page load is optimized by loading only essential fonts
- Font loading status is tracked and displayed in the UI
- Supports all 295 figlet fonts with proper error handling

### SVG Export Technology

- **High-Resolution Canvas Rendering**: Uses 2x pixel ratio for accurate measurement
- **Pixel-to-Shape Conversion**: Converts rendered text to optimized SVG rectangles
- **Rectangle Merging Algorithm**: Merges adjacent pixels for optimal file size
- **Anti-aliasing Handling**: Proper threshold detection for smooth edges
- **Automatic Sizing**: SVG dimensions calculated from actual content

### Performance Optimizations

- Lazy loading of font files
- Reactive font status tracking
- Efficient SVG generation with minimal file size
- Responsive UI updates without blocking

## License

This project is licensed under the MIT License.
