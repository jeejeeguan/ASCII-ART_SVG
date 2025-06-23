# ASCII 艺术 SVG 生成器

一个现代化的网页应用程序，用于将文本转换为 ASCII 艺术并导出为高质量的 SVG 文件，具有先进的像素到形状转换技术。

[中文版本](./README_zh.md) | [English Version](./README.md)

## 功能特性

- 🎨 **实时 ASCII 艺术生成** - 输入文字即可实时看到 ASCII 艺术效果
- 🔤 **海量字体库** - 支持 295 种不同的 ASCII 艺术字体，支持动态加载
- ⚡ **快速字体导航** - 使用方向键（↑/↓）或按钮快速切换字体
- 🎛️ **字符宽度控制** - 通过 5 种不同的宽度选项精细调整间距
- 📥 **高级 SVG 导出** - 采用像素到形状转换技术实现最佳质量导出
- 🚀 **动态字体加载** - 按需加载字体以获得更好的性能
- 📱 **响应式设计** - 在桌面和移动设备上都能完美运行
- 🎯 **用户友好界面** - 简洁现代的设计，带有字体加载指示器
- 🔄 **字体状态跟踪** - 视觉对勾标记显示哪些字体已加载

## 技术栈

- **Vue 3** - 采用组合式 API 的渐进式 JavaScript 框架
- **Vite** - 支持动态导入的快速构建工具和开发服务器
- **TailwindCSS** - 实用程序优先的 CSS 框架
- **TypeScript** - 类型安全的 JavaScript 开发
- **figlet.js** - 支持动态字体加载的 ASCII 艺术文本生成器库
- **HTML5 Canvas** - 用于精确 SVG 转换的高分辨率渲染

## 快速开始

### 环境要求

- Node.js 18+ 和 npm

### 安装步骤

1. 克隆仓库：

```sh
git clone https://github.com/jeejeeguan/ASCII-ART_SVG.git
cd ASCII-ART_SVG/ascii-art-svg
```

2. 安装依赖：

```sh
npm install
```

3. 启动开发服务器：

```sh
npm run dev
```

4. 打开浏览器并访问 `http://localhost:5173`

## 使用方法

1. **输入文字**：在输入框中输入您想要的文字
2. **选择字体**：从下拉菜单中的 295 种可用字体中选择
3. **控制宽度**：使用宽度选项调整字符间距（全宽、紧凑、压缩等）
4. **快速导航**：使用 ↑/↓ 方向键快速在字体间切换
5. **导出**：点击"导出为 SVG"按钮下载优化后的 SVG 文件

## 字符宽度选项

- **全宽（Full）**：最大字符间距
- **紧凑（Fitted）**：最小字符间距
- **控制压缩（Controlled Smushing）**：带有特定规则的受控字符重叠
- **通用压缩（Universal Smushing）**：通用字符重叠规则
- **默认（Default）**：标准 figlet 间距

## 键盘快捷键

- `↑` （向上箭头）：切换到上一个字体
- `↓` （向下箭头）：切换到下一个字体

## 字体库

应用程序包含 **295 种 ASCII 艺术字体**，支持动态加载，包括：

- **经典字体**：Standard、Big、Block、Bubble、Digital、Doom
- **艺术字体**：Ghost、Graffiti、Star Wars、Rammstein、Hollywood
- **技术字体**：Binary、Hex、Morse、Computer、Electronic
- **装饰字体**：Flower Power、Heart Left/Right、Hieroglyphs
- **3D 字体**：3-D、3D Diagonal、Banner3-D、Isometric 系列
- **脚本字体**：Cursive、Calvin S、Script、Caligraphy
- **以及其他 270+ 种字体！**

字体在选择时动态加载，优化了初始加载时间和内存使用。

## 开发命令

### 开发环境编译和热重载

```sh
npm run dev
```

### 生产环境类型检查、编译和压缩

```sh
npm run build
```

### 仅类型检查

```sh
npm run type-check
```

### ESLint 代码检查

```sh
npm run lint
```

### Prettier 代码格式化

```sh
npm run format
```

### 预览生产构建

```sh
npm run preview
```

## 高级功能

### 动态字体加载

- 使用 Vite 的动态导入按需加载字体
- 通过仅加载必要字体来优化初始页面加载
- 在 UI 中跟踪和显示字体加载状态
- 支持所有 295 种 figlet 字体，具有适当的错误处理

### SVG 导出技术

- **高分辨率 Canvas 渲染**：使用 2x 像素比率进行精确测量
- **像素到形状转换**：将渲染的文本转换为优化的 SVG 矩形
- **矩形合并算法**：合并相邻像素以获得最佳文件大小
- **抗锯齿处理**：适当的阈值检测以实现平滑边缘
- **自动调整大小**：根据实际内容计算 SVG 尺寸

### 性能优化

- 字体文件的延迟加载
- 响应式字体状态跟踪
- 高效的 SVG 生成，最小文件大小
- 不阻塞的响应式 UI 更新

## 许可证

本项目采用 MIT 许可证。
