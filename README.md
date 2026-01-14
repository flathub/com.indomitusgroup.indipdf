# indiPDF - PDF Editor for Linux

A powerful, native PDF editor application for Linux, built with Tauri, Vue 3, TypeScript, and pdf-lib.

## Features

### File Operations
- **Open & Save**: Open, edit, and save PDF documents
- **Save As**: Save copies with new names
- **Save & Flatten**: Permanently embed annotations into PDFs
- **Print**: Print documents with full annotation support and page selection
- **Merge PDFs**: Combine multiple PDF files into one
- **Split PDFs**: Extract page ranges into separate documents
- **Add Pages**: Insert pages from other PDFs into the current document
- **Recent Files**: Quick access to recently opened documents
- **Multi-tab Interface**: Work with multiple documents simultaneously

### Page Management
- **Drag-and-drop Reordering**: Easily reorganize pages via sidebar thumbnails
- **Page Rotation**: Rotate individual pages (persists on save)
- **Page Deletion**: Remove unwanted pages
- **Extract Pages**: Save specific pages as new documents

### Annotations & Markup
- **Highlight, Underline, Strikethrough**: Text markup tools with color selection
- **Text Annotations**: Add text boxes anywhere on the page
- **Rich Text Formatting**: Font family, size, and color customization
- **Comment Annotations**: Add comments with text selection highlighting
- **Link Annotations**: Create hyperlinks from text selections
- **Freehand Drawing**: Draw freely with customizable colors and widths
- **Eraser Tool**: Remove portions of freehand drawings
- **Shapes**: Rectangles, circles, lines, and arrows
- **Stamps & Images**: Add images and stamp annotations
- **Signature Support**: Create, save, and apply digital signatures

### Editing Features
- **Form Filling**: Work with fillable PDF forms
- **Calculated Fields**: Support for PDF form calculations (SUM, AVG, etc.)
- **Document Metadata**: Edit PDF title, author, subject, and other metadata
- **Undo/Redo**: Full undo and redo support for all operations
- **Copy/Paste**: System clipboard and in-app clipboard support
- **Clipboard History**: Sidebar panel showing clipboard history

### Navigation & Search
- **Full-text Search**: Search within PDF documents with error feedback
- **Search Navigation**: Find next/previous occurrences (Ctrl+G / Ctrl+Shift+G)
- **Zoom Controls**: Zoom in, out, and fit-to-width
- **Default Zoom**: Set your preferred default zoom level
- **Sidebar Thumbnails**: Visual page navigation with drag reordering

### User Experience
- **Dark/Light Theme**: Automatic system theme detection (GNOME, KDE, GTK, XDG Portal)
- **GTK-style Interface**: Native Linux look and feel
- **Keyboard Shortcuts**: Comprehensive keyboard navigation
- **Unsaved Changes Protection**: Prompts before closing modified documents
- **File Association**: Double-click PDF files to open in indiPDF

### Licensing
- **Free to Use**: Full functionality without time limits
- **Watermark System**: Unlicensed copies add a watermark to saved files
- **Smart Detection**: Recognizes already-watermarked documents
- **License Activation**: Purchase a license to save files without watermarks
- **In-app Purchase**: Buy directly from Help menu via secure Stripe checkout
- **Ed25519 Verification**: Cryptographically secure license validation

## Installation

### Flatpak (Recommended)
```bash
flatpak install flathub com.indomitusgroup.indipdf
```

### From Source
See Development section below.

## Technology Stack

- **Frontend**: Vue 3 + TypeScript + Vite
- **State Management**: Pinia
- **Backend**: Tauri 2 (Rust)
- **PDF Rendering**: PDF.js
- **PDF Manipulation**: pdf-lib (frontend), lopdf (backend)
- **UI Icons**: Lucide Vue
- **Drag & Drop**: vuedraggable
- **Licensing**: Ed25519 cryptographic signatures

## Prerequisites

