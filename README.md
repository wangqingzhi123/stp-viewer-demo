# 3D 模型查看器 - 支持 STP/GLB/GLTF

基于 **Three.js** 和 **occt-import-js** 的完全免费开源的 3D 模型查看器！

## ✨ 特性

- 🎯 **完全免费开源** - 无需付费，无需授权
- 🚀 **Three.js 引擎** - 业界最流行的 WebGL 3D 库
- 🔧 **occt-import-js** - OpenCASCADE 的 WebAssembly 版本，专业解析 STP/STEP
- 📦 **多格式支持** - 支持 STP/STEP、GLB、GLTF 格式
- 🎮 **丰富的交互** - 旋转、缩放、平移、自动旋转
- 📊 **实时统计** - 显示顶点数、三角形数、对象数
- 💡 **美观的 UI** - 现代化的深色主题界面
- ⌨️ **快捷键支持** - 方向键平移，R 重置视角，F 适配视图
- 🔗 **URL 参数** - 通过 `?model=文件名` 加载不同模型

## 📜 开源协议

本项目采用 **GNU Lesser General Public License v3.0 (LGPL-3.0)** 协议开源。

详见 [LICENSE](LICENSE) 文件。

## 📚 使用的开源库

- **Three.js** - MIT License - https://threejs.org/
- **occt-import-js** - LGPL-3.0 License - https://github.com/kaaes/occt-import-js

## 📁 文件说明

```
stp-viewer-demo/
├── LICENSE                    # LGPL-3.0 开源协议
├── README.md                  # 本文档
├── README-ThreeJS.md          # 旧版说明文档
├── index-standalone.html      # 主程序文件（推荐使用！）
├── js/
│   ├── three.min.js           # Three.js 非模块版
│   ├── three.module.min.js    # Three.js ES6 模块版
│   ├── OrbitControls.js       # 轨道控制器
│   ├── GLTFLoader.js          # GLB/GLTF 加载器
│   ├── occt-import-js.js      # STP 解析器
│   ├── occt-import-js.wasm    # STP 解析器 WebAssembly
│   └── utils/
│       └── BufferGeometryUtils.js  # 几何工具库
├── DragonAttenuation.glb      # 示例 GLB 模型
└── page101.stp               # 示例 STP 模型
```

## 🚀 快速开始

### 1. 确认文件

确保以下文件都在同一目录下：
- `index-standalone.html`
- `js/` 文件夹及其中的所有文件
- 你的模型文件（.stp/.glb/.gltf）

### 2. 通过 URL 参数加载模型（推荐）

```bash
# 加载默认模型
http://localhost:8080/index-standalone.html

# 加载指定 STP 模型
http://localhost:8080/index-standalone.html?model=your-model.stp

# 加载指定 GLB 模型
http://localhost:8080/index-standalone.html?model=your-model.glb

# 加载指定 GLTF 模型
http://localhost:8080/index-standalone.html?model=your-model.gltf
```

### 3. 或修改代码中的默认模型路径

编辑 `index-standalone.html`：

```javascript
// 找到这一行，修改为你的模型文件路径
const modelFilePath = './your-model.stp';
```

### 4. 启动本地服务器

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
2. 右键点击 `index-standalone.html`
3. 选择 "Open with Live Server"

### 5. 访问页面

在浏览器中打开：
```
http://localhost:8080/index-standalone.html
```

## 🎮 使用说明

### 鼠标操作

| 操作 | 说明 |
|------|------|
| 左键拖拽 | 旋转模型 |
| 滚轮 | 缩放模型 |

### 键盘操作

| 按键 | 说明 |
|------|------|
| ↑ ↓ ← → | 平移模型 |
| R | 重置视角 |
| F | 适配视图 |

### 按钮控制

- **线框模式** - 切换实体/线框显示
- **自动旋转** - 开启/关闭自动旋转
- **重置视角** - 恢复默认视角
- **适配视图** - 自动缩放以完整显示模型

## 🔧 技术架构

### 核心组件

1. **Three.js** - 3D 渲染引擎
   - 负责场景、相机、渲染器、光照等

2. **GLTFLoader** - GLB/GLTF 加载器
   - 加载 GLB 和 GLTF 格式模型

3. **occt-import-js** - STP 解析器
   - OpenCASCADE 的 WebAssembly 版本
   - 专业解析 STP/STEP CAD 格式
   - 将 STP 转换为三角形网格

### 工作流程

```
STP 文件 → occt-import-js 解析 → 三角形网格 → Three.js 渲染
GLB/GLTF 文件 → GLTFLoader 加载 → Three.js 渲染
```

## 📝 自定义配置

### 修改默认模型文件

```javascript
// 在 index-standalone.html 中找到这一行
const modelFilePath = './your-model.stp';
```

### 修改主题颜色

```css
/* 修改渐变色背景 */
background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);

/* 修改主题色 */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

## 🐛 常见问题

### Q: 页面空白或报错
A: 检查浏览器控制台（F12）查看具体错误信息。

### Q: 报错 "Failed to fetch" 或无法加载模型文件
A: 
1. 确保使用本地服务器运行（不要直接双击 HTML）
2. 检查模型文件路径是否正确
3. 检查浏览器控制台的网络请求

### Q: 模型加载很慢
A: 
- STP 文件越大，解析时间越长
- 这是正常现象，因为 OCCT 解析很复杂
- 可以查看浏览器控制台的进度

### Q: 如何获取 occt-import-js？
A: 
- GitHub: https://github.com/kaaes/occt-import-js

## 📚 相关资源

- **Three.js 官网**: https://threejs.org/
- **Three.js 文档**: https://threejs.org/docs/
- **occt-import-js**: https://github.com/kaaes/occt-import-js
- **OpenCASCADE**: https://www.opencascade.com/

## 🎯 优势对比

| 特性 | 本方案 | 其他付费方案 |
|------|--------|------------|
| 费用 | 🆓 完全免费 | 💰 需要付费 |
| 开源 | ✅ 完全开源 | ❌ 闭源 |
| 多格式 | ✅ STP/GLB/GLTF | ⚠️ 有限 |
| 隐私 | ✅ 本地处理 | ⚠️ 可能上传 |

## 🎉 总结

这是一个**完全免费、完全开源**的方案，功能强大，可以满足大多数 3D 模型查看需求！

- ✅ 无需付费
- ✅ 无需授权
- ✅ 本地处理，保护隐私
- ✅ 代码完全可定制
- ✅ 使用业界标准的 Three.js
- ✅ 支持多种 3D 格式

---

**祝你使用愉快！** 🦞✨

---

## 版权声明

Copyright (C) 2024

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
