# Three.js + occt-import-js STP 查看器

基于 **Three.js** 和 **occt-import-js** 的完全免费开源的 STP 3D 模型查看器！

## ✨ 特性

- 🎯 **完全免费开源** - 无需付费，无需授权
- 🚀 **Three.js 引擎** - 业界最流行的 WebGL 3D 库
- 🔧 **occt-import-js** - OpenCASCADE 的 WebAssembly 版本，专业解析 STP/STEP
- 🎮 **丰富的交互** - 旋转、缩放、平移、自动旋转
- 📊 **实时统计** - 显示顶点数、三角形数、对象数
- 💡 **美观的 UI** - 现代化的深色主题界面
- ⌨️ **快捷键支持** - R 重置视角，F 适配视图

## 📁 文件说明

```
stp-viewer-demo/
├── index-threejs.html      # Three.js 版本的主页面（推荐使用！）
├── occt-import-js.js       # OCCT 导入库（WebAssembly）
├── page101.stp            # 示例 STP 模型文件
├── README-ThreeJS.md      # 本文档
└── README.md              # 原版说明
```

## 🚀 快速开始

### 1. 确认文件

确保以下文件都在同一目录下：
- `index-threejs.html`
- `occt-import-js.js`
- `page101.stp`（或你自己的 STP 文件）

### 2. 修改模型路径（如果需要）

如果要加载其他 STP 文件，编辑 `index-threejs.html`：

```javascript
// 找到这一行，修改为你的 STP 文件路径
const stpFilePath = './page101.stp';
```

### 3. 启动本地服务器

**重要**：由于涉及到文件加载和 WebAssembly，必须使用本地服务器运行，不能直接双击打开 HTML 文件！

#### 方法一：使用 Python（推荐）

```bash
# 进入项目目录
cd /home/ubuntu/.openclaw/workspace/stp-viewer-demo

# Python 3
python3 -m http.server 8080

# 或 Python 2
python -m SimpleHTTPServer 8080
```

#### 方法二：使用 Node.js

```bash
# 安装 http-server（如果没有）
npm install -g http-server

# 启动服务器
http-server -p 8080
```

#### 方法三：使用 VS Code

1. 安装 "Live Server" 插件
2. 右键点击 `index-threejs.html`
3. 选择 "Open with Live Server"

### 4. 访问页面

在浏览器中打开：
```
http://localhost:8080/index-threejs.html
```

## 🎮 使用说明

### 鼠标操作

| 操作 | 说明 |
|------|------|
| 左键拖拽 | 旋转模型 |
| 滚轮 | 缩放模型 |
| 右键拖拽 | 平移模型 |

### 按钮控制

- **线框模式** - 切换实体/线框显示
- **自动旋转** - 开启/关闭自动旋转
- **重置视角** - 恢复默认视角
- **适配视图** - 自动缩放以完整显示模型

### 快捷键

- **R** - 重置视角
- **F** - 适配视图

## 🔧 技术架构

### 核心组件

1. **Three.js** - 3D 渲染引擎
   - CDN: https://cdn.jsdelivr.net/npm/three@0.157.0
   - 负责场景、相机、渲染器、光照等

2. **OrbitControls** - 轨道控制器
   - 提供流畅的旋转、缩放、平移交互

3. **occt-import-js** - STP 解析器
   - OpenCASCADE 的 WebAssembly 版本
   - 专业解析 STP/STEP CAD 格式
   - 将 STP 转换为三角形网格

### 工作流程

```
STP 文件 → occt-import-js 解析 → 三角形网格 → Three.js 渲染
```

## 📝 自定义配置

### 修改模型文件

```javascript
// 在 index-threejs.html 中找到这一行
const stpFilePath = './your-model.stp';
```

### 修改主题颜色

```css
/* 修改渐变色背景 */
background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);

/* 修改主题色 */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### 修改模型材质

```javascript
// 在代码中找到这部分
const material = new THREE.MeshPhongMaterial({
    color: 0x667eea,        // 修改颜色
    shininess: 100,            // 修改光泽度
    specular: 0x444444,        // 修改高光色
    side: THREE.DoubleSide
});
```

## 🐛 常见问题

### Q: 页面空白或报错 "occtImportJs is not defined"
A: 检查 `occt-import-js.js` 文件是否在同一目录下，并且文件名正确。

### Q: 报错 "Failed to fetch" 或无法加载 STP 文件
A: 
1. 确保使用本地服务器运行（不要直接双击 HTML）
2. 检查 STP 文件路径是否正确
3. 检查浏览器控制台的网络请求

### Q: 模型加载很慢
A: 
- STP 文件越大，解析时间越长
- 这是正常现象，因为 OCCT 解析很复杂
- 可以查看浏览器控制台的进度

### Q: 模型显示不完整或有错误
A: 
- 尝试用其他软件打开 STP 文件，确认文件本身没问题
- 检查模型是否有复杂的曲面或几何体

### Q: 如何获取 occt-import-js？
A: 
- GitHub: https://github.com/ykob/occt-import-js
- 可以从 Release 页面下载预构建版本

## 📚 相关资源

- **Three.js 官网**: https://threejs.org/
- **Three.js 文档**: https://threejs.org/docs/
- **occt-import-js**: https://github.com/ykob/occt-import-js
- **OpenCASCADE**: https://www.opencascade.com/

## 🎯 优势对比

| 特性 | 本方案（Three.js + occt） | 其他付费方案 |
|------|------------------------|------------|
| 费用 | 🆓 完全免费 | 💰 需要付费 |
| 开源 | ✅ 完全开源 | ❌ 闭源 |
| STP 解析 | ✅ 专业 OCCT 引擎 | ✅ 专业引擎 |
| 交互性 | ✅ 丰富 | ✅ 丰富 |
| 可定制 | ✅ 高度可定制 | ⚠️ 有限 |
| 隐私 | ✅ 本地处理 | ⚠️ 可能上传 |

## 🎉 总结

这是一个**完全免费、完全开源**的方案，功能强大，可以满足大多数 STP 模型查看需求！

- ✅ 无需付费
- ✅ 无需授权
- ✅ 本地处理，保护隐私
- ✅ 代码完全可定制
- ✅ 使用业界标准的 Three.js

---

**祝你使用愉快！** 🦞✨
