# Dofus Ingame Library - Bilingual HTML Explorer

A standalone, memory-optimized HTML application for viewing and searching Dofus game documents in multiple languages with bilingual support.

## Features

### 1. **Lazy Loading & Memory Optimization**
- ✅ Initial load shows only the document index (no content displayed)
- ✅ Documents are loaded on-demand when selected from the sidebar
- ✅ IndexedDB caching: subsequent page reloads use cached data (no API calls)
- ✅ Images load only on mouse hover over documents

### 2. **Language & View Modes**
- ✅ Single-language mode (default): Spanish, English, French, Portuguese, German
- ✅ Bilingual mode: side-by-side column view with synchronized scrolling
- ✅ Second language selector when in bilingual mode (exclude current language)
- ✅ Bilingual titles appear within each language column (not above)

### 3. **Search & Navigation**
- ✅ Real-time search across all documents
- ✅ Keyboard shortcuts: Ctrl+F (focus search), Escape (clear search)
- ✅ Search highlighting with yellow background
- ✅ Click index items to load and view documents

### 4. **Image Handling**
- ✅ Auto-converts `##png,ID##` format to actual image URLs
- ✅ Images from: `https://api.e-bou.fr/img/unity/UI/documents/`
- ✅ Lazy-loading: images only load when hovering over the document

### 5. **Responsive Design**
- ✅ Collapsible sidebar (hamburger menu)
- ✅ Mobile-friendly layout
- ✅ Synchronized scrolling in bilingual mode

## File Structure

```
d3-library/
├── index.html              # Main application (all-in-one)
├── config.json             # Optional: configuration file (for reference)
├── README.md               # This file
└── Dofus_ingame_library_bilingual_html_export.ipynb
```

## Configuration

The configuration is **embedded directly in `index.html`** to avoid CORS issues when opening files locally.

If you need to modify settings, edit the `config` object in the `<script>` section of `index.html`:

```javascript
let config = {
  "api": {
    "baseUrl": "https://api.beta.dofusdb.fr",
    "endpoints": { "documents": "/documents" },
    "defaultLimit": 50
  },
  "ui": {
    "defaultLanguage": "es",
    "supportedLanguages": ["en", "fr", "es", "pt", "de", "it"]
  },
  "features": {
    "imageProcessing": true,
    "imageBaseUrl": "https://api.e-bou.fr/img/unity/UI/documents/"
  }
}
```

**Note:** `config.json` is provided for reference but is not loaded by the app due to CORS restrictions when using the `file://` protocol.

## Usage

1. Open `index.html` in a modern web browser
2. Browse the document index on the left sidebar
3. Click any document title to load and view its content
4. Use language buttons to switch primary language
5. Toggle "Bilingual" to switch between single and dual-column view
6. In bilingual mode, use "Second language:" buttons to choose the second language

## Technical Details

### Caching Strategy
- **IndexedDB**: Stores fetched documents locally
- **On First Load**: Fetches from API and caches
- **On Subsequent Loads**: Reads from cache (instant loading)
- **No Cache Expiry**: Documents persist until manually cleared

### Image Loading
- Images converted from `##format,ID##` to actual URLs
- Lazy-loaded on document hover to save bandwidth
- Placeholder src="" until hover event

### Synchronized Scrolling
- Works in bilingual mode using percentage-based sync
- Maintains alignment between different-length content
- Disabled when switching languages or view modes

### Memory Optimization
- Only visible documents rendered in DOM
- Single document displayed at a time (on-demand)
- Images lazy-loaded on hover
- Reuses cache on page reload

## Browser Compatibility

- Chrome/Edge 88+
- Firefox 85+
- Safari 14+
- Requires IndexedDB support for caching

## Known Limitations

- First API call required to populate cache
- Search operates on cached documents only
- Bilingual mode title position (in-column) differs from single-language header

## Future Enhancements

- Pagination for large result sets
- Advanced filtering by document class
- Offline service worker support
- Export documents to PDF
- User preferences persistence

---

Last updated: November 25, 2025
