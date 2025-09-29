# 📊 实时词云互动应用

一个适合课堂教学的实时词云互动系统，学生扫描二维码输入词语，教师端实时显示词云图。

## ✨ 功能特点

### 教师端（index.html）
- 🔗 自动生成二维码和链接
- ☁️ 实时动态词云图
- 📊 实时统计（词语数量、参与人数）
- 💾 支持保存词云图片
- 🔄 自动刷新功能
- 🗑️ 一键清空数据

### 学生端（student.html）
- 📱 移动端友好设计
- ✍️ 支持多词输入（空格、逗号分隔）
- 📌 快速填入示例
- ✅ 显示已提交词语
- 🎨 精美的动画效果

## 🚀 快速开始

### 方法1：GitHub Pages部署（推荐）

#### 步骤1：准备文件
下载以下三个文件：
- `index.html` - 教师展示页面
- `student.html` - 学生输入页面
- `README.md` - 说明文档（可选）

#### 步骤2：创建GitHub仓库
1. 登录 [GitHub](https://github.com)
2. 点击右上角 `+` → `New repository`
3. 填写信息：
   - Repository name: `wordcloud-app`
   - 选择 `Public`
   - ✅ 勾选 `Add a README file`
4. 点击 `Create repository`

#### 步骤3：上传文件

**方法A：网页上传**
1. 在仓库页面，点击 `Add file` → `Upload files`
2. 拖拽 `index.html` 和 `student.html` 到页面
3. 填写提交信息："添加词云应用"
4. 点击 `Commit changes`

**方法B：使用Git命令**
```bash
# 克隆仓库
git clone https://github.com/你的用户名/wordcloud-app.git
cd wordcloud-app

# 复制文件到仓库目录
# 将 index.html 和 student.html 复制到这个文件夹

# 提交并推送
git add index.html student.html
git commit -m "添加词云应用"
git push
```

#### 步骤4：启用GitHub Pages
1. 进入仓库设置：`Settings`
2. 左侧菜单点击 `Pages`
3. Source 设置：
   - Branch: `main`
   - Folder: `/ (root)`
4. 点击 `Save`
5. 等待1-2分钟，页面会显示你的网站地址

#### 步骤5：访问应用
你的应用地址：
```
https://你的用户名.github.io/wordcloud-app/
```

教师访问：
```
https://你的用户名.github.io/wordcloud-app/index.html
```

学生通过扫码或访问教师端生成的链接即可参与。

### 方法2：本地运行

#### 使用Python
```bash
# 在文件所在目录
python -m http.server 8000

# 访问
# 教师端: http://localhost:8000/index.html
# 学生端: http://localhost:8000/student.html?session=xxx
```

#### 使用Node.js
```bash
# 安装 http-server
npm install -g http-server

# 启动服务
http-server

# 访问显示的地址
```

#### 使用VS Code
1. 安装 `Live Server` 插件
2. 右键 `index.html` → `Open with Live Server`

## 📖 使用说明

### 教师端操作
1. 打开 `index.html`
2. 展示二维码给学生扫描
3. 或复制链接分享给学生
4. 实时查看词云图更新
5. 可以保存词云图片
6. 结束后可清空数据

### 学生端操作
1. 扫描二维码或访问链接
2. 输入昵称（可选）
3. 输入一个或多个词语
4. 点击提交
5. 查看已提交的词语

### 输入格式示例
```
创新 合作 梦想
或
创新，合作，梦想
或
创新
合作
梦想
```

## 🛠️ 技术说明

### 核心技术
- **前端**: HTML5 + CSS3 + JavaScript
- **词云生成**: D3.js + d3-cloud
- **二维码**: QRCode.js
- **数据存储**: localStorage
- **跨页面通信**: BroadcastChannel API

### 浏览器兼容性
- ✅ Chrome/Edge (推荐)
- ✅ Firefox
- ✅ Safari
- ✅ 移动端浏览器

### 数据存储
- 使用浏览器的 localStorage 存储数据
- 数据保存在本地，不会上传到服务器
- 清除浏览器缓存会丢失数据
- 每个会话有独立的数据空间

## 🎨 自定义配置

### 修改颜色主题
在 CSS 中修改渐变色：
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### 修改词云颜色
在 JavaScript 中修改调色板：
```javascript
const color = d3.scaleOrdinal()
    .range(['#667eea', '#764ba2', '#f093fb', ...]);
```

### 修改字体大小范围
```javascript
const fontScale = d3.scaleLinear()
    .domain([minFreq, maxFreq])
    .range([16, 80]); // 最小16px，最大80px
```

## 📱 在局域网中使用

### 查看本机IP地址

**Windows:**
```bash
ipconfig
# 查找 IPv4 地址，例如：192.168.1.100
```

**Mac/Linux:**
```bash
ifconfig
# 或
ip addr show
```

### 分享给学生
如果在同一WiFi/局域网：
```
http://你的IP地址:8000/index.html
例如: http://192.168.1.100:8000/index.html
```

## 🌐 外网访问方案

### 使用ngrok（内网穿透）
```bash
# 下载 ngrok: https://ngrok.com/
# 启动本地服务器后
ngrok http 8000

# 会生成公网地址，例如：
# https://abc123.ngrok.io
```

### 使用GitHub Pages（推荐）
按照上面的部署步骤，获得永久链接：
```
https://你的用户名.github.io/wordcloud-app/
```

## 💡 使用技巧

1. **多场景使用**: 每次打开教师端会自动生成新的会话ID，数据互不干扰
2. **保存词云**: 点击"保存图片"按钮可下载PNG格式词云图
3. **数据管理**: 建议每次活动结束后清空数据
4. **最佳实践**: 提前测试链接是否可访问
5. **网络要求**: 学生需能访问教师端所在的网络

## 🔧 常见问题

### Q: 学生提交后，教师端没有显示？
A: 请检查：
1. 学生和教师是否访问的同一个会话链接
2. 刷新教师端页面
3. 检查浏览器是否支持 localStorage

### Q: 二维码生成失败？
A: 确保通过 HTTP 服务器访问，不能用 `file://` 协议

### Q: 词云不显示中文？
A: 已使用"Microsoft YaHei"字体，应该正常显示中文

### Q: 数据会保存多久？
A: 数据保存在浏览器本地，除非清除浏览器缓存，否则会一直保留

### Q: 可以同时进行多个词云活动吗？
A: 可以！每次打开教师端会生成新的会话ID，数据完全独立

## 📄 许可证

MIT License - 自由使用、修改和分发

## 🤝 贡献

欢迎提交问题和改进建议！

## 📧 联系方式

如有问题，欢迎通过GitHub Issues反馈。

---

**祝你使用愉快！🎉**
