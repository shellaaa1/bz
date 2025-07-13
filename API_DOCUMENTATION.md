# INSO Wallpaper Application - API Documentation

## Overview

The INSO Wallpaper Application is a web-based wallpaper gallery that displays high-quality wallpapers from various categories. The application provides a responsive interface for browsing, filtering, and viewing wallpapers from the INSO API.

**Project Information:**
- **Creator:** redy (2017-3-31)
- **License:** AGPL v3
- **GitHub:** https://github.com/insoxin/API
- **Live Demo:** a.pages.dev

## Table of Contents

1. [Core API Functions](#core-api-functions)
2. [Category Functions](#category-functions)
3. [Navigation Functions](#navigation-functions)
4. [Sorting Functions](#sorting-functions)
5. [Utility Functions](#utility-functions)
6. [CSS Classes](#css-classes)
7. [HTML Components](#html-components)
8. [Configuration Variables](#configuration-variables)
9. [Usage Examples](#usage-examples)
10. [Browser Compatibility](#browser-compatibility)

---

## Core API Functions

### `init()`
**Purpose:** Initializes the wallpaper gallery by fetching images from the INSO API.

**Functionality:**
- Makes a POST request to the INSO API endpoint
- Fetches wallpapers based on current category, orientation, and sorting preferences
- Dynamically resizes images to fit the responsive grid layout
- Sets up click handlers for image viewing
- Scrolls to top of page after loading

**API Endpoint:**
```
POST https://aibizhi.isoyu.com/v1/{orientation}/category/{categoryId}/{orientation}?limit={limit}&skip={skip}&adult=true&first=0&order={order}
```

**Parameters:**
- `orientation`: Image orientation ("vertical" or "horizontal")
- `categoryId`: Category identifier (see category functions)
- `limit`: Number of images per page (default: 48)
- `skip`: Number of images to skip for pagination
- `order`: Sort order ("hot" or "new")

**Response Format:**
```json
{
  "res": {
    "vertical": [
      {
        "wp": "full_image_url",
        "thumb": "thumbnail_url"
      }
    ]
  }
}
```

**Example:**
```javascript
// Initialize with default settings
init();
```

### `init0()`
**Purpose:** Creates the initial HTML structure for the image grid.

**Functionality:**
- Generates placeholder divs for the image grid
- Sets up responsive Bootstrap grid layout
- Adds loading GIF placeholders
- Creates 48 image containers by default

**Grid Structure:**
- **Large screens:** 6 columns (col-lg-2)
- **Medium screens:** 4 columns (col-md-3)
- **Small screens:** 2 columns (col-sm-6, col-xs-6)

**Example:**
```javascript
// Initialize grid structure
init0();
```

---

## Category Functions

### `title_image()`
**Purpose:** Loads the default category (beautiful girls).

**Category ID:** `4e4d610cdf714d2966000000`

**Example:**
```javascript
// Load default category
title_image();
```

### `girls()`
**Purpose:** Loads wallpapers from the "Beautiful Girls" category.

**Category ID:** `4e4d610cdf714d2966000000`

**Example:**
```javascript
// Load girls category
girls();
```

### `scenery()`
**Purpose:** Loads wallpapers from the "Scenery/Landscape" category.

**Category ID:** `4e4d610cdf714d2966000002`

**Example:**
```javascript
// Load scenery category
scenery();
```

### `animation()`
**Purpose:** Loads wallpapers from the "Animation" category.

**Category ID:** `4e4d610cdf714d2966000003`

**Example:**
```javascript
// Load animation category
animation();
```

### `animals()`
**Purpose:** Loads wallpapers from the "Animals" category.

**Category ID:** `4e4d610cdf714d2966000001`

**Example:**
```javascript
// Load animals category
animals();
```

### `game()`
**Purpose:** Loads wallpapers from the "Gaming" category.

**Category ID:** `4e4d610cdf714d2966000007`

**Example:**
```javascript
// Load gaming category
game();
```

### `machine()`
**Purpose:** Loads wallpapers from the "Machinery/Technology" category.

**Category ID:** `4e4d610cdf714d2966000005`

**Example:**
```javascript
// Load machinery category
machine();
```

### `paint()`
**Purpose:** Loads wallpapers from the "Hand-drawn Art" category.

**Category ID:** `4e4d610cdf714d2966000004`

**Example:**
```javascript
// Load hand-drawn art category
paint();
```

### `word()`
**Purpose:** Loads wallpapers from the "Text/Quotes" category.

**Category ID:** `5109e04e48d5b9364ae9ac45`

**Example:**
```javascript
// Load text category
word();
```

### `visual()`
**Purpose:** Loads wallpapers from the "Visual Arts" category.

**Category ID:** `4fb479f75ba1c65561000027`

**Example:**
```javascript
// Load visual arts category
visual();
```

### `monogatari()`
**Purpose:** Loads wallpapers from the "Monogatari" category.

**Category ID:** `4fb47a465ba1c65561000028`

**Example:**
```javascript
// Load monogatari category
monogatari();
```

### `design()`
**Purpose:** Loads wallpapers from the "Design" category.

**Category ID:** `4fb47a195ba1c60ca5000222`

**Example:**
```javascript
// Load design category
design();
```

### `emotion()`
**Purpose:** Loads wallpapers from the "Emotional" category.

**Category ID:** `4ef0a35c0569795756000000`

**Example:**
```javascript
// Load emotional category
emotion();
```

### `city()`
**Purpose:** Loads wallpapers from the "City/Urban" category.

**Category ID:** `4fb47a305ba1c60ca5000223`

**Example:**
```javascript
// Load city category
city();
```

### `film()`
**Purpose:** Loads wallpapers from the "Film/Movie" category.

**Category ID:** `4e58c2570569791a19000000`

**Example:**
```javascript
// Load film category
film();
```

### `handsome()`
**Purpose:** Loads wallpapers from the "Handsome Men" category.

**Category ID:** `4e4d610cdf714d2966000006`

**Example:**
```javascript
// Load handsome men category
handsome();
```

### `stars()`
**Purpose:** Loads wallpapers from the "Celebrities" category.

**Category ID:** `5109e05248d5b9368bb559dc`

**Example:**
```javascript
// Load celebrities category
stars();
```

---

## Navigation Functions

### `first()`
**Purpose:** Navigates to the first page of the current category.

**Functionality:**
- Resets current page to 0
- Resets skip counter to 0
- Reloads images from the beginning

**Example:**
```javascript
// Go to first page
first();
```

### `pre()`
**Purpose:** Navigates to the previous page.

**Functionality:**
- Decrements current page counter
- Updates skip counter for pagination
- Shows alert if already on first page
- Reloads images from previous page

**Example:**
```javascript
// Go to previous page
pre();
```

### `next()`
**Purpose:** Navigates to the next page.

**Functionality:**
- Increments current page counter
- Updates skip counter for pagination
- Reloads images from next page

**Example:**
```javascript
// Go to next page
next();
```

### `random()`
**Purpose:** Loads a random page from the current category.

**Functionality:**
- Generates random skip value between 100-1099
- Reloads images from random position
- Maintains current category and sorting

**Example:**
```javascript
// Load random page
random();
```

---

## Sorting Functions

### `popular()`
**Purpose:** Sorts wallpapers by popularity (most popular first).

**Functionality:**
- Sets order parameter to "hot"
- Resets to first page
- Reloads images with popular sorting

**Example:**
```javascript
// Sort by popularity
popular();
```

### `newer()`
**Purpose:** Sorts wallpapers by date (newest first).

**Functionality:**
- Sets order parameter to "new"
- Resets to first page
- Reloads images with newest sorting

**Example:**
```javascript
// Sort by newest
newer();
```

---

## Utility Functions

### `include(filename)`
**Purpose:** Dynamically includes JavaScript files.

**Parameters:**
- `filename`: URL or path to the JavaScript file

**Functionality:**
- Creates a new script element
- Sets the source to the provided filename
- Appends the script to the document head

**Example:**
```javascript
// Include external script
include('https://example.com/script.js');
```

### `getChromeVersion()`
**Purpose:** Detects the Chrome browser version.

**Returns:**
- Chrome version number as integer
- `false` if not Chrome browser

**Functionality:**
- Parses user agent string for Chrome version
- Returns version number or false

**Example:**
```javascript
// Get Chrome version
var version = getChromeVersion();
if (version >= 79) {
    // Use HTTPS version
} else {
    // Use HTTP version
}
```

---

## CSS Classes

### `.img`
**Purpose:** Styles for wallpaper images.

**Properties:**
- `border: 1px solid #1fbaf3` - Blue border
- `box-shadow: 0 0 15px #1fbaf3` - Blue glow effect
- `border-radius: 5px` - Rounded corners

**Usage:**
```html
<img class="img" src="wallpaper.jpg" alt="Wallpaper">
```

### `.bottom_btn`
**Purpose:** Styles for bottom navigation buttons.

**Properties:**
- `padding-top: 10px` - Top padding
- `padding-bottom: 10px` - Bottom padding
- `text-align: center` - Center alignment

**Usage:**
```html
<div class="bottom_btn">
    <button onclick="first()">First</button>
    <button onclick="pre()">Previous</button>
    <button onclick="next()">Next</button>
    <button onclick="random()">Random</button>
</div>
```

### `.brand`
**Purpose:** Styles for the brand/logo element.

**Properties:**
- `padding: 0` - No padding

**Usage:**
```html
<a class="navbar-brand brand" href="#">INSO壁纸</a>
```

### `.div_container-fluid`
**Purpose:** Styles for the main container.

**Properties:**
- `text-align: center` - Center alignment

**Usage:**
```html
<div class="div_container-fluid">
    <!-- Content -->
</div>
```

### `.div_view_row`
**Purpose:** Styles for view row elements.

**Properties:**
- `margin-top: 10px` - Top margin

**Usage:**
```html
<div class="div_view_row">
    <!-- Content -->
</div>
```

### `.body_view`
**Purpose:** Styles for body view elements.

**Properties:**
- `padding: 20px` - 20px padding

**Usage:**
```html
<div class="body_view">
    <!-- Content -->
</div>
```

---

## HTML Components

### Navigation Bar
**Purpose:** Main navigation component with category filters.

**Structure:**
```html
<nav class="navbar navbar-inverse">
    <div class="container-fluid">
        <div class="navbar-header">
            <a class="navbar-brand brand" onclick="title_image()">INSO壁纸</a>
        </div>
        <div class="collapse navbar-collapse">
            <ul class="nav navbar-nav">
                <!-- Category links -->
            </ul>
        </div>
    </div>
</nav>
```

### Image Grid
**Purpose:** Responsive grid for displaying wallpapers.

**Structure:**
```html
<div class="container-fluid div_container-fluid">
    <div id="gg" class="row">
        <!-- Dynamic image containers -->
    </div>
</div>
```

### Navigation Buttons
**Purpose:** Bottom navigation controls.

**Structure:**
```html
<div class="row bottom_btn">
    <input onclick="first()" type="button" class="btn btn-info" value="首页">
    <input onclick="pre()" type="button" class="btn btn-info" value="上页">
    <input onclick="next()" type="button" class="btn btn-info" value="下页">
    <input onclick="random()" type="button" class="btn btn-info" value="随机">
</div>
```

---

## Configuration Variables

### Global Variables
```javascript
var hv = "vertical";           // Image orientation
var a = "4e4d610cdf714d2966000000";  // Current category ID
var b = 48;                   // Images per page
var c = 0;                    // Skip counter for pagination
var d = "hot";                // Sort order (hot/new)
var currentPage = 0;          // Current page number
var imgsUrl = [];             // Array of full image URLs
var i;                        // Loop counter
```

### Category IDs Reference
| Category | ID | Function |
|----------|----|----------|
| Beautiful Girls | `4e4d610cdf714d2966000000` | `girls()` |
| Scenery | `4e4d610cdf714d2966000002` | `scenery()` |
| Animation | `4e4d610cdf714d2966000003` | `animation()` |
| Animals | `4e4d610cdf714d2966000001` | `animals()` |
| Gaming | `4e4d610cdf714d2966000007` | `game()` |
| Machinery | `4e4d610cdf714d2966000005` | `machine()` |
| Hand-drawn | `4e4d610cdf714d2966000004` | `paint()` |
| Text | `5109e04e48d5b9364ae9ac45` | `word()` |
| Visual Arts | `4fb479f75ba1c65561000027` | `visual()` |
| Monogatari | `4fb47a465ba1c65561000028` | `monogatari()` |
| Design | `4fb47a195ba1c60ca5000222` | `design()` |
| Emotional | `4ef0a35c0569795756000000` | `emotion()` |
| City | `4fb47a305ba1c60ca5000223` | `city()` |
| Film | `4e58c2570569791a19000000` | `film()` |
| Handsome Men | `4e4d610cdf714d2966000006` | `handsome()` |
| Celebrities | `5109e05248d5b9368bb559dc` | `stars()` |

---

## Usage Examples

### Basic Implementation
```html
<!DOCTYPE html>
<html>
<head>
    <title>Wallpaper Gallery</title>
    <link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <script src="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <script src="bz_js/inso_img.js"></script>
    <link href="bz_css/inso_bz.css" rel="stylesheet">
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar navbar-inverse">
        <div class="container-fluid">
            <div class="navbar-header">
                <a class="navbar-brand" onclick="title_image()">Wallpaper Gallery</a>
            </div>
            <div class="collapse navbar-collapse">
                <ul class="nav navbar-nav">
                    <li><a onclick="scenery()">Scenery</a></li>
                    <li><a onclick="animals()">Animals</a></li>
                    <li><a onclick="animation()">Animation</a></li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Image Grid -->
    <div class="container-fluid div_container-fluid">
        <div id="gg" class="row"></div>
    </div>

    <!-- Navigation Buttons -->
    <div class="row bottom_btn">
        <input onclick="first()" type="button" class="btn btn-info" value="First">
        <input onclick="pre()" type="button" class="btn btn-info" value="Previous">
        <input onclick="next()" type="button" class="btn btn-info" value="Next">
        <input onclick="random()" type="button" class="btn btn-info" value="Random">
    </div>
</body>
</html>
```

### Custom Category Loading
```javascript
// Load specific category
function loadCustomCategory(categoryId) {
    currentPage = 0;
    c = Math.floor(Math.random() * 1000) + 100;
    a = categoryId;
    init();
}

// Usage
loadCustomCategory("4e4d610cdf714d2966000002"); // Load scenery
```

### Custom Image Count
```javascript
// Change number of images per page
function setImageCount(count) {
    b = count;
    init0(); // Recreate grid
    init();  // Load images
}

// Usage
setImageCount(24); // Show 24 images per page
```

### Custom Sorting
```javascript
// Custom sort function
function customSort(sortOrder) {
    currentPage = 0;
    c = 0;
    d = sortOrder;
    init();
}

// Usage
customSort("hot");  // Sort by popularity
customSort("new");  // Sort by date
```

---

## Browser Compatibility

### Chrome Version Detection
The application automatically detects Chrome version and loads appropriate scripts:

- **Chrome < 79:** Loads `inso_httpimages.js`
- **Chrome >= 79:** Loads `inso_httpsimages.js`

### Supported Browsers
- Chrome (all versions)
- Firefox
- Safari
- Edge
- Internet Explorer (with Bootstrap 3.3.7 support)

### Dependencies
- **jQuery:** 3.3.1
- **Bootstrap:** 3.3.7
- **Dark Mode JS:** 1.5.4

---

## Error Handling

### Network Errors
- API requests use jQuery's built-in error handling
- Failed requests will not update the image grid
- Users can retry by clicking navigation buttons

### Browser Compatibility
- Automatic script selection based on Chrome version
- Graceful degradation for unsupported features

### User Feedback
- Alert messages for navigation limits ("当前已是首页！！！")
- Loading GIFs for image placeholders
- Responsive design for various screen sizes

---

## Performance Considerations

### Image Loading
- Thumbnails load first for faster display
- Full images load on click
- Responsive image sizing based on container width

### Pagination
- Efficient skip-based pagination
- Random page loading for variety
- Page state management

### Responsive Design
- Bootstrap grid system for responsive layout
- Dynamic image sizing based on screen size
- Mobile-friendly navigation

---

## Security Notes

### API Access
- Uses HTTPS endpoints for secure communication
- No authentication required for public API
- CORS-compliant requests

### Content Filtering
- Adult content filtering available via API parameter
- Safe for general audiences

---

## License Information

**License:** AGPL v3  
**Creator:** redy (2017-3-31)  
**GitHub:** https://github.com/insoxin/API  

Please respect the original work and do not remove or modify the copyright notice.

---

*This documentation covers all public APIs, functions, and components of the INSO Wallpaper Application. For additional support or questions, please refer to the project's GitHub repository.*