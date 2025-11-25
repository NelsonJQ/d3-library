# Dofus Ingame Library - Bilingual HTML Explorer

A standalone, memory-optimized HTML application for viewing and searching Dofus game documents in multiple languages with bilingual support.

Access here :

https://nelsonjq.github.io/d3-library/
---

## Features

### 1. **UI Elements and Features**
The application provides a rich and interactive user interface designed for ease of use and accessibility. Below are the key UI elements and features:

#### **Available Languages**
- The application supports the following languages:
  - **Spanish (ES)** (default)
  - **English (EN)**
  - **French (FR)**
  - **Portuguese (PT)**
  - **German (DE)**
- Users can switch between these languages using the **Language Selector** in the sidebar.

#### **Bilingual Mode**
- **Single-Language Mode**: Displays content in one selected language.
- **Bilingual Mode**: Displays content side-by-side in two languages, with synchronized scrolling for easy comparison.
  - Users can select a **primary language** and a **secondary language** (excluding the primary language).
  - Titles and subtitles are displayed within each language column.

#### **Search and Navigation**
- **Real-Time Search**: Search across all documents with results displayed instantly.
- **Search Highlighting**: Matches are highlighted in yellow within the document content.
- **Keyboard Shortcuts**:
  - `Ctrl+F` (or `Cmd+F`): Focus on the search bar.
  - `Escape`: Clear the search input.
- **Document Index**: A collapsible sidebar lists all available documents. Clicking on a document title loads its content.

#### **Image Handling**
- Converts placeholders like `##png,ID##` into actual image URLs.
- Images are lazy-loaded and only fetched when hovered over, reducing initial load time and memory usage.

#### **Accessibility Features**
- **Dark/Light Theme Toggle**: Switch between light and dark themes.
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

#### **Data Source**
- The application retrieves data from the **DofusDB API** (`https://api.beta.dofusdb.fr`), which provides access to Dofus game documents.

#### **Copyright Disclaimer**
- All data and content displayed in this application are the property of **Ankama Games**.
- Ankama Games is the creator and owner of the Dofus game and its associated content.
- Data is retrieved via **DofusDB.fr** and used under the terms of their API.

> **Disclaimer**: This application is a fan-made project and is not affiliated with or endorsed by Ankama Games. All rights to the content belong to Ankama Games. For more information, visit [Ankama Games](https://www.ankama.com/fr/games).
