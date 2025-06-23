# ASCII Art SVG Generator

A modern web application for creating ASCII art from text and exporting it as SVG files.

## Features

- 🎨 **Real-time ASCII Art Generation** - Type text and see ASCII art instantly
- 🔤 **Multiple Font Styles** - 33+ different ASCII art fonts to choose from
- ⚡ **Quick Font Navigation** - Use arrow keys (↑/↓) or buttons to quickly switch fonts
- 📥 **SVG Export** - Export your ASCII art as high-quality SVG vector files
- 📱 **Responsive Design** - Works perfectly on desktop and mobile devices
- 🎯 **User-Friendly Interface** - Clean, modern design with helpful tooltips

## Technologies Used

- **Vue 3** - Progressive JavaScript framework with Composition API
- **Vite** - Fast build tool and development server
- **TailwindCSS** - Utility-first CSS framework for styling
- **TypeScript** - Type-safe JavaScript development
- **figlet.js** - ASCII art text generator library

## Getting Started

### Prerequisites

- Node.js 18+ and npm

### Installation

1. Install dependencies:
```sh
npm install
```

2. Start the development server:
```sh
npm run dev
```

3. Open your browser and navigate to `http://localhost:5173`

## Usage

1. **Enter Text**: Type your desired text in the input field
2. **Choose Font**: Select a font from the dropdown or use the Previous/Next buttons
3. **Quick Navigation**: Use ↑/↓ arrow keys to quickly switch between fonts
4. **Export**: Click "Export as SVG" to download your ASCII art as an SVG file

## Keyboard Shortcuts

- `↑` (Up Arrow): Switch to previous font
- `↓` (Down Arrow): Switch to next font

## Available Fonts

The application includes 33+ ASCII art fonts including:
- Standard, Big, Block, Bubble
- Digital, Doom, Ghost, Graffiti
- Isometric, Lean, Letters, Roman
- Slant, Speed, Thick, Twisted
- And many more!

## Development Commands

### Compile and Hot-Reload for Development
```sh
npm run dev
```

### Type-Check, Compile and Minify for Production
```sh
npm run build
```

### Lint with ESLint
```sh
npm run lint
```

## Features Comparison

This application improves upon existing ASCII art generators by:

- ✅ **Quick font switching** with arrow keys (no need to repeatedly open/close menus)
- ✅ **SVG export support** for vector graphics (perfect for designers)
- ✅ **Modern, responsive interface** that works on all devices
- ✅ **Real-time preview** with instant feedback
- ✅ **Font counter** showing current selection (e.g., "Font 5/33")

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## License

This project is licensed under the MIT License.
