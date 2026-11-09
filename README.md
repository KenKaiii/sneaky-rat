# Element Copier - Chrome Extension

A modern Chrome extension that lets you copy any HTML element from any website with its computed styles, perfectly formatted for LLM consumption or code reuse.

> [!TIP]
> **Want to build your own apps with AI?** A free 7-day build challenge and 20+ step-by-step projects are in my free community: **[skool.com/raid](https://www.skool.com/raid)**

## Features

- **Smart Hover Detection** - Hover over any element on any website to highlight it
- **Intelligent Style Reduction** - Automatically removes bloat and keeps only visually significant styles
  - Filters out default browser styles
  - Removes tracking attributes and framework-specific data
  - Eliminates redundant vendor prefixes
  - Optimizes to CSS shorthands where possible
  - **Typical reduction: 70-90% of computed styles**
- **Asset Resolution** - Automatically extracts and lists images, fonts, and background images
- **Pseudo-element Support** - Optionally include `::before` and `::after` styles
- **LLM-Optimized Output** - Clean, commented output format perfect for pasting into Claude, ChatGPT, etc.
- **Clipboard Integration** - One-click copy to clipboard

## Installation & Development

1. Install dependencies:
```shell
npm install
```

2. Start development server:
```shell
npm run dev
```

3. Load the extension in Chrome:
   - Open `chrome://extensions/`
   - Enable "Developer mode"
   - Click "Load unpacked"
   - Select the `build/` directory

## Production Build

```shell
npm run build
```

The extension will be built to the `build/` directory, ready for the Chrome Web Store.

## Usage

1. **Activate** - Click the extension icon and press "Activate"
2. **Hover** - Move your mouse over any element on the page
3. **Copy** - Click the blue "Copy" button that appears
4. **Paste** - Paste into your LLM, code editor, or anywhere

Press **ESC** to deactivate.

## Options

- **Include Assets** - Extract image URLs and font families
- **Aggressive Style Reduction** - Remove inherited styles (even more reduction)
- **Include Pseudo-elements** - Capture `::before` and `::after` styles

## Tech Stack

Built with 2025 best practices:
- **Vite** - Fast build tool with HMR
- **React 18** + **TypeScript**
- **Manifest V3** - Latest Chrome extension API
- **@crxjs/vite-plugin** - Seamless extension development

## How It Works

### Style Reduction Algorithm

The `StyleReducer` applies intelligent filtering:
- **Default Value Filtering** - Removes browser defaults
- **Conditional Property Analysis** - Removes irrelevant properties
- **Vendor Prefix Cleanup** - Removes unnecessary prefixes
- **Shorthand Optimization** - Converts to CSS shorthands
- **Inheritance Matching** - Optionally removes parent-matched values

### Example Output

```html
<!-- Extracted Element -->
<!-- Styles reduced: 347 → 12 (96% reduction) -->

<button class="primary-button">Click Me</button>

<style>
.extracted-1234 {
  display: inline-flex;
  padding: 12px 24px;
  background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
  border-radius: 8px;
  font-size: 14px;
}
</style>
```

## Project Structure

```
element-copier/
├── src/
│   ├── lib/
│   │   ├── styleReducer.ts       # Smart CSS reduction
│   │   ├── elementExtractor.ts   # Element extraction
│   │   └── assetResolver.ts      # Asset URL extraction
│   ├── contentScript/            # Hover detection & copying
│   ├── popup/                    # Extension UI
│   └── manifest.ts
└── build/                        # Built extension
```

## License

MIT

---

Generated with [create-chrome-ext](https://github.com/guocaoyi/create-chrome-ext)
