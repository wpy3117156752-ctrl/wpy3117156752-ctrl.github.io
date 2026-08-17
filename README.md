# 📱 图片识别出入库系统 - 项目说明

## 🎯 项目已转换为：纯 HTML5 + LocalStorage 单文件应用

✅ 无需 npm / 无需 node_modules / 无需任何打包工具  
✅ 双击 `index.html` 即可在电脑浏览器中运行  
✅ 直接用手机浏览器打开也能用  

---

## 📲 3 种方式让它在手机上像 APP 一样运行

### 方式 1️⃣：安卓手机安装为本地 APP（推荐 - 无需联网）

**最简方案：使用 "PWA 打包工具" 在线转 APK**

1. 把 `index.html` 上传到一个能联网的地方，例如：
   - **GitHub Pages**（免费，推荐）
   - 或者上传到您自己的服务器/对象存储
2. 打开在线 PWA → APK 打包网站：https://www.pwabuilder.com/
3. 输入您的网址 → 点击 **"Package For Stores"** → 选择 **Android**
4. 下载生成的 APK，传到手机安装即可

### 方式 2️⃣：手机浏览器直接访问（最简单）

1. 把 `index.html` 复制到手机（通过微信/QQ/邮箱）
2. 用手机浏览器（Chrome / 华为浏览器 / 小米浏览器）打开
3. 浏览器菜单 → **"添加到主屏幕"**
4. 主屏幕上会出现一个 APP 图标，点击就像 APP 一样运行（全屏、无地址栏）

### 方式 3️⃣：使用 HBuilderX 打包（最专业）

如果以后想做真正的原生 APK：

1. 下载 [HBuilderX](https://www.dcloud.io/hbuilderx.html)（DCloud 官方免费 IDE）
2. 文件 → 新建项目 → **5+App**（HTML5+ 项目）
3. 把 `index.html` 放到项目根目录，替换默认首页
4. 菜单 → **发行 → 原生 APP-云打包**
5. 选择 Android → 生成 APK → 自动下载

> 这种方法需要您在 DCloud 实名认证，但生成的 APK 可以安装到任何安卓手机。

---

## 🚀 当前功能

- ✅ 入库 / 出库两种模式切换
- ✅ 拍照识别商品编号（演示模式自动填入示例编号）
- ✅ 手动输入商品编号
- ✅ 实时库存清单与统计
- ✅ 历史记录保存（localStorage 本地存储）
- ✅ 数据持久化（关闭浏览器后保留）
- ✅ 移动端优化的 UI 设计
- ✅ 后置摄像头拍照（capture="environment"）

---

## 📂 文件结构

```
flower/
├── index.html      # 主程序（双击就能在浏览器打开）
├── App.vue         # 备用源码（与 index.html 内容一致）
├── README.md       # 本说明文件
├── apk-build-guide.md   # APK 打包详细指南
└── static/         # 静态资源（图标等）
```

## ⚙️ 识别功能说明

当前 **recognizeFromImage()** 是演示版，会自动填入示例编号。  
要接入真实 OCR，请在 `index.html` 中替换该函数：

```javascript
function recognizeFromImage(dataUrl) {
  showToast('🔍 正在识别图片...');
  // 替换为真实 OCR 接口调用
  fetch('https://your-ocr-api.com/recognize', {
    method: 'POST',
    body: JSON.stringify({ image: dataUrl })
  }).then(r => r.json()).then(result => {
    document.getElementById('preview-code').value = result.code;
    document.getElementById('preview-name').value = result.name;
    showToast('✅ 识别成功');
  });
}
```

推荐 OCR 服务：
- 百度 OCR（中文识别率最高）
- 腾讯云 OCR
- 阿里云 OCR
- Tesseract.js（离线，免费）
