# Function Reference Card

## 🎯 Core Functions

| Function | Purpose | Usage |
|----------|---------|-------|
| `init0()` | Initialize grid layout | `init0();` |
| `init()` | Load wallpapers from API | `init();` |

## 🗂️ Category Functions

| Function | Category | Usage |
|----------|----------|-------|
| `girls()` | Beauty/Girls | `girls();` |
| `scenery()` | Scenery | `scenery();` |
| `animation()` | Animation | `animation();` |
| `animals()` | Animals | `animals();` |
| `game()` | Gaming | `game();` |
| `machine()` | Mechanical | `machine();` |
| `paint()` | Hand-drawn | `paint();` |
| `word()` | Text/Word | `word();` |
| `visual()` | Visual | `visual();` |
| `monogatari()` | Monogatari | `monogatari();` |
| `design()` | Design | `design();` |
| `emotion()` | Emotion | `emotion();` |
| `city()` | City | `city();` |
| `film()` | Film | `film();` |
| `handsome()` | Men | `handsome();` |
| `stars()` | Celebrity | `stars();` |
| `title_image()` | Reset to default | `title_image();` |

## 🧭 Navigation Functions

| Function | Purpose | Usage |
|----------|---------|-------|
| `first()` | Go to first page | `first();` |
| `pre()` | Previous page | `pre();` |
| `next()` | Next page | `next();` |
| `random()` | Random wallpapers | `random();` |

## 🔄 Sorting Functions

| Function | Purpose | Usage |
|----------|---------|-------|
| `popular()` | Sort by popularity | `popular();` |
| `newer()` | Sort by newest | `newer();` |

## 🔧 Utility Functions

| Function | Purpose | Parameters | Returns |
|----------|---------|------------|---------|
| `include()` | Load external JS | `filename` (string) | None |
| `getChromeVersion()` | Get Chrome version | None | int or false |

## 📊 Global Variables Reference

| Variable | Type | Purpose | Example Value |
|----------|------|---------|---------------|
| `hv` | string | Image orientation | `"vertical"` |
| `a` | string | Current category ID | `"4e4d610cdf714d2966000000"` |
| `b` | number | Images per page | `48` |
| `c` | number | Pagination offset | `0` |
| `d` | string | Sort order | `"hot"` or `"new"` |
| `currentPage` | number | Current page number | `0` |
| `imgsUrl` | array | Full-size image URLs | `[]` |
| `i` | number | Loop iterator | `0` |

## 🌐 API Reference

**Endpoint**: `POST https://aibizhi.isoyu.com/v1/vertical/category/{categoryId}/vertical`

**Parameters**:
- `limit`: Number of images (default: 48)
- `skip`: Pagination offset (default: 0)
- `adult`: Include adult content (default: true)
- `first`: First request flag (default: 0)
- `order`: Sort order (default: "hot")

**Response**:
```json
{
  "res": {
    "vertical": [
      {
        "wp": "full-size-url",
        "thumb": "thumbnail-url"
      }
    ]
  }
}
```

## 🎨 CSS Classes

| Class | Purpose |
|-------|---------|
| `.img` | Image styling with blue glow |
| `.bottom_btn` | Pagination button container |
| `.div_container-fluid` | Main content container |
| `.body_view` | Content area padding |

## 📱 Bootstrap Grid Classes

| Class | Screen Size | Columns |
|-------|-------------|---------|
| `.col-lg-2` | Large (≥1200px) | 6 per row |
| `.col-md-3` | Medium (≥992px) | 4 per row |
| `.col-sm-6` | Small (≥768px) | 2 per row |
| `.col-xs-6` | Extra Small (<768px) | 2 per row |

## ⚡ Quick Commands

```javascript
// Initialize application
init0(); init();

// Switch categories
girls(); scenery(); animation();

// Navigate
first(); next(); pre(); random();

// Sort
popular(); newer();

// Get info
getChromeVersion();
```

## 🔍 Common Patterns

### Load Category
```javascript
currentPage = 0;
c = Math.floor(Math.random() * 1000) + 100;
a = "category-id";
init();
```

### Navigate Pages
```javascript
currentPage++; // or currentPage--
c = currentPage * b;
init();
```

### Change Sort Order
```javascript
d = "hot"; // or "new"
currentPage = 0;
c = 0;
init();
```

---

📖 **For detailed documentation**: [API_DOCUMENTATION.md](API_DOCUMENTATION.md)  
🚀 **For quick reference**: [QUICK_REFERENCE.md](QUICK_REFERENCE.md)