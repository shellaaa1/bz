# INSO Wallpaper Application

A comprehensive web-based wallpaper gallery that displays high-quality wallpapers from various categories using the INSO API.

## 📚 Documentation

This project includes comprehensive documentation for all public APIs, functions, and components:

- **[API Documentation](API_DOCUMENTATION.md)** - Complete API reference with detailed function descriptions
- **[Quick Reference](QUICK_REFERENCE.md)** - Fast lookup tables and common usage patterns
- **[Developer Guide](DEVELOPER_GUIDE.md)** - Integration examples and best practices

## 🚀 Quick Start

### Basic Implementation

```html
<!DOCTYPE html>
<html>
<head>
    <title>Wallpaper Gallery</title>
    <link href="https://cdn.bootcss.com/twitter-bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
    <link href="bz_css/inso_bz.css" rel="stylesheet">
</head>
<body>
    <div class="container-fluid">
        <div id="gg" class="row"></div>
        <div class="row bottom_btn">
            <button onclick="first()" class="btn btn-info">First</button>
            <button onclick="next()" class="btn btn-info">Next</button>
            <button onclick="random()" class="btn btn-info">Random</button>
        </div>
    </div>
    
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <script src="bz_js/inso_img.js"></script>
    <script>
        $(function() {
            init0(); // Create grid
            init();  // Load images
        });
    </script>
</body>
</html>
```

## 🎯 Features

- **16+ Categories** - Scenery, Animals, Animation, Gaming, and more
- **Responsive Design** - Works on desktop, tablet, and mobile
- **Pagination** - Navigate through thousands of wallpapers
- **Sorting Options** - Popular and newest wallpapers
- **Random Access** - Discover new wallpapers randomly
- **High Quality** - Full-resolution wallpapers
- **Fast Loading** - Optimized thumbnail loading

## 📁 Project Structure

```
├── index.html              # Main application file
├── bz_css/
│   └── inso_bz.css        # Custom styles
├── bz_js/
│   ├── inso_img.js        # Main API functions
│   ├── inso_appVersion.js # Browser compatibility
│   ├── inso_httpimages.js # HTTP version (Chrome < 79)
│   └── inso_httpsimages.js # HTTPS version (Chrome >= 79)
├── insoimg/
│   └── loading.gif        # Loading placeholder
├── API_DOCUMENTATION.md   # Complete API reference
├── QUICK_REFERENCE.md     # Quick lookup guide
├── DEVELOPER_GUIDE.md     # Integration guide
└── README.md              # This file
```

## 🔧 API Functions

### Core Functions
- `init()` - Load images from API
- `init0()` - Create image grid

### Category Functions
- `scenery()` - Landscape wallpapers
- `animals()` - Animal wallpapers  
- `animation()` - Animated wallpapers
- `game()` - Gaming wallpapers
- `girls()` - Beautiful girls
- And 11 more categories...

### Navigation Functions
- `first()` - Go to first page
- `pre()` - Previous page
- `next()` - Next page
- `random()` - Random page

### Sorting Functions
- `popular()` - Sort by popularity
- `newer()` - Sort by newest

## 🌐 API Endpoint

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

## 🎨 Customization

### Change Image Count
```javascript
b = 24; // Show 24 images instead of 48
init0();
init();
```

### Custom Category
```javascript
a = "4e4d610cdf714d2966000002"; // Scenery category
init();
```

### Custom Styling
```css
.img {
    border: 2px solid #your-color;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}
```

## 📱 Browser Support

- **Chrome:** All versions (auto-detects HTTPS/HTTP)
- **Firefox:** All versions
- **Safari:** All versions
- **Edge:** All versions
- **Internet Explorer:** With Bootstrap 3.3.7

## 📦 Dependencies

- **jQuery:** 3.3.1
- **Bootstrap:** 3.3.7
- **Dark Mode JS:** 1.5.4 (optional)

## 🔗 Links

- **Live Demo:** [a.pages.dev](https://a.pages.dev)
- **GitHub:** [https://github.com/insoxin/API](https://github.com/insoxin/API)
- **Creator:** redy (2017-3-31)
- **License:** AGPL v3

## 📖 Documentation Index

| Document | Purpose | Best For |
|----------|---------|----------|
| [API Documentation](API_DOCUMENTATION.md) | Complete function reference | API integration |
| [Quick Reference](QUICK_REFERENCE.md) | Fast lookup tables | Quick questions |
| [Developer Guide](DEVELOPER_GUIDE.md) | Integration examples | Getting started |

## 🤝 Contributing

Please respect the original work and do not remove or modify the copyright notice. This project is licensed under AGPL v3.

## 📄 License

**License:** AGPL v3  
**Creator:** redy (2017-3-31)  
**GitHub:** https://github.com/insoxin/API  

---

*For detailed API documentation, see [API_DOCUMENTATION.md](API_DOCUMENTATION.md)*