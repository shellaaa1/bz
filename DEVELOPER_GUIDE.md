# INSO Wallpaper API - Developer Guide

## Table of Contents

1. [Getting Started](#getting-started)
2. [Integration Examples](#integration-examples)
3. [Customization Guide](#customization-guide)
4. [Advanced Usage](#advanced-usage)
5. [Troubleshooting](#troubleshooting)
6. [Best Practices](#best-practices)

---

## Getting Started

### Prerequisites

- Modern web browser
- Basic knowledge of HTML, CSS, and JavaScript
- jQuery 3.3.1 or higher
- Bootstrap 3.3.7 (for responsive design)

### Basic Setup

1. **Include Dependencies**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Wallpaper Gallery</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    
    <!-- Bootstrap CSS -->
    <link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    
    <!-- Custom CSS -->
    <link href="bz_css/inso_bz.css" rel="stylesheet">
</head>
<body>
    <!-- jQuery -->
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    
    <!-- Bootstrap JS -->
    <script src="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
    
    <!-- INSO Wallpaper API -->
    <script src="bz_js/inso_img.js"></script>
</body>
</html>
```

2. **Create Basic Structure**
```html
<!-- Navigation -->
<nav class="navbar navbar-inverse">
    <div class="container-fluid">
        <div class="navbar-header">
            <a class="navbar-brand" onclick="title_image()">Wallpaper Gallery</a>
        </div>
    </div>
</nav>

<!-- Image Grid Container -->
<div class="container-fluid div_container-fluid">
    <div id="gg" class="row"></div>
</div>

<!-- Navigation Controls -->
<div class="row bottom_btn">
    <input onclick="first()" type="button" class="btn btn-info" value="First">
    <input onclick="pre()" type="button" class="btn btn-info" value="Previous">
    <input onclick="next()" type="button" class="btn btn-info" value="Next">
    <input onclick="random()" type="button" class="btn btn-info" value="Random">
</div>
```

3. **Initialize Gallery**
```javascript
$(document).ready(function() {
    init0(); // Create grid structure
    init();  // Load initial images
});
```

---

## Integration Examples

### Example 1: Minimal Gallery

```html
<!DOCTYPE html>
<html>
<head>
    <title>Minimal Wallpaper Gallery</title>
    <link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    <link href="bz_css/inso_bz.css" rel="stylesheet">
</head>
<body>
    <div class="container-fluid">
        <h1>Wallpaper Gallery</h1>
        <div id="gg" class="row"></div>
        <div class="row bottom_btn">
            <button onclick="first()" class="btn btn-primary">First</button>
            <button onclick="next()" class="btn btn-primary">Next</button>
            <button onclick="random()" class="btn btn-primary">Random</button>
        </div>
    </div>
    
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <script src="bz_js/inso_img.js"></script>
    <script>
        $(function() {
            init0();
            init();
        });
    </script>
</body>
</html>
```

### Example 2: Category-Based Gallery

```html
<!DOCTYPE html>
<html>
<head>
    <title>Category Wallpaper Gallery</title>
    <link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    <link href="bz_css/inso_bz.css" rel="stylesheet">
</head>
<body>
    <nav class="navbar navbar-default">
        <div class="container-fluid">
            <div class="navbar-header">
                <a class="navbar-brand" onclick="title_image()">Wallpaper Gallery</a>
            </div>
            <div class="collapse navbar-collapse">
                <ul class="nav navbar-nav">
                    <li><a onclick="scenery()">Scenery</a></li>
                    <li><a onclick="animals()">Animals</a></li>
                    <li><a onclick="animation()">Animation</a></li>
                    <li><a onclick="game()">Gaming</a></li>
                </ul>
                <ul class="nav navbar-nav navbar-right">
                    <li class="dropdown">
                        <a class="dropdown-toggle" data-toggle="dropdown">Sort <span class="caret"></span></a>
                        <ul class="dropdown-menu">
                            <li><a onclick="popular()">Popular</a></li>
                            <li><a onclick="newer()">Newest</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    
    <div class="container-fluid">
        <div id="gg" class="row"></div>
        <div class="row bottom_btn">
            <button onclick="first()" class="btn btn-info">First</button>
            <button onclick="pre()" class="btn btn-info">Previous</button>
            <button onclick="next()" class="btn btn-info">Next</button>
            <button onclick="random()" class="btn btn-info">Random</button>
        </div>
    </div>
    
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <script src="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <script src="bz_js/inso_img.js"></script>
    <script>
        $(function() {
            init0();
            init();
        });
    </script>
</body>
</html>
```

### Example 3: Custom Styled Gallery

```html
<!DOCTYPE html>
<html>
<head>
    <title>Custom Wallpaper Gallery</title>
    <link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    <link href="bz_css/inso_bz.css" rel="stylesheet">
    <style>
        .custom-gallery {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px 0;
        }
        
        .custom-nav {
            background: rgba(255, 255, 255, 0.1) !important;
            border: none;
            backdrop-filter: blur(10px);
        }
        
        .custom-nav .navbar-brand,
        .custom-nav .navbar-nav > li > a {
            color: white !important;
        }
        
        .custom-nav .navbar-nav > li > a:hover {
            background: rgba(255, 255, 255, 0.2) !important;
        }
        
        .custom-btn {
            background: rgba(255, 255, 255, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.3);
            color: white;
            transition: all 0.3s ease;
        }
        
        .custom-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            color: white;
        }
        
        .custom-img {
            border: 2px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            border-radius: 10px;
            transition: transform 0.3s ease;
        }
        
        .custom-img:hover {
            transform: scale(1.05);
        }
    </style>
</head>
<body>
    <div class="custom-gallery">
        <nav class="navbar navbar-default custom-nav">
            <div class="container-fluid">
                <div class="navbar-header">
                    <a class="navbar-brand" onclick="title_image()">🌟 Wallpaper Gallery</a>
                </div>
                <div class="collapse navbar-collapse">
                    <ul class="nav navbar-nav">
                        <li><a onclick="scenery()">🏔️ Scenery</a></li>
                        <li><a onclick="animals()">🐾 Animals</a></li>
                        <li><a onclick="animation()">🎨 Animation</a></li>
                        <li><a onclick="game()">🎮 Gaming</a></li>
                    </ul>
                </div>
            </div>
        </nav>
        
        <div class="container-fluid">
            <div id="gg" class="row"></div>
            <div class="row bottom_btn">
                <button onclick="first()" class="btn custom-btn">First</button>
                <button onclick="pre()" class="btn custom-btn">Previous</button>
                <button onclick="next()" class="btn custom-btn">Next</button>
                <button onclick="random()" class="btn custom-btn">Random</button>
            </div>
        </div>
    </div>
    
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <script src="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <script src="bz_js/inso_img.js"></script>
    <script>
        $(function() {
            // Override default image class
            var originalInit0 = init0;
            init0 = function() {
                originalInit0();
                $('.img').addClass('custom-img');
            };
            
            init0();
            init();
        });
    </script>
</body>
</html>
```

---

## Customization Guide

### Customizing Image Count

```javascript
// Change number of images per page
function setImageCount(count) {
    b = count; // Global variable for image count
    init0();   // Recreate grid
    init();    // Load images
}

// Usage
setImageCount(24); // Show 24 images instead of 48
```

### Customizing Image Sizing

```javascript
// Override image sizing in init() function
function customInit() {
    $.post("https://aibizhi.isoyu.com/v1/" + hv + "/category/" + a + "/" + hv + "?limit=" + b + "&skip=" + c + "&adult=true&first=0&order=" + d, function (data) {
        var imgs = document.getElementsByClassName("img");
        for (i = 0; i < imgs.length; i++) {
            var url = data.res.vertical[i].wp;
            imgsUrl[i] = url;
            var img = imgs[i];
            
            // Custom sizing
            img.width = 300;  // Fixed width
            img.height = 400; // Fixed height
            
            img.src = "" + data.res.vertical[i].thumb;
            $(img).click({m: imgsUrl, i: i}, function (event) {
                window.open("" + event.data.m[event.data.i], "true - URL");
            });
        }
    }, "json");
    window.scrollTo(0,0);
}
```

### Customizing Grid Layout

```javascript
// Custom grid creation
function customInit0() {
    var div_row = $("#gg");
    div_row.empty(); // Clear existing content
    
    for (var k = 0; k < b; k++) {
        div_row.append(`
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12" style="padding: 10px">
                <div class="image-container" style="position: relative; overflow: hidden; border-radius: 10px;">
                    <img class="img custom-img"
                         src="https://cdn.jsdelivr.net/gh/insoxin/bz@main/insoimg/loading.gif"
                         alt="Loading..."
                         style="width: 100%; height: auto; transition: transform 0.3s ease;">
                    <div class="image-overlay" style="position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.5); opacity: 0; transition: opacity 0.3s ease;"></div>
                </div>
            </div>
        `);
    }
}
```

### Adding Loading States

```javascript
// Add loading indicator
function showLoading() {
    $('#gg').html('<div class="col-12 text-center"><div class="spinner-border" role="status"><span class="sr-only">Loading...</span></div></div>');
}

function hideLoading() {
    // Loading will be hidden when images load
}

// Modified init function with loading
function initWithLoading() {
    showLoading();
    $.post("https://aibizhi.isoyu.com/v1/" + hv + "/category/" + a + "/" + hv + "?limit=" + b + "&skip=" + c + "&adult=true&first=0&order=" + d, function (data) {
        // ... existing code ...
        hideLoading();
    }, "json").fail(function() {
        hideLoading();
        $('#gg').html('<div class="col-12 text-center text-danger">Failed to load images. Please try again.</div>');
    });
}
```

---

## Advanced Usage

### Custom Category Management

```javascript
// Category management system
var categories = {
    scenery: {
        id: "4e4d610cdf714d2966000002",
        name: "Scenery",
        icon: "🏔️"
    },
    animals: {
        id: "4e4d610cdf714d2966000001", 
        name: "Animals",
        icon: "🐾"
    },
    animation: {
        id: "4e4d610cdf714d2966000003",
        name: "Animation", 
        icon: "🎨"
    }
};

function loadCategory(categoryKey) {
    if (categories[categoryKey]) {
        currentPage = 0;
        c = Math.floor(Math.random() * 1000) + 100;
        a = categories[categoryKey].id;
        init();
        
        // Update UI
        $('.current-category').text(categories[categoryKey].name);
    }
}

// Dynamic category menu generation
function generateCategoryMenu() {
    var menu = $('.category-menu');
    menu.empty();
    
    Object.keys(categories).forEach(function(key) {
        var category = categories[key];
        menu.append(`
            <li><a onclick="loadCategory('${key}')">${category.icon} ${category.name}</a></li>
        `);
    });
}
```

### Image Preloading

```javascript
// Preload next page images
function preloadNextPage() {
    var nextSkip = c + b;
    $.post("https://aibizhi.isoyu.com/v1/" + hv + "/category/" + a + "/" + hv + "?limit=" + b + "&skip=" + nextSkip + "&adult=true&first=0&order=" + d, function (data) {
        // Store preloaded data
        window.preloadedData = data;
    }, "json");
}

// Use preloaded data
function nextWithPreload() {
    if (window.preloadedData) {
        // Use preloaded data
        displayImages(window.preloadedData);
        currentPage++;
        c = currentPage * b;
        
        // Preload next page
        preloadNextPage();
    } else {
        // Fallback to normal next
        next();
    }
}
```

### Custom Image Display

```javascript
// Custom image display function
function displayImages(data) {
    var imgs = document.getElementsByClassName("img");
    for (i = 0; i < imgs.length; i++) {
        var url = data.res.vertical[i].wp;
        imgsUrl[i] = url;
        var img = imgs[i];
        
        // Add fade-in effect
        $(img).fadeOut(200, function() {
            img.src = "" + data.res.vertical[i].thumb;
            $(img).fadeIn(200);
        });
        
        // Enhanced click handler
        $(img).off('click').click({m: imgsUrl, i: i}, function (event) {
            var fullUrl = event.data.m[event.data.i];
            
            // Create modal for full image
            var modal = $(`
                <div class="modal fade" tabindex="-1">
                    <div class="modal-dialog modal-lg">
                        <div class="modal-content">
                            <div class="modal-header">
                                <button type="button" class="close" data-dismiss="modal">&times;</button>
                                <h4 class="modal-title">Full Image</h4>
                            </div>
                            <div class="modal-body text-center">
                                <img src="${fullUrl}" style="max-width: 100%; height: auto;">
                            </div>
                            <div class="modal-footer">
                                <a href="${fullUrl}" target="_blank" class="btn btn-primary">Open in New Tab</a>
                                <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
                            </div>
                        </div>
                    </div>
                </div>
            `);
            
            modal.modal('show');
        });
    }
}
```

---

## Troubleshooting

### Common Issues

#### 1. Images Not Loading
```javascript
// Check network connectivity
function checkConnection() {
    $.ajax({
        url: "https://aibizhi.isoyu.com/v1/vertical/category/4e4d610cdf714d2966000000/vertical?limit=1&skip=0&adult=true&first=0&order=hot",
        method: "POST",
        timeout: 5000,
        success: function() {
            console.log("API is accessible");
        },
        error: function(xhr, status, error) {
            console.error("API error:", error);
            $('#gg').html('<div class="col-12 text-center text-danger">Network error. Please check your connection.</div>');
        }
    });
}
```

#### 2. Grid Layout Issues
```javascript
// Fix grid layout
function fixGridLayout() {
    // Ensure proper Bootstrap classes
    $('.col-lg-2').removeClass('col-lg-2').addClass('col-lg-2 col-md-3 col-sm-6 col-xs-6');
    
    // Force reflow
    $('.row').each(function() {
        $(this).hide().show(0);
    });
}
```

#### 3. Browser Compatibility
```javascript
// Browser detection and fallbacks
function checkBrowserCompatibility() {
    var userAgent = navigator.userAgent;
    var isChrome = /Chrome/.test(userAgent);
    var isFirefox = /Firefox/.test(userAgent);
    var isSafari = /Safari/.test(userAgent);
    
    if (!isChrome && !isFirefox && !isSafari) {
        console.warn("Browser may not be fully supported");
        // Add fallback styles or functionality
    }
}
```

### Debug Mode

```javascript
// Enable debug mode
var DEBUG_MODE = true;

function debugLog(message, data) {
    if (DEBUG_MODE) {
        console.log("[INSO API Debug]", message, data);
    }
}

// Modified init function with debug
function initWithDebug() {
    debugLog("Initializing gallery", {
        category: a,
        page: currentPage,
        skip: c,
        order: d
    });
    
    $.post("https://aibizhi.isoyu.com/v1/" + hv + "/category/" + a + "/" + hv + "?limit=" + b + "&skip=" + c + "&adult=true&first=0&order=" + d, function (data) {
        debugLog("API response received", data);
        // ... existing code ...
    }, "json").fail(function(xhr, status, error) {
        debugLog("API request failed", {status: status, error: error, xhr: xhr});
    });
}
```

---

## Best Practices

### 1. Performance Optimization

```javascript
// Debounce rapid function calls
function debounce(func, wait) {
    var timeout;
    return function executedFunction(...args) {
        var later = function() {
            clearTimeout(timeout);
            func(...args);
        };
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
    };
}

// Debounced navigation
var debouncedNext = debounce(next, 300);
var debouncedPre = debounce(pre, 300);
```

### 2. Error Handling

```javascript
// Comprehensive error handling
function safeInit() {
    try {
        if (typeof $ === 'undefined') {
            throw new Error('jQuery not loaded');
        }
        
        if (typeof init === 'undefined') {
            throw new Error('INSO API not loaded');
        }
        
        init0();
        init();
        
    } catch (error) {
        console.error('Initialization failed:', error);
        $('#gg').html(`
            <div class="col-12 text-center">
                <div class="alert alert-danger">
                    <h4>Initialization Error</h4>
                    <p>${error.message}</p>
                    <button onclick="location.reload()" class="btn btn-primary">Retry</button>
                </div>
            </div>
        `);
    }
}
```

### 3. Accessibility

```javascript
// Add accessibility features
function enhanceAccessibility() {
    // Add ARIA labels
    $('.img').attr('role', 'button');
    $('.img').attr('tabindex', '0');
    
    // Add keyboard navigation
    $('.img').keypress(function(e) {
        if (e.which === 13 || e.which === 32) { // Enter or Space
            $(this).click();
        }
    });
    
    // Add screen reader support
    $('.bottom_btn button').each(function() {
        var text = $(this).val();
        $(this).attr('aria-label', text + ' page');
    });
}
```

### 4. Mobile Optimization

```javascript
// Mobile-specific optimizations
function optimizeForMobile() {
    if (window.innerWidth <= 768) {
        // Reduce image count on mobile
        b = 24;
        
        // Add touch gestures
        var touchStartX = 0;
        var touchEndX = 0;
        
        document.addEventListener('touchstart', function(e) {
            touchStartX = e.changedTouches[0].screenX;
        });
        
        document.addEventListener('touchend', function(e) {
            touchEndX = e.changedTouches[0].screenX;
            handleSwipe();
        });
        
        function handleSwipe() {
            var swipeThreshold = 50;
            var diff = touchStartX - touchEndX;
            
            if (Math.abs(diff) > swipeThreshold) {
                if (diff > 0) {
                    next(); // Swipe left
                } else {
                    pre();  // Swipe right
                }
            }
        }
    }
}
```

### 5. SEO and Meta Tags

```html
<!-- Add SEO-friendly meta tags -->
<head>
    <meta name="description" content="High-quality wallpaper gallery with categories including scenery, animals, animation, and more">
    <meta name="keywords" content="wallpapers, backgrounds, scenery, animals, animation, gaming">
    <meta property="og:title" content="INSO Wallpaper Gallery">
    <meta property="og:description" content="Discover beautiful wallpapers from various categories">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://your-domain.com">
    <meta property="og:image" content="https://your-domain.com/preview.jpg">
</head>
```

---

## Conclusion

This developer guide provides comprehensive examples and best practices for integrating the INSO Wallpaper API into your web applications. The API is designed to be simple yet powerful, offering extensive customization options while maintaining ease of use.

For additional support or questions, please refer to the main documentation or the project's GitHub repository.

---

*This guide is part of the INSO Wallpaper API documentation suite. See `API_DOCUMENTATION.md` for complete API reference and `QUICK_REFERENCE.md` for quick lookup tables.*