- Node.js 18+
- Rust 1.70+
- Linux system dependencies for Tauri:
  ```bash
  # Ubuntu/Debian
  sudo apt update
  sudo apt install libwebkit2gtk-4.1-dev build-essential curl wget file libxdo-dev libssl-dev libayatana-appindicator3-dev librsvg2-dev

  # For printing support
  sudo apt install cups libcups2-dev
  ```

## Development

```bash
# Install dependencies
npm install

# Run in development mode
npm run tauri dev

# Build for production
npm run tauri build
```

## Project Structure

```
indiPDF/
├── src/                    # Frontend Vue application
│   ├── components/         # Vue components
│   │   ├── PDFViewer.vue   # Main PDF viewing/editing component
│   │   ├── Toolbar.vue     # Annotation toolbar
│   │   ├── MenuBar.vue     # Application menu
│   │   ├── Sidebar.vue     # Thumbnails and clipboard
│   │   ├── LicenseModal.vue # License management
│   │   └── ...
│   ├── stores/             # Pinia state management
│   │   ├── appStore.ts     # Application state
│   │   └── licenseStore.ts # License management
│   ├── types/              # TypeScript type definitions
│   ├── utils/              # Utility functions
│   │   ├── pdfUtils.ts     # PDF operations
│   │   └── fileUtils.ts    # File handling
│   ├── App.vue             # Main application component
│   └── main.ts             # Application entry point
├── src-tauri/              # Tauri backend (Rust)
│   ├── src/
│   │   └── lib.rs          # Rust commands and PDF operations
│   ├── Cargo.toml          # Rust dependencies
│   └── tauri.conf.json     # Tauri configuration
├── flatpak/                # Flatpak packaging
│   ├── com.indomitusgroup.indipdf.yml  # Flatpak manifest
│   └── prepare-release.sh  # Release preparation script
├── index.html              # HTML entry point
├── package.json            # Node.js dependencies
└── vite.config.ts          # Vite configuration
```

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+O` | Open file |
| `Ctrl+S` | Save file |
| `Ctrl+Shift+S` | Save As |
| `Ctrl+P` | Print |
| `Ctrl+W` | Close document |
| `Ctrl+F` | Find/Search |
| `Ctrl+G` | Find next |
| `Ctrl+Shift+G` | Find previous |
| `Ctrl+Z` | Undo |
| `Ctrl+Shift+Z` / `Ctrl+Y` | Redo |
| `Ctrl++` | Zoom in |
| `Ctrl+-` | Zoom out |
| `Ctrl+0` | Fit to width |
| `Ctrl+R` | Rotate page |
| `Ctrl+M` | Toggle comment tool |
| `F9` | Toggle sidebar |

## Roadmap

### Completed
- [x] Full annotation support with selection and editing
- [x] Print support with page selection
- [x] Undo/redo functionality
- [x] Keyboard shortcuts
- [x] Dark/light theme detection
- [x] Comment annotations with text highlighting
- [x] Multi-tab document support
- [x] Link annotations
- [x] Rich text formatting
- [x] Form field calculations
- [x] Document metadata editing
- [x] Recent files
- [x] System clipboard integration
- [x] Flatpak packaging
- [x] In-app license purchase
- [x] Text editing within existing PDF text

### Planned
- [ ] OCR support via external tools
- [ ] Cloud storage integration
- [ ] PDF/A compliance
- [ ] Digital certificate signatures

## License

Proprietary - See license terms at [indomitusgroup.com/indipdf/indipdf-license](https://indomitusgroup.com/indipdf/indipdf-license/)

## Support

For bug reports and feature requests, visit [indomitusgroup.com/indipdf/indipdf-bug-report/](https://indomitusgroup.com/indipdf/indipdf-bug-report/)

To purchase a license, visit [indomitusgroup.com](https://www.indomitusgroup.com) or use Help > Buy indiPDF in the application.
