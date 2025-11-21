# 🎨 GitHub个人主页配置指南

## 📋 目录
- [快速开始](#快速开始)
- [基础设置](#基础设置)
- [GitHub Actions设置](#github-actions设置)
- [高级功能](#高级功能)
- [故障排除](#故障排除)

---

## 🚀 快速开始

### 步骤 1: 创建特殊仓库
1. 在GitHub上创建一个与你的用户名**完全相同**的仓库
   - 例如，如果你的用户名是 `KillerPQY`，仓库名也必须是 `KillerPQY`
2. 设置仓库为 **Public**（公开）
3. 勾选 "Add a README file"

### 步骤 2: 替换用户名
在 [`README.md`](README.md) 中，将所有 `KillerPQY` 替换为你的GitHub用户名：
- 使用编辑器的"查找和替换"功能
- 快捷键：`Ctrl+H` (Windows/Linux) 或 `Cmd+H` (Mac)

### 步骤 3: 自定义内容
根据以下指南自定义各个部分。

---

## ⚙️ 基础设置

### 1. 个人信息修改

#### 欢迎横幅
```html
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=180&section=header&text=你的文字&fontSize=42&fontColor=fff&animation=twinkling&fontAlignY=32" />
```
**参数说明：**
- `type`: 横幅类型 (waving, wave, cylinder, rounded, soft, rect, slice等)
- `color`: 颜色方案 (gradient, auto, 或十六进制颜色)
- `customColorList`: 自定义渐变颜色列表
- `height`: 高度
- `text`: 显示的文字（需要URL编码，空格用%20代替）
- `fontSize`: 字体大小
- `animation`: 动画效果 (twinkling, fadeIn, scaleIn, blink)

**更多参数**: https://github.com/kyechan99/capsule-render

#### 打字机效果
```html
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&duration=3000&pause=1000&color=3DAEF7&center=true&vCenter=true&multiline=false&repeat=true&width=600&height=60&lines=第一行文字;第二行文字;第三行文字" />
```
**参数说明：**
- `lines`: 要显示的文字（用`;`分隔多行）
- `duration`: 每个字符打字速度（毫秒）
- `pause`: 每行完成后的暂停时间
- `color`: 文字颜色
- `font`: 字体（需要URL编码）

**自定义工具**: https://readme-typing-svg.demolab.com/demo/

### 2. 关于我部分

修改 [`README.md`](README.md) 中的JavaScript代码块：
```javascript
const KillerPQY = {
    pronouns: "He" | "Him",  // 修改为你的代词
    location: "🇨🇳 China",   // 修改为你的位置
    code: ["JavaScript", "Python"],  // 修改为你使用的语言
    // ... 其他信息
};
```

### 3. 技术栈徽章

#### 自定义徽章
```html
<img src="https://img.shields.io/badge/技术名称-颜色代码?style=for-the-badge&logo=logo名称&logoColor=white" />
```

**示例：**
```html
<!-- React -->
<img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black" />

<!-- 自定义技术 -->
<img src="https://img.shields.io/badge/MyTech-FF6B6B?style=for-the-badge" />
```

**查找Logo**: https://simpleicons.org/
**配色方案**: https://brandcolors.net/

### 4. GitHub统计卡片

#### GitHub Stats
```html
<img src="https://github-readme-stats.vercel.app/api?username=你的用户名&show_icons=true&theme=主题名&include_all_commits=true&count_private=true" />
```

**可用主题：**
- `tokyonight` (东京之夜 - 深蓝紫)
- `dracula` (德古拉 - 深紫粉)
- `radical` (激进 - 粉紫渐变)
- `merko` (墨绿)
- `gruvbox` (复古黄棕)
- `dark` (深色)
- `cobalt` (钴蓝)
- `synthwave` (合成波 - 霓虹粉紫)
- `highcontrast` (高对比度)
- `github_dark` (GitHub深色)

**自定义主题：**
```html
<img src="https://github-readme-stats.vercel.app/api?username=你的用户名&show_icons=true&bg_color=0D1117&title_color=58A6FF&icon_color=1F6FEB&text_color=C9D1D9&border_color=30363D" />
```

**参数说明：**
- `bg_color`: 背景颜色
- `title_color`: 标题颜色
- `icon_color`: 图标颜色
- `text_color`: 文字颜色
- `border_color`: 边框颜色
- `hide_border=true`: 隐藏边框

#### 最常用语言
```html
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=你的用户名&layout=compact&langs_count=8&theme=tokyonight" />
```

**布局选项：**
- `compact`: 紧凑型
- `donut`: 甜甜圈图
- `donut-vertical`: 垂直甜甜圈
- `pie`: 饼图

#### Streak Stats（连续贡献）
```html
<img src="https://github-readme-streak-stats.herokuapp.com/?user=你的用户名&theme=tokyonight" />
```

#### 活动图
```html
<img src="https://github-readme-activity-graph.vercel.app/graph?username=你的用户名&theme=tokyo-night" />
```

**可用主题：**
- `github`, `github-compact`, `github-dark`
- `xcode`, `rogue`, `merko`
- `tokyo-night`, `dracula`

### 5. 精选项目

```html
<a href="https://github.com/你的用户名/仓库名">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=你的用户名&repo=仓库名&theme=tokyonight" />
</a>
```

**注意：** 将 `仓库名` 替换为你想展示的项目仓库名称。

### 6. 社交媒体链接

修改 [`README.md`](README.md) 中的社交媒体部分：
```html
<a href="你的链接">
  <img src="https://img.shields.io/badge/平台名-颜色?style=for-the-badge&logo=logo名&logoColor=white" />
</a>
```

**常用社交平台：**
```html
<!-- GitHub -->
<a href="https://github.com/你的用户名">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" />
</a>

<!-- 邮箱 -->
<a href="mailto:你的邮箱@example.com">
  <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" />
</a>

<!-- Twitter/X -->
<a href="https://twitter.com/你的用户名">
  <img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" />
</a>

<!-- LinkedIn -->
<a href="https://linkedin.com/in/你的用户名">
  <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" />
</a>

<!-- 微信 -->
<img src="https://img.shields.io/badge/微信-07C160?style=for-the-badge&logo=wechat&logoColor=white" />

<!-- 知乎 -->
<a href="https://zhihu.com/people/你的ID">
  <img src="https://img.shields.io/badge/知乎-0084FF?style=for-the-badge&logo=zhihu&logoColor=white" />
</a>

<!-- B站 -->
<a href="https://space.bilibili.com/你的UID">
  <img src="https://img.shields.io/badge/哔哩哔哩-00A1D6?style=for-the-badge&logo=bilibili&logoColor=white" />
</a>
```

---

## 🔧 GitHub Actions设置

### 1. 自动更新博客文章

#### 前置要求
- 你的博客需要有RSS feed（如：`https://your-blog.com/feed.xml`）

#### 设置步骤
1. 确保 [`.github/workflows/blog-post-workflow.yml`](.github/workflows/blog-post-workflow.yml) 文件存在
2. 修改 `feed_list` 为你的博客RSS地址：
   ```yaml
   feed_list: "https://your-blog.com/feed.xml"
   ```
3. 在 [`README.md`](README.md) 中保留以下注释标记：
   ```html
   <!-- BLOG-POST-LIST:START -->
   <!-- BLOG-POST-LIST:END -->
   ```

**支持的平台：**
- Dev.to: `https://dev.to/feed/你的用户名`
- Medium: `https://medium.com/feed/@你的用户名`
- 个人博客: `https://your-blog.com/feed.xml`
- 掘金: 需要自建RSS服务

### 2. WakaTime编程时长统计

#### 前置要求
1. 注册 [WakaTime](https://wakatime.com/)
2. 安装WakaTime编辑器插件（VS Code、IntelliJ等）
3. 获取WakaTime API Key

#### 设置步骤
1. 在GitHub仓库中添加Secret：
   - 进入仓库 → Settings → Secrets and variables → Actions
   - 点击 "New repository secret"
   - Name: `WAKATIME_API_KEY`
   - Value: 你的WakaTime API Key（在 https://wakatime.com/settings/api-key 获取）

2. 确保 [`.github/workflows/waka-readme.yml`](.github/workflows/waka-readme.yml) 文件存在

3. 在 [`README.md`](README.md) 中保留以下注释标记：
   ```html
   <!--START_SECTION:waka-->
   <!--END_SECTION:waka-->
   ```

### 3. 贡献蛇动画

#### 设置步骤
1. 确保 [`.github/workflows/snake.yml`](.github/workflows/snake.yml) 文件存在
2. 手动触发一次工作流：
   - 进入仓库 → Actions → "Generate Snake Animation"
   - 点击 "Run workflow"
3. 等待工作流完成，蛇动画会自动生成到 `output` 分支

**注意：** 首次运行可能需要几分钟。

### 4. 启用GitHub Actions权限

确保GitHub Actions有写入权限：
1. 进入仓库 → Settings → Actions → General
2. 滚动到 "Workflow permissions"
3. 选择 "Read and write permissions"
4. 勾选 "Allow GitHub Actions to create and approve pull requests"
5. 保存更改

---

## 🎨 高级功能

### 1. 访客计数器

**基础样式：**
```html
<img src="https://komarev.com/ghpvc/?username=你的用户名&style=flat-square&color=blue" />
```

**可用样式：**
- `flat` - 扁平
- `flat-square` - 扁平方形
- `for-the-badge` - 徽章样式
- `plastic` - 塑料质感

**可用颜色：**
`brightgreen`, `green`, `yellowgreen`, `yellow`, `orange`, `red`, `blue`, `lightgrey`, `blueviolet`, `ff69b4`

### 2. GitHub Profile Trophy（成就奖杯）

```html
<img src="https://github-profile-trophy.vercel.app/?username=你的用户名&theme=tokyonight&no-frame=true&column=7" />
```

**参数说明：**
- `column`: 每行显示的奖杯数量
- `margin-w`: 水平间距
- `margin-h`: 垂直间距
- `no-frame`: 无边框
- `no-bg`: 无背景

**可用主题：** 与github-readme-stats相同

### 3. 自定义动态引用

```html
<img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=tokyonight" />
```

**自定义引用：**
```html
<img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=tokyonight&quote=你的座右铭&author=你的名字" />
```

### 4. Spotify正在播放

需要设置Spotify API（较复杂）：
```html
<img src="https://spotify-github-profile.vercel.app/api/view?uid=你的Spotify用户ID&cover_image=true&theme=novatorem" />
```

**教程：** https://github.com/kittinan/spotify-github-profile

### 5. 自定义SVG动画

可以嵌入自定义的SVG文件：
```html
<img src="./assets/your-animation.svg" />
```

**创建工具：**
- [SVGator](https://www.svgator.com/) - SVG动画编辑器
- [Figma](https://www.figma.com/) - 设计工具（可导出SVG）

### 6. Metrics嵌入式仪表板

需要设置GitHub Token：
```html
<img src="https://metrics.lecoq.io/你的用户名?template=classic&base.header=0&base.activity=0&base.community=0&base.repositories=0&base.metadata=0&achievements=1&achievements.threshold=C&achievements.secrets=true&achievements.display=detailed&achievements.limit=0&config.timezone=Asia%2FShanghai" />
```

**配置工具：** https://metrics.lecoq.io/

---

## 🎨 配色方案推荐

### 深色主题
```css
背景: #0D1117
标题: #58A6FF
图标: #1F6FEB
文字: #C9D1D9
边框: #30363D
```

### 蓝紫渐变
```css
背景: linear-gradient(135deg, #667eea 0%, #764ba2 100%)
强调: #667eea
次要: #764ba2
```

### 绿色清新
```css
背景: #1a1a2e
主色: #16213e
强调: #0f3460
高亮: #00f2fe
```

### 粉紫梦幻
```css
背景: #2d1b4e
主色: #6a4c93
强调: #a06cd5
高亮: #f72585
```

---

## 🔧 故障排除

### 问题1: 统计卡片不显示
**解决方案：**
- 确保仓库是Public
- 检查用户名拼写是否正确
- 清除浏览器缓存或在隐私模式下查看
- 等待几分钟，Vercel部署可能需要时间

### 问题2: GitHub Actions失败
**解决方案：**
- 检查Actions权限设置
- 确认Secrets配置正确
- 查看Actions日志了解具体错误
- 确保YAML文件缩进正确

### 问题3: 图片无法加载
**解决方案：**
- 检查URL是否正确
- 确认图片服务没有被墙
- 尝试使用CDN镜像
- 检查网络连接

### 问题4: 蛇动画不显示
**解决方案：**
- 确保output分支存在
- 手动触发一次snake workflow
- 检查GitHub Pages设置
- 等待几分钟让Actions完成

---

## 📚 有用资源

### 徽章和图标
- [Shields.io](https://shields.io/) - 徽章生成器
- [Simple Icons](https://simpleicons.org/) - 品牌Logo SVG
- [Devicon](https://devicon.dev/) - 开发者图标库
- [Skill Icons](https://github.com/tandpfun/skill-icons) - 技能图标生成器

### 统计工具
- [GitHub Readme Stats](https://github.com/anuraghazra/github-readme-stats)
- [GitHub Readme Streak Stats](https://github.com/DenverCoder1/github-readme-streak-stats)
- [GitHub Profile Trophy](https://github.com/ryo-ma/github-profile-trophy)
- [Activity Graph](https://github.com/Ashutosh00710/github-readme-activity-graph)

### 动画效果
- [Typing SVG](https://github.com/DenverCoder1/readme-typing-svg)
- [Capsule Render](https://github.com/kyechan99/capsule-render)
- [GitHub Profile Views Counter](https://github.com/antonkomarev/github-profile-views-counter)
- [Snake Animation](https://github.com/Platane/snk)

### 自动化工具
- [Blog Post Workflow](https://github.com/gautamkrishnar/blog-post-workflow)
- [WakaTime Readme](https://github.com/athul/waka-readme)
- [GitHub Metrics](https://github.com/lowlighter/metrics)

---

## 💡 最佳实践

### 1. 保持简洁
- 不要放太多内容，重点突出
- 使用折叠section隐藏次要信息
- 保持视觉层次清晰

### 2. 移动端适配
- 使用响应式布局
- 避免过大的图片
- 测试在不同设备上的显示效果

### 3. 性能优化
- 压缩图片大小
- 使用CDN加速
- 延迟加载非关键内容

### 4. 定期更新
- 及时更新技术栈
- 添加新完成的项目
- 保持内容新鲜度

### 5. 个性化
- 展示真实的你
- 添加独特的元素
- 保持专业性和创意性的平衡

---

## 📝 自定义清单

使用此清单确保完成所有自定义：

- [ ] 替换所有用户名为你的GitHub用户名
- [ ] 修改个人介绍信息
- [ ] 更新技术栈徽章
- [ ] 自定义配色方案
- [ ] 设置社交媒体链接
- [ ] 替换精选项目链接
- [ ] 配置WakaTime（可选）
- [ ] 设置博客RSS（可选）
- [ ] 启用GitHub Actions
- [ ] 测试所有链接
- [ ] 检查移动端显示
- [ ] 预览最终效果

---

## 🤝 贡献

如果你发现问题或有改进建议，欢迎提交Issue或Pull Request！

---

## 📄 许可证

此模板采用 MIT 许可证。你可以自由使用、修改和分发。

---

<div align="center">
  <sub>创建于 2024 | Made with ❤️ by KillerPQY</sub>
</div>