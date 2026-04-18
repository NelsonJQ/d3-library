# Dofus Ingame Library - Bilingual HTML Explorer

A standalone, memory-optimized HTML application for viewing and searching Dofus game documents in multiple languages, with bilingual and bisource comparison support.

Access here :

https://nelsonjq.github.io/d3-library/
---

## Features

### 1. **UI Elements and Features**
The application provides a rich and interactive user interface designed for ease of use, comparison workflows, and accessibility. Below are the key UI elements and features:

#### **4 Data Sources**
- The application supports four document sources:
  - **Dofus 3 / DofusDB source**
  - **Dofus Touch source**
  - **Wakfu source**
  - **Islands of Wakfu (IoW) source**
- Users can switch source with the **Source Selector** in the sidebar.
- The selected source is persisted between sessions.

#### **Available Languages**
- The application supports the following languages:
  - **Spanish (ES)** (default)
  - **English (EN)**
  - **French (FR)**
  - **Portuguese (PT)**
  - **German (DE)**
  - **Italian (IT)** (Islands of Wakfu only)
  - **Japanese (JA)** (Islands of Wakfu only)
- Users can switch between these languages using the **Language Selector** in the sidebar.
- Language availability is source-aware (for example, Wakfu has fewer language variants, while IoW adds IT and JA).

#### **Bilingual and Bisource Modes**
- **Single-Language Mode**: Displays content in one selected language.
- **Bilingual Mode**: Displays content side-by-side in two languages, with synchronized scrolling for easy comparison.
  - Users can select a **primary language** and a **secondary language** (excluding the primary language).
  - Titles and subtitles are displayed within each language column.
- **Bisource Comparison Mode**: Compare equivalent documents across the two sources.
  - The app resolves best cross-source matches by normalized titles.
  - Source context is displayed in each document header.
  - Quick compare actions are available directly from document cards.

#### **Islands of Wakfu (IoW) Experience**
- IoW uses a dedicated source with 9 mystery documents from `data/islandswakfu/mysteries.json`.
- IoW exposes a source-specific **All Cards** control that is enabled by default to display all IoW docs in a card grid.
- IoW metadata includes a dedicated CTA block linking to Ankama's game page and Xbox Store.
- IoW documents display **Chibi** as the default author chip.

#### **Dual-Index View and Filters**
- **Dual-Index View**: Displays two synchronized index columns (one per source).
- **Cross-source Selection**: Open a document from either side and jump to its counterpart.
- **Dual-Index Filters**: Filter lists to show all docs, only matched docs, or unmatched docs to quickly inspect coverage differences.

#### **Search and Navigation**
- **Real-Time Search**: Search across all documents with results displayed instantly.
- **Search Highlighting**: Matches are highlighted in yellow within the document content.
- **Diff Highlighting**:
  - **Paragraph-level diff** highlights unmatched blocks between compared documents.
  - **Character-level diff** highlights precise text changes inside matched paragraphs.
- **Keyboard Shortcuts**:
  - `Ctrl+F` (or `Cmd+F`): Focus on the search bar.
  - `Escape`: Clear the search input.
- **Document Index**: A collapsible sidebar lists all available documents. Clicking on a document title loads its content.

#### **Image Handling**
- Converts placeholders like `##png,ID##` into actual image URLs.
- Images are lazy-loaded and only fetched when hovered over, reducing initial load time and memory usage.

#### **Accessibility Features**
- **Theme Toggle (Light/Dark/Retro)**: Switch between three visual themes, including a new retro-inspired style.
- **Font Size Adjustment**: Increase or decrease font size (80% to 150%).
- **Line Height Adjustment**: Adjust line spacing for better readability.
- **Toolbar Visibility**: The accessibility toolbar appears on scroll or mouse movement and hides after a few seconds of inactivity.

#### **Responsive Design**
- Fully responsive layout with a collapsible sidebar for smaller screens.
- Optimized for both desktop and mobile devices.

---

### 2. **Caching Strategy and Memory Optimization**

#### **Caching Strategy**
- The application uses **IndexedDB**, a **NoSQL database** built into modern browsers, to store documents locally.
- **How it works**:
  - On the first load, documents are fetched from the API and cached in IndexedDB.
  - On subsequent loads, the application retrieves documents from the cache, ensuring faster load times and reduced API calls.
  - The cache persists until manually cleared or updated.
- **Source-aware caching**:
  - Dofus 3 data is cached in IndexedDB.
  - Dofus Touch language payloads are managed with runtime cache maps for fast source/language switching.
- **Cache Expiry**:
  - The application checks for new documents daily. If new documents are detected, the cache is updated automatically.

#### **Memory Optimization**
- **Lazy Loading**:
  - Documents are loaded on demand when selected from the sidebar.
  - Images are fetched only when hovered over.
- **Virtual Scrolling**:
  - Only visible content is rendered in the DOM, reducing memory usage.
- **Synchronized Scrolling**:
  - In bilingual mode, scrolling is percentage-based to maintain alignment between columns of different lengths.

---

### 3. **Data Source and Copyright Disclaimer**

#### **Data Sources**
- **Dofus 3 / DofusDB API** (`https://api.beta.dofusdb.fr`) for Dofus 3 documents.
- **Dofus Touch, Wakfu, and Islands of Wakfu JSON payloads** from local datasets:
  - `data/touch/` (`fr`, `en`, `es`, `pt`, `de`)
  - `data/wakfu/` (`fr`, `en`, `es`, `pt`)
  - `data/islandswakfu/mysteries.json` (`fr`, `en`, `es`, `de`, `it`, `ja`)

#### **Copyright Disclaimer**
- All data and content displayed in this application are the property of **Ankama Games**.
- Ankama Games is the creator and owner of the Dofus game and its associated content.
- Data is retrieved via **DofusDB.fr** and used under the terms of their API.

> **Disclaimer**: This application is a fan-made project and is not affiliated with or endorsed by Ankama Games. All rights to the content belong to Ankama Games. For more information, visit [Ankama Games](https://www.ankama.com/fr/games).
