# 🎤 孩子英文自我介绍 - 二维码语音系统

一个简单高效的系统，为幼儿园/小学孩子创建专属语音二维码，扫码即可自动播放孩子的英文自我介绍。

## 📋 功能特性

✅ 一键生成二维码  
✅ 扫码自动播放对应孩子的音频  
✅ 支持下载和打印二维码  
✅ 音频预览功能  
✅ 响应式设计，支持手机扫描  
✅ 无需后端服务，纯静态页面  

## 📁 项目结构

```
kids-voice-qrcode/
├── index.html              # 二维码生成工具页面
├── play.html               # 播放页面（扫码打开）
├── audios/                 # 音频文件夹
│   ├── xiaoming.mp3        # 小明的英文自我介绍
│   ├── xiaohong.mp3        # 小红的英文自我介绍
│   ├── xiaogang.mp3        # 小刚的英文自我介绍
│   ├── xiaoli.mp3          # 小丽的英文自我介绍
│   └── xiaowang.mp3        # 小王的英文自我介绍
└── README.md               # 本文件
```

## 🚀 快速开始

### 1. 启用 GitHub Pages

在仓库设置中：
- 进入 **Settings** → **Pages**
- 选择 **Branch: main** 和 **Folder: / (root)**
- 点击 **Save**
- 几分钟后会得到网站URL：`https://mvptracy.github.io/kids-voice-qrcode/`

### 2. 添加孩子的音频

1. 将孩子的MP3文件放在 `audios/` 文件夹中
2. 文件名格式：孩子的中文名字，如 `xiaoming.mp3`
3. 在 `index.html` 和 `play.html` 中的 `children` 对象里添加孩子信息

**例如添加新孩子"小陈"：**

在 `index.html` 中找到这段代码：
```javascript
const children = {
    xiaoming: { name: '小明', filename: 'xiaoming.mp3', displayName: '小明 (Xiaoming)' },
    xiaohong: { name: '小红', filename: 'xiaohong.mp3', displayName: '小红 (Xiaohong)' },
    // ... 其他孩子
    xiaochen: { name: '小陈', filename: 'xiaochen.mp3', displayName: '小陈 (Xiaochen)' }  // 新增
};
```

同时在 `index.html` 的 `<select>` 标签中添加：
```html
<option value="xiaochen">小陈 (Xiaochen)</option>
```

在 `play.html` 中的 `children` 对象中也要添加：
```javascript
const children = {
    '小明': { filename: 'xiaoming.mp3', displayName: '小明 (Xiaoming)' },
    '小红': { filename: 'xiaohong.mp3', displayName: '小红 (Xiaohong)' },
    // ... 其他孩子
    '小陈': { filename: 'xiaochen.mp3', displayName: '小陈 (Xiaochen)' }  // 新增
};
```

## 📱 使用流程

### 🖥️ 老师/管理员流程

1. 访问：`https://mvptracy.github.io/kids-voice-qrcode/`
2. 从下拉列表中选择孩子名字
3. 预听音频确认无误
4. 点击 **✨ 生成二维码**
5. 点击 **⬇️ 下载二维码** 或 **🖨️ 打印**
6. 将二维码打印贴在孩子的自画像旁边

### 📱 访客/家长流程

1. 用手机相机或微信扫描二维码
2. 自动打开播放页面
3. 点击播放按钮即可听到孩子的英文自我介绍

## 🎙️ 音频要求

- **格式**：MP3（推荐）、WAV、M4A 等常见音频格式
- **时长**：10-60 秒
- **质量**：清晰、无明显噪音
- **大小**：建议 < 5MB（每个文件）
- **命名**：与孩子中文名字对应，如 `xiaoming.mp3`、`xiaohong.mp3` 等

## 🔧 配置说明

### 修改孩子列表

**在 `index.html` 中：**

找到这个部分：
```javascript
const children = {
    xiaoming: { name: '小明', filename: 'xiaoming.mp3', displayName: '小明 (Xiaoming)' },
    // ...
};
```

参数说明：
- `name`：孩子的中文名字（用于play.html的URL参数）
- `filename`：音频文件名
- `displayName`：在下拉列表中显示的名字

同时更新 HTML 中的 `<select>` 下拉菜单。

**在 `play.html` 中：**

找到这个部分：
```javascript
const children = {
    '小明': { filename: 'xiaoming.mp3', displayName: '小明 (Xiaoming)' },
    // ...
};
```

这里的 key 必须与 `index.html` 中 `name` 的值相同。

## ❓ 常见问题

**Q: 扫码后打不开页面？**  
A: 检查 GitHub Pages 是否已启用，URL 是否正确

**Q: 音频无法播放？**  
A: 检查文件是否放在 `audios/` 文件夹，文件名是否正确，浏览器是否支持该格式

**Q: 如何修改二维码大小？**  
A: 在 `index.html` 中找到 `QRCode.toCanvas()` 部分，修改 `width: 350` 的值

**Q: 能否自动播放？**  
A: 大多数浏览器不允许自动播放，需要用户点击播放按钮。这是浏览器的安全策略。

## 📝 自定义配置

### 修改颜色主题

在 `index.html` 和 `play.html` 的 CSS 中，修改这些颜色值：
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);  /* 改这里 */
```

### 修改页面标题

修改 HTML 中的 `<title>` 标签内容

## 🌐 部署到其他平台

除了 GitHub Pages，还可以部署到：
- Vercel
- Netlify
- Surge.sh
- Firebase Hosting

只需上传整个文件夹即可。

## 📞 技术支持

如有问题，请联系项目管理员。

---

**祝所有小朋友们英文学习进步！** 🌟