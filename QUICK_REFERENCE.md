# INSO Wallpaper - Quick Reference Guide

## 🚀 Getting Started

```javascript
// Initialize the application
init0();  // Setup grid
init();   // Load wallpapers
```

## 📝 Category Functions

| Function | Description | Category ID |
|----------|-------------|-------------|
| `girls()` | Beauty/Girls | `4e4d610cdf714d2966000000` |
| `scenery()` | Scenery | `4e4d610cdf714d2966000002` |
| `animation()` | Animation | `4e4d610cdf714d2966000003` |
| `animals()` | Animals | `4e4d610cdf714d2966000001` |
| `game()` | Gaming | `4e4d610cdf714d2966000007` |
| `machine()` | Mechanical | `4e4d610cdf714d2966000005` |
| `paint()` | Hand-drawn | `4e4d610cdf714d2966000004` |
| `word()` | Text/Word | `5109e04e48d5b9364ae9ac45` |
| `visual()` | Visual | `4fb479f75ba1c65561000027` |
| `monogatari()` | Monogatari | `4fb47a465ba1c65561000028` |
| `design()` | Design | `4fb47a195ba1c60ca5000222` |
| `emotion()` | Emotion | `4ef0a35c0569795756000000` |
| `city()` | City | `4fb47a305ba1c60ca5000223` |
| `film()` | Film | `4e58c2570569791a19000000` |
| `handsome()` | Men | `4e4d610cdf714d2966000006` |
| `stars()` | Celebrity | `5109e05248d5b9368bb559dc` |

## 🧭 Navigation Functions

```javascript
first();    // Go to first page
pre();      // Previous page
next();     // Next page
random();   // Load random wallpapers
```

## 🔄 Sorting Functions

```javascript
popular();  // Sort by popularity (hot)
newer();    // Sort by newest
```

## 🔧 Utility Functions

```javascript
include('script.js');        // Load external JS
getChromeVersion();          // Get Chrome version
title_image();              // Reset to default category
```

## 📊 Global Variables

```javascript
var hv = "vertical";         // Image orientation
var a = "category-id";       // Current category ID
var b = 48;                  // Images per page
var c = 0;                   // Pagination offset
var d = "hot";              // Sort order
var currentPage = 0;         // Current page
var imgsUrl = [];           // Full-size image URLs
```

## 🌐 API Endpoint

```javascript
// Base URL
https://aibizhi.isoyu.com/v1/vertical/category/{categoryId}/vertical

// Parameters
?limit=48&skip=0&adult=true&first=0&order=hot
```

## 🎨 CSS Classes

```css
.img                    /* Image styling with blue glow */
.bottom_btn            /* Pagination button container */
.div_container-fluid   /* Main content container */
.body_view             /* Content area padding */
```

## 📱 Responsive Grid

```html
<div class="col-lg-2 col-md-3 col-sm-6 col-xs-6">
  <img class="img" src="..." alt="...">
</div>
```

## 🔗 Dependencies

- jQuery 3.3.1
- Bootstrap 3.3.7
- Darkmode.js 1.5.4

## ⚡ Common Usage Patterns

### Switch Category
```javascript
scenery();  // Load scenery wallpapers
```

### Navigate Pages
```javascript
next();     // Go to next page
pre();      // Go to previous page
```

### Change Sorting
```javascript
popular();  // Sort by popularity
newer();    // Sort by newest
```

### Custom Category
```javascript
function customCategory() {
    currentPage = 0;
    c = Math.floor(Math.random() * 1000) + 100;
    a = "your-category-id";
    init();
}
```

### Responsive Configuration
```javascript
if (window.innerWidth < 768) {
    b = 24;  // Fewer images on mobile
} else {
    b = 48;  // More images on desktop
}
```

## 🛠️ Browser Compatibility

- Chrome < 79: Uses `inso_httpimages.js`
- Chrome >= 79: Uses `inso_httpsimages.js`
- Auto-detection via `getChromeVersion()`

## 📄 Files Structure

```
├── index.html              # Main HTML file
├── bz_css/
│   └── inso_bz.css        # Custom styles
├── bz_js/
│   ├── inso_appVersion.js  # Version detection
│   ├── inso_img.js         # Main image functions
│   ├── inso_httpimages.js  # HTTP version
│   └── inso_httpsimages.js # HTTPS version
└── insoimg/
    └── loading.gif         # Loading animation
```

## 🔍 Error Handling

```javascript
// Navigation validation
function pre() {
    if (currentPage > 0) {
        // Navigate to previous page
    } else {
        alert("当前已是首页！！！");
    }
}

// API error handling (recommended)
$.post(apiUrl, function(data) {
    // Success
}).fail(function(xhr, status, error) {
    console.error('API Error:', error);
});
```

## 🎯 Performance Tips

1. **Image Loading**: Thumbnails first, full-size on click
2. **Pagination**: 48 images per page (configurable)
3. **Caching**: Full URLs stored in `imgsUrl` array
4. **Random Loading**: Offset randomization for variety

## 🔐 Security Notes

- CORS required for API calls
- Content filtering via `adult=true` parameter
- XSS prevention for dynamic content

---

For detailed documentation, see [API_DOCUMENTATION.md](API_DOCUMENTATION.md)