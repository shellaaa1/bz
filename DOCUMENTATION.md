# INSO 壁纸项目开发文档

> 该文档面向二次开发者与站点运维人员，详细介绍了本仓库中全部对外可用的 **API / 函数 / 组件**，并给出了调用示例以及常见的使用场景与注意事项。

---

## 目录

1. [项目概览](#项目概览)
2. [文件结构](#文件结构)
3. [运行方式](#运行方式)
4. [公共 JavaScript API](#公共-javascript-api)
   1. [核心流程函数](#核心流程函数)
   2. [翻页 & 随机函数](#翻页--随机函数)
   3. [分类切换函数](#分类切换函数)
   4. [排序切换函数](#排序切换函数)
   5. [浏览器兼容辅助函数](#浏览器兼容辅助函数)
5. [后端数据接口](#后端数据接口)
6. [HTML 组件与自定义样式](#html-组件与自定义样式)
7. [常见问题](#常见问题)

---

## 项目概览

本仓库实现了一个纯前端的高清壁纸浏览站点，默认语言为中文，使用开源的 **[爱壁纸 API](https://aibizhi.isoyu.com/)** 获取图片数据。站点基于 **Bootstrap 3** 与 **jQuery**，不依赖任何后端服务即可部署到静态托管平台（如 GitHub Pages、Cloudflare Pages）。

> 提示：如果需要部署到自有域名，只需将 `index.html` 与 `bz_css/`、`bz_js/` 目录一起上传即可。

---

## 文件结构

```
├── index.html          # 入口页面（含导航栏与图片网格占位）
├── bz_js/              # 业务脚本目录
│   ├── inso_appVersion.js   # 浏览器版本检测，按需加载 http/https 版图片脚本
│   ├── inso_httpimages.js   # 针对旧版浏览器的图片加载脚本
│   ├── inso_httpsimages.js  # 主力脚本（Chrome 79+ / Edge / Firefox 等现代浏览器）
│   └── inso_img.js          # 与 https 版脚本等价，本地调试可直接引用
├── bz_css/
│   └── inso_bz.css      # 站点定制样式
└── insoimg/loading.gif  # 图片占位动画
```

---

## 运行方式

1. 本地预览：
   ```bash
   # 在项目根目录启动任意静态服务器，例如：
   npm install -g http-server   # 如果你未安装 http-server
   http-server -p 8080
   # 访问 http://localhost:8080 即可
   ```

2. 生产部署：
   * 将 `index.html` 和所有静态资源上传到支持 HTTPS 的静态托管即可。
   * 如果你的托管平台强制 HTTP，可将 `index.html` 中脚本地址替换为 `bz_js/inso_httpimages.js` 版本。

---

## 公共 JavaScript API

以下 API 统一定义在 `bz_js/*.js` 中，全局可用（绑定到 `window`）。为了方便说明，以下示例默认引入 `bz_js/inso_img.js`，但同样适用于 `inso_httpsimages.js`。

### 核心流程函数

| 函数 | 说明 | 参数 | 返回值 |
|------|------|------|--------|
| `init0()` | 在页面网格区域（`#gg`）生成 48 个图片占位元素 | 无 | 无 |
| `init()` | 根据当前分类、页码等状态，向爱壁纸 API 发起 POST 请求并渲染图片 | 无 | 无 |

> **最佳实践**：开发者通常无需直接调用 `init0()` 与 `init()`，页面加载后它们已由 `$(function(){ ... })` 自动调用。只有在自定义刷新逻辑时才需要手动触发。

### 翻页 & 随机函数

| 函数 | 说明 |
|-------|------|
| `first()`  | 返回第一页（重置 `currentPage = 0`）并刷新图片 |
| `pre()`    | 加载上一页；若已经是第一页则弹出提示 |
| `next()`   | 加载下一页 |
| `random()` | 随机跳转：随机生成 `skip` 参数（100–1099），常用于“随机看看”功能 |

**调用示例**：
```html
<!-- 在自定义按钮上绑定点击事件 -->
<button onclick="next()">下一页</button>
```

### 分类切换函数

每个函数对应爱壁纸 API 的一个 **分类 ID**，调用后会：
1. 重置当前页与 `skip`（随机 100–1099）；
2. 更新全局分类变量 `a`；
3. 调用 `init()` 重新拉取数据。

| 分类 | 函数名 | 分类 ID |
|------|--------|---------|
| 首页/美女 | `girls()` / `title_image()` | `4e4d610cdf714d2966000000` |
| 风景 | `scenery()` | `4e4d610cdf714d2966000002` |
| 动漫 | `animation()` | `4e4d610cdf714d2966000003` |
| 动物 | `animals()` | `4e4d610cdf714d2966000001` |
| 游戏 | `game()` | `4e4d610cdf714d2966000007` |
| 机械 | `machine()` | `4e4d610cdf714d2966000005` |
| 手绘 | `paint()` | `4e4d610cdf714d2966000004` |
| 文字 | `word()` | `5109e04e48d5b9364ae9ac45` |
| 视觉 | `visual()` | `4fb479f75ba1c65561000027` |
| 物语 | `monogatari()` | `4fb47a465ba1c65561000028` |
| 设计 | `design()` | `4fb47a195ba1c60ca5000222` |
| 情感 | `emotion()` | `4ef0a35c0569795756000000` |
| 城市 | `city()` | `4fb47a305ba1c60ca5000223` |
| 影视 | `film()` | `4e58c2570569791a19000000` |
| 男生 | `handsome()` | `4e4d610cdf714d2966000006` |
| 明星 | `stars()` | `5109e05248d5b9368bb559dc` |

**示例：自定义分类按钮**
```html
<li><a href="javascript:void(0)" onclick="city()">城市风光</a></li>
```

### 排序切换函数

| 函数 | 行为 |
|-------|------|
| `popular()` | 设置 `order = hot`（最热）并刷新 |
| `newer()`   | 设置 `order = new`（最新）并刷新 |

与分类切换类似，两函数都会重置页码然后调用 `init()`。

### 浏览器兼容辅助函数

`bz_js/inso_appVersion.js` 对低版本 Chrome（低于 79）动态加载 `inso_httpimages.js`，否则加载 `inso_httpsimages.js`。

```javascript
function include(filename) {
  const script = document.createElement('script');
  script.src  = filename;
  script.type = 'text/javascript';
  document.head.appendChild(script);
}

function getChromeVersion() {
  const matched = navigator.userAgent.match(/Chrom(e|ium)\/([0-9]+)\./);
  return matched ? parseInt(matched[2], 10) : false;
}

const version = getChromeVersion();
include(version < 79
  ? 'bz_js/inso_httpimages.js'
  : 'bz_js/inso_httpsimages.js');
```

如无兼容性需求，HTML 中可直接引入 `bz_js/inso_img.js` 以减少一次网络请求。

---

## 后端数据接口

脚本通过如下格式的 URL 获取图片数据（POST 请求）：

```
https://aibizhi.isoyu.com/v1/{orientation}/category/{categoryId}/{orientation}?limit={b}&skip={c}&adult=true&first=0&order={d}
```

* `orientation` (`hv`)：当前仅支持 `vertical`。
* `categoryId` (`a`)：由分类切换函数维护。
* `limit` (`b`)：每次加载的图片数量，默认 `48`。
* `skip` (`c`)：分页偏移量。`currentPage × b` 或随机值。
* `order` (`d`)：排序键，`hot` / `new`。

返回示例（已截断）：
```jsonc
{
  "res": {
    "vertical": [
      {
        "thumb": "https://.../small_123.jpg",
        "wp":    "https://.../wallpaper_123.jpg",
        // 其他字段省略
      }
    ]
  }
}
```

脚本逻辑仅使用其中两字段：
1. `thumb`  → 网格缩略图。
2. `wp`     → 点击后在新窗口打开的原图地址。

---

## HTML 组件与自定义样式

### 页面结构要点

```html
<nav class="navbar navbar-inverse"> ... </nav>
<div class="container-fluid div_container-fluid">
  <div id="gg" class="row"></div>     <!-- 图片网格 -->
  <div class="row bottom_btn">          <!-- 翻页按钮 -->
    <input onclick="first()"  type="button" value="首页"  class="btn btn-info">
    <input onclick="pre()"    type="button" value="上页"  class="btn btn-info">
    <input onclick="next()"   type="button" value="下页"  class="btn btn-info">
    <input onclick="random()" type="button" value="随机"  class="btn btn-info">
  </div>
</div>
```

### 自定义样式

可在 `bz_css/inso_bz.css` 中调整细节。例如修改缩略图边框颜色：
```css
.img {
  border: 1px solid #e91e63; /* 原 #1fbaf3 */
  box-shadow: 0 0 15px #e91e63;
  border-radius: 8px;
}
```

---

## 常见问题

1. **为何图片加载失败？**  
   请确认托管站点启用了 **HTTPS**，或使用 `inso_httpimages.js` 作为降级方案。

2. **如何减少首屏加载流量？**  
   将 `b`（每页图片数）从 48 调低至 24 即可，同时在 `init0()` 里调整循环次数。

3. **可否在 Node.js / React 等框架中调用？**  
   可以，但脚本依赖全局 `window` 与 `jQuery`，需自行做适配。更推荐直接使用后端接口自行开发。

---

> 如有任何疑问或改进建议，欢迎提交 Issue 或 PR！
