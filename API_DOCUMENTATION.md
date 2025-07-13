# INSO Wallpaper API Documentation

## Overview

INSO Wallpaper is a web-based wallpaper gallery application that fetches and displays wallpapers from various categories. The application provides a responsive interface with pagination, category filtering, and sorting capabilities.

## Table of Contents

1. [Core Functions](#core-functions)
2. [Category Functions](#category-functions)
3. [Navigation Functions](#navigation-functions)
4. [Utility Functions](#utility-functions)
5. [Global Variables](#global-variables)
6. [API Endpoints](#api-endpoints)
7. [UI Components](#ui-components)
8. [CSS Classes](#css-classes)
9. [Usage Examples](#usage-examples)

---

## Core Functions

### `init0()`
Initializes the image grid layout with placeholder loading images.

**Purpose**: Sets up the initial DOM structure for the image gallery.

**Parameters**: None

**Returns**: None

**Example**:
```javascript
init0(); // Creates 48 placeholder image containers
```

**Implementation Details**:
- Creates `b` (48) image containers in a Bootstrap grid
- Each container has responsive classes: `col-lg-2 col-md-3 col-sm-6 col-xs-6`
- Displays loading.gif as placeholder during initialization

---

### `init()`
Fetches wallpaper data from the API and populates the image grid.

**Purpose**: Main function that loads and displays wallpapers based on current category and pagination settings.

**Parameters**: None

**Returns**: None

**Example**:
```javascript
init(); // Loads wallpapers for current category and page
```

**Implementation Details**:
- Makes POST request to wallpaper API
- Calculates responsive image dimensions
- Binds click handlers to open full-size wallpapers
- Updates image sources with thumbnail URLs

**API Call Format**:
```
POST https://aibizhi.isoyu.com/v1/vertical/category/{categoryId}/vertical
Query Parameters:
- limit: {b} (number of images, default 48)
- skip: {c} (pagination offset)
- adult: true
- first: 0
- order: {d} (sorting order: "hot" or "new")
```

---

## Category Functions

All category functions follow the same pattern: reset pagination, randomize offset, set category ID, and reload images.

### `girls()`
Loads wallpapers from the Girls/Beauty category.

**Category ID**: `4e4d610cdf714d2966000000`

**Example**:
```javascript
girls(); // Switches to girls category
```

---

### `scenery()`
Loads wallpapers from the Scenery category.

**Category ID**: `4e4d610cdf714d2966000002`

**Example**:
```javascript
scenery(); // Switches to scenery category
```

---

### `animation()`
Loads wallpapers from the Animation category.

**Category ID**: `4e4d610cdf714d2966000003`

**Example**:
```javascript
animation(); // Switches to animation category
```

---

### `animals()`
Loads wallpapers from the Animals category.

**Category ID**: `4e4d610cdf714d2966000001`

**Example**:
```javascript
animals(); // Switches to animals category
```

---

### `game()`
Loads wallpapers from the Gaming category.

**Category ID**: `4e4d610cdf714d2966000007`

**Example**:
```javascript
game(); // Switches to gaming category
```

---

### `machine()`
Loads wallpapers from the Machine/Mechanical category.

**Category ID**: `4e4d610cdf714d2966000005`

**Example**:
```javascript
machine(); // Switches to machine category
```

---

### `paint()`
Loads wallpapers from the Hand-drawn/Paint category.

**Category ID**: `4e4d610cdf714d2966000004`

**Example**:
```javascript
paint(); // Switches to paint category
```

---

### `word()`
Loads wallpapers from the Text/Word category.

**Category ID**: `5109e04e48d5b9364ae9ac45`

**Example**:
```javascript
word(); // Switches to word category
```

---

### `visual()`
Loads wallpapers from the Visual category.

**Category ID**: `4fb479f75ba1c65561000027`

**Example**:
```javascript
visual(); // Switches to visual category
```

---

### `monogatari()`
Loads wallpapers from the Monogatari category.

**Category ID**: `4fb47a465ba1c65561000028`

**Example**:
```javascript
monogatari(); // Switches to monogatari category
```

---

### `design()`
Loads wallpapers from the Design category.

**Category ID**: `4fb47a195ba1c60ca5000222`

**Example**:
```javascript
design(); // Switches to design category
```

---

### `emotion()`
Loads wallpapers from the Emotion category.

**Category ID**: `4ef0a35c0569795756000000`

**Example**:
```javascript
emotion(); // Switches to emotion category
```

---

### `city()`
Loads wallpapers from the City category.

**Category ID**: `4fb47a305ba1c60ca5000223`

**Example**:
```javascript
city(); // Switches to city category
```

---

### `film()`
Loads wallpapers from the Film category.

**Category ID**: `4e58c2570569791a19000000`

**Example**:
```javascript
film(); // Switches to film category
```

---

### `handsome()`
Loads wallpapers from the Handsome/Men category.

**Category ID**: `4e4d610cdf714d2966000006`

**Example**:
```javascript
handsome(); // Switches to handsome category
```

---

### `stars()`
Loads wallpapers from the Stars/Celebrity category.

**Category ID**: `5109e05248d5b9368bb559dc`

**Example**:
```javascript
stars(); // Switches to stars category
```

---

### `title_image()`
Resets to the default category (Girls).

**Purpose**: Returns to the main/default category view.

**Example**:
```javascript
title_image(); // Returns to default category
```

---

## Navigation Functions

### `first()`
Navigates to the first page of the current category.

**Purpose**: Resets pagination to the beginning.

**Example**:
```javascript
first(); // Goes to first page
```

**Implementation**:
- Sets `currentPage = 0`
- Sets `c = 0` (pagination offset)
- Calls `init()` to reload images

---

### `pre()`
Navigates to the previous page if available.

**Purpose**: Implements backward pagination with validation.

**Example**:
```javascript
pre(); // Goes to previous page
```

**Implementation**:
- Checks if `currentPage > 0`
- If true: decrements `currentPage` and recalculates offset
- If false: displays alert "当前已是首页！！！"

---

### `next()`
Navigates to the next page.

**Purpose**: Implements forward pagination.

**Example**:
```javascript
next(); // Goes to next page
```

**Implementation**:
- Increments `currentPage`
- Recalculates pagination offset: `c = currentPage * b`
- Calls `init()` to reload images

---

### `random()`
Loads a random selection of wallpapers from the current category.

**Purpose**: Provides randomized content discovery.

**Example**:
```javascript
random(); // Loads random wallpapers
```

**Implementation**:
- Generates random offset: `c = Math.floor(Math.random() * 1000) + 100`
- Calls `init()` to reload images

---

## Sorting Functions

### `popular()`
Sorts wallpapers by popularity (most popular first).

**Purpose**: Changes sorting order to "hot" (popular).

**Example**:
```javascript
popular(); // Sorts by popularity
```

**Implementation**:
- Sets `d = "hot"`
- Resets pagination: `currentPage = 0, c = 0`
- Calls `init()` to reload images

---

### `newer()`
Sorts wallpapers by newest first.

**Purpose**: Changes sorting order to "new" (newest first).

**Example**:
```javascript
newer(); // Sorts by newest
```

**Implementation**:
- Sets `d = "new"`
- Resets pagination: `currentPage = 0, c = 0`
- Calls `init()` to reload images

---

## Utility Functions

### `include(filename)`
Dynamically loads JavaScript files.

**Purpose**: Loads external JavaScript files into the document head.

**Parameters**:
- `filename` (string): Path to the JavaScript file

**Returns**: None

**Example**:
```javascript
include('https://example.com/script.js');
```

**Implementation**:
- Creates script element
- Sets src and type attributes
- Appends to document head

---

### `getChromeVersion()`
Detects Chrome browser version.

**Purpose**: Browser compatibility detection for version-specific features.

**Parameters**: None

**Returns**: 
- `integer`: Chrome version number
- `false`: If not Chrome browser

**Example**:
```javascript
var version = getChromeVersion();
if (version && version >= 79) {
    // Use modern features
}
```

**Implementation**:
- Parses `navigator.userAgent` for Chrome version
- Returns parsed integer or false

---

## Global Variables

### Configuration Variables

```javascript
var hv = "vertical";           // Image orientation type
var a = "4e4d610cdf714d2966000000"; // Current category ID
var b = 48;                    // Number of images per page
var c = 0;                     // Pagination offset
var d = "hot";                 // Sorting order ("hot" or "new")
var currentPage = 0;           // Current page number
var imgsUrl = [];              // Array storing full-size image URLs
var i;                         // Loop iterator variable
```

### Variable Details

- **`hv`**: Always set to "vertical" for vertical wallpapers
- **`a`**: Category identifier that changes based on selected category
- **`b`**: Controls how many wallpapers are loaded per page
- **`c`**: Calculated as `currentPage * b` for API pagination
- **`d`**: Controls sorting - "hot" for popular, "new" for newest
- **`currentPage`**: Zero-based page counter
- **`imgsUrl`**: Stores full-resolution URLs for click handlers
- **`i`**: Used in loops for image processing

---

## API Endpoints

### Wallpaper API

**Base URL**: `https://aibizhi.isoyu.com/v1/`

**Endpoint**: `POST /vertical/category/{categoryId}/vertical`

**Request Parameters**:
- `limit`: Number of wallpapers to fetch (default: 48)
- `skip`: Number of wallpapers to skip for pagination
- `adult`: Include adult content (true/false)
- `first`: First request flag (0/1)
- `order`: Sort order ("hot" for popular, "new" for newest)

**Response Structure**:
```json
{
  "res": {
    "vertical": [
      {
        "wp": "https://full-size-wallpaper-url.jpg",
        "thumb": "https://thumbnail-url.jpg"
      }
    ]
  }
}
```

**Example Request**:
```javascript
$.post("https://aibizhi.isoyu.com/v1/vertical/category/4e4d610cdf714d2966000000/vertical?limit=48&skip=0&adult=true&first=0&order=hot", 
  function(data) {
    // Process response
  }, 
  "json"
);
```

---

## UI Components

### Navigation Bar

**Bootstrap Components**:
- `navbar-inverse`: Dark theme navigation bar
- `navbar-brand`: Application title "INSO壁纸"
- `navbar-nav`: Navigation menu items
- `dropdown`: Category and sorting dropdowns

**Navigation Items**:
- Category links with Glyphicon icons
- Dropdown menus for additional categories
- Sorting options (Popular/Newest)

### Image Grid

**Bootstrap Grid System**:
- `container-fluid`: Full-width container
- `row`: Bootstrap row container
- Responsive columns: `col-lg-2 col-md-3 col-sm-6 col-xs-6`

**Image Properties**:
- Responsive sizing based on container width
- Aspect ratio: 10:7 (width:height)
- Click handlers for full-size viewing

### Pagination Controls

**Button Layout**:
- `btn btn-info`: Bootstrap button styling
- Centered alignment with `text-align: center`
- Functions: First, Previous, Next, Random

---

## CSS Classes

### Custom Styling

```css
.img {
    border: 1px solid #1fbaf3;
    box-shadow: 0 0 15px #1fbaf3;
    border-radius: 5px;
}
```
**Purpose**: Blue glowing border effect for wallpaper images

```css
.bottom_btn {
    padding-top: 10px;
    padding-bottom: 10px;
    text-align: center;
}
```
**Purpose**: Styling for pagination button container

```css
.div_container-fluid {
    text-align: center;
}
```
**Purpose**: Centers the main content container

```css
.body_view {
    padding: 20px;
}
```
**Purpose**: Padding for main content area

```css
h3 {
    color: #269abc;
}
```
**Purpose**: Blue color for heading elements

---

## Usage Examples

### Basic Implementation

```html
<!DOCTYPE html>
<html>
<head>
    <link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    <link href="bz_css/inso_bz.css" rel="stylesheet">
</head>
<body>
    <div id="gg" class="row"></div>
    
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <script src="bz_js/inso_appVersion.js"></script>
    <script src="bz_js/inso_img.js"></script>
</body>
</html>
```

### Programmatic Category Switching

```javascript
// Switch to different categories
girls();      // Load girls wallpapers
scenery();    // Load scenery wallpapers
animation();  // Load animation wallpapers

// Navigate pages
first();      // Go to first page
next();       // Go to next page
pre();        // Go to previous page
random();     // Load random wallpapers

// Change sorting
popular();    // Sort by popularity
newer();      // Sort by newest
```

### Custom Category Implementation

```javascript
function customCategory() {
    currentPage = 0;
    c = Math.floor(Math.random() * 1000) + 100;
    a = "your-category-id-here";
    init();
}
```

### Event Handling

```javascript
// Add custom click handlers
$(document).ready(function() {
    // Custom initialization
    init0();
    init();
    
    // Custom event handlers
    $('.img').on('click', function() {
        // Custom click handling
    });
});
```

### Responsive Configuration

```javascript
// Adjust images per page for different screen sizes
if (window.innerWidth < 768) {
    b = 24; // Fewer images on mobile
} else {
    b = 48; // More images on desktop
}
```

---

## Browser Compatibility

### Chrome Version Detection

The application automatically detects Chrome version and loads appropriate JavaScript:

- **Chrome < 79**: Loads `inso_httpimages.js`
- **Chrome >= 79**: Loads `inso_httpsimages.js`

### Supported Browsers

- Chrome (all versions)
- Firefox (modern versions)
- Safari (modern versions)
- Edge (modern versions)
- Internet Explorer (with compatibility CSS)

---

## Dependencies

### External Libraries

1. **jQuery 3.3.1**: DOM manipulation and AJAX
2. **Bootstrap 3.3.7**: CSS framework and components
3. **Darkmode.js 1.5.4**: Dark mode functionality

### CDN Resources

```html
<!-- CSS -->
<link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">

<!-- JavaScript -->
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script src="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/darkmode-js@1.5.4/lib/darkmode-js.min.js"></script>
```

---

## Error Handling

### Navigation Errors

```javascript
function pre() {
    if (currentPage > 0) {
        currentPage--;
        c = currentPage * b;
        init();
    } else {
        alert("当前已是首页！！！"); // "Already on first page"
    }
}
```

### API Error Handling

The application relies on jQuery's AJAX error handling. For production use, consider adding:

```javascript
$.post(apiUrl, function(data) {
    // Success handler
}).fail(function(xhr, status, error) {
    console.error('API Error:', error);
    // Handle error state
});
```

---

## Performance Considerations

### Image Loading

- Uses thumbnail URLs for grid display
- Full-size images loaded only on click
- Loading GIF placeholders during initialization

### Pagination

- Loads 48 images per page by default
- Configurable via `b` variable
- Efficient offset-based pagination

### Caching

- Stores full-size URLs in `imgsUrl` array
- Prevents duplicate API calls for same page
- Browser caching of thumbnails and resources

---

## Security Considerations

### CORS

- API endpoints must support CORS for cross-origin requests
- Current implementation uses `https://aibizhi.isoyu.com/v1/`

### Content Safety

- `adult=true` parameter in API requests
- Consider implementing content filtering for different audiences

### XSS Prevention

- All dynamic content should be properly escaped
- Consider using jQuery's `.text()` instead of `.html()` for user content

---

## License

This project is licensed under AGPL v3. Please respect the original work and do not modify copyright information.

**Original Author**: redy  
**GitHub**: https://github.com/insoxin/API  
**Created**: 2017-3-31