# INSO Wallpaper API - Quick Reference Guide

## 🚀 Quick Start

```html
<!-- Include required files -->
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script src="bz_js/inso_img.js"></script>
<link href="bz_css/inso_bz.css" rel="stylesheet">

<!-- Initialize -->
<script>
$(function() {
    init0(); // Create grid
    init();  // Load images
});
</script>
```

## 📋 Function Reference

### Core Functions
| Function | Purpose | Example |
|----------|---------|---------|
| `init()` | Load images from API | `init()` |
| `init0()` | Create image grid | `init0()` |

### Category Functions
| Function | Category | ID |
|----------|----------|----|
| `title_image()` | Default (Girls) | `4e4d610cdf714d2966000000` |
| `girls()` | Beautiful Girls | `4e4d610cdf714d2966000000` |
| `scenery()` | Scenery | `4e4d610cdf714d2966000002` |
| `animation()` | Animation | `4e4d610cdf714d2966000003` |
| `animals()` | Animals | `4e4d610cdf714d2966000001` |
| `game()` | Gaming | `4e4d610cdf714d2966000007` |
| `machine()` | Machinery | `4e4d610cdf714d2966000005` |
| `paint()` | Hand-drawn | `4e4d610cdf714d2966000004` |
| `word()` | Text/Quotes | `5109e04e48d5b9364ae9ac45` |
| `visual()` | Visual Arts | `4fb479f75ba1c65561000027` |
| `monogatari()` | Monogatari | `4fb47a465ba1c65561000028` |
| `design()` | Design | `4fb47a195ba1c60ca5000222` |
| `emotion()` | Emotional | `4ef0a35c0569795756000000` |
| `city()` | City/Urban | `4fb47a305ba1c60ca5000223` |
| `film()` | Film/Movie | `4e58c2570569791a19000000` |
| `handsome()` | Handsome Men | `4e4d610cdf714d2966000006` |
| `stars()` | Celebrities | `5109e05248d5b9368bb559dc` |

### Navigation Functions
| Function | Purpose | Example |
|----------|---------|---------|
| `first()` | Go to first page | `first()` |
| `pre()` | Previous page | `pre()` |
| `next()` | Next page | `next()` |
| `random()` | Random page | `random()` |

### Sorting Functions
| Function | Purpose | Example |
|----------|---------|---------|
| `popular()` | Sort by popularity | `popular()` |
| `newer()` | Sort by newest | `newer()` |

## 🔧 Configuration Variables

```javascript
// Global configuration
var hv = "vertical";           // Orientation
var a = "4e4d610cdf714d2966000000";  // Category ID
var b = 48;                   // Images per page
var c = 0;                    // Skip counter
var d = "hot";                // Sort order
var currentPage = 0;          // Current page
var imgsUrl = [];             // Image URLs array
```

## 🎨 CSS Classes

| Class | Purpose | Usage |
|-------|---------|-------|
| `.img` | Image styling | `<img class="img">` |
| `.bottom_btn` | Navigation buttons | `<div class="bottom_btn">` |
| `.brand` | Brand/logo | `<a class="navbar-brand brand">` |
| `.div_container-fluid` | Main container | `<div class="div_container-fluid">` |

## 📡 API Endpoint

```
POST https://aibizhi.isoyu.com/v1/{orientation}/category/{categoryId}/{orientation}
```

**Parameters:**
- `orientation`: "vertical" or "horizontal"
- `categoryId`: Category identifier
- `limit`: Images per page (default: 48)
- `skip`: Skip count for pagination
- `order`: "hot" or "new"
- `adult`: "true" or "false"

## 📱 Responsive Grid

```html
<!-- Bootstrap responsive classes -->
<div class="col-lg-2 col-md-3 col-sm-6 col-xs-6">
    <img class="img" src="..." alt="...">
</div>
```

- **Large screens:** 6 columns
- **Medium screens:** 4 columns  
- **Small screens:** 2 columns

## 🔄 Common Patterns

### Load Category with Random Start
```javascript
function loadCategory(categoryId) {
    currentPage = 0;
    c = Math.floor(Math.random() * 1000) + 100;
    a = categoryId;
    init();
}
```

### Change Images Per Page
```javascript
function setImageCount(count) {
    b = count;
    init0();
    init();
}
```

### Custom Sort
```javascript
function customSort(order) {
    currentPage = 0;
    c = 0;
    d = order;
    init();
}
```

## 🚨 Error Handling

```javascript
// Check if on first page
if (currentPage > 0) {
    pre();
} else {
    alert("当前已是首页！！！");
}
```

## 🌐 Browser Support

- **Chrome:** All versions (auto-detects for HTTPS/HTTP)
- **Firefox:** All versions
- **Safari:** All versions
- **Edge:** All versions
- **IE:** With Bootstrap 3.3.7

## 📦 Dependencies

```html
<!-- Required -->
<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
<script src="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
<link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">

<!-- Optional -->
<script src="https://cdn.jsdelivr.net/npm/darkmode-js@1.5.4/lib/darkmode-js.min.js"></script>
```

## 🎯 Quick Examples

### Basic Gallery
```html
<div id="gg" class="row"></div>
<div class="bottom_btn">
    <button onclick="first()">First</button>
    <button onclick="next()">Next</button>
    <button onclick="random()">Random</button>
</div>
```

### Category Navigation
```html
<ul class="nav navbar-nav">
    <li><a onclick="scenery()">Scenery</a></li>
    <li><a onclick="animals()">Animals</a></li>
    <li><a onclick="animation()">Animation</a></li>
</ul>
```

### Sort Controls
```html
<ul class="dropdown-menu">
    <li><a onclick="popular()">Most Popular</a></li>
    <li><a onclick="newer()">Newest</a></li>
</ul>
```

---

*For detailed documentation, see `API_DOCUMENTATION.md`*