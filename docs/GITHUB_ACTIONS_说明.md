# 📖 GitHub Actions 工作流详解

## 什么是 GitHub Actions？

GitHub Actions 是 GitHub 提供的**自动化工具**，可以让你的仓库自动执行各种任务，比如：
- 🔄 定时更新内容
- 🧪 自动测试代码
- 📦 自动部署项目
- 🎨 生成动态内容

在 `.github/workflows` 文件夹下的文件都是 GitHub Actions 的**配置文件**，告诉 GitHub 要做什么、什么时候做。

---

## 📁 我们创建的三个工作流

### 1️⃣ [`blog-post-workflow.yml`](.github/workflows/blog-post-workflow.yml) - 博客文章自动更新

#### 🎯 作用
自动从你的博客获取最新文章，并更新到 README.md 中。

#### ⚙️ 工作原理
```yaml
name: Latest blog post workflow

on:
  schedule:
    - cron: '0 0 * * *'  # 每天UTC时间0点（北京时间早上8点）运行
  workflow_dispatch:      # 也可以手动触发

jobs:
  update-readme-with-blog:
    runs-on: ubuntu-latest  # 在Ubuntu虚拟机上运行
    steps:
      - name: Checkout
        uses: actions/checkout@v3  # 拉取你的代码
        
      - name: Pull in blog posts
        uses: gautamkrishnar/blog-post-workflow@v1  # 使用博客工作流
        with:
          comment_tag_name: "BLOG-POST-LIST"
          feed_list: "你的博客RSS地址"
          max_post_count: 5  # 最多显示5篇文章
```

#### 📝 需要的配置

1. **在 README.md 中添加标记**：
```html
## 📝 最新博客文章

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->
```

2. **修改博客RSS地址**（第21行）：
```yaml
feed_list: "https://your-blog.com/feed.xml"
```

#### 💡 支持的博客平台
- **个人博客**：`https://your-blog.com/feed.xml`
- **Dev.to**：`https://dev.to/feed/your-username`
- **Medium**：`https://medium.com/feed/@your-username`
- **掘金**：需要第三方RSS服务

#### 🔄 运行时间
- **自动**：每天北京时间早上8点
- **手动**：进入 Actions → Latest blog post workflow → Run workflow

#### ✅ 效果示例
README.md 会自动更新为：
```markdown
## 📝 最新博客文章

<!-- BLOG-POST-LIST:START -->
- [如何优化React性能](https://blog.com/react-performance)
- [深入理解JavaScript闭包](https://blog.com/js-closure)
- [Docker入门指南](https://blog.com/docker-guide)
<!-- BLOG-POST-LIST:END -->
```

---

### 2️⃣ [`waka-readme.yml`](.github/workflows/waka-readme.yml) - 编程时长统计

#### 🎯 作用
显示你最近7天的编程时长统计，包括：
- 使用了哪些编程语言
- 每种语言编程了多长时间
- 占比百分比

#### ⚙️ 工作原理
```yaml
name: Waka Readme

on:
  schedule:
    - cron: '0 0 * * *'  # 每天更新一次
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - uses: athul/waka-readme@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}  # 从Secrets读取API密钥
          TIME_RANGE: last_7_days  # 显示最近7天的数据
```

#### 📝 需要的配置

**步骤1：注册 WakaTime**
1. 访问 https://wakatime.com/ 并注册账号
2. 安装 WakaTime 编辑器插件：
   - VS Code：搜索 "WakaTime" 插件
   - IntelliJ IDEA：在插件市场搜索
   - 其他编辑器：https://wakatime.com/plugins

**步骤2：获取 API Key**
1. 登录 WakaTime
2. 访问 https://wakatime.com/settings/api-key
3. 复制你的 API Key（形如：`waka_xxxxx...`）

**步骤3：添加到 GitHub Secrets**
1. 进入你的仓库 → Settings（设置）
2. 点击左侧 "Secrets and variables" → "Actions"
3. 点击 "New repository secret"
4. Name 填写：`WAKATIME_API_KEY`
5. Value 粘贴你的 WakaTime API Key
6. 点击 "Add secret"

**步骤4：在 README.md 中添加标记**：
```html
## ⏱️ 本周编程时长

<!--START_SECTION:waka-->
<!--END_SECTION:waka-->
```

#### ✅ 效果示例
README.md 会自动更新为：
```markdown
## ⏱️ 本周编程时长

<!--START_SECTION:waka-->
JavaScript   12 hrs 30 mins  ███████████░░░░░░  45.2%
Python       8 hrs 15 mins   ███████░░░░░░░░░░  29.8%
TypeScript   4 hrs 20 mins   ████░░░░░░░░░░░░░  15.7%
HTML/CSS     2 hrs 30 mins   ██░░░░░░░░░░░░░░░   9.3%
<!--END_SECTION:waka-->
```

#### 🎨 可自定义参数
```yaml
TIME_RANGE: all_time      # 显示所有时间的统计
TIME_RANGE: last_30_days  # 显示最近30天
TIME_RANGE: last_year     # 显示最近一年
SHOW_TITLE: false         # 隐藏标题
BLOCKS: ⣀⣄⣤⣦⣶⣷⣿          # 自定义进度条字符
```

---

### 3️⃣ [`snake.yml`](.github/workflows/snake.yml) - 贡献蛇动画

#### 🎯 作用
生成一个**吃掉你的 GitHub 贡献图**的贪吃蛇动画，超级酷炫！

#### ⚙️ 工作原理
```yaml
name: Generate Snake Animation

on:
  schedule:
    - cron: "0 */12 * * *"  # 每12小时运行一次
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3  # 使用蛇动画生成器
        with:
          github_user_name: ${{ github.repository_owner }}  # 自动获取用户名
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
      
      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output  # 推送到output分支
          build_dir: dist
```

#### 📝 需要的配置

**步骤1：启用 GitHub Actions 写入权限**
1. 进入仓库 → Settings → Actions → General
2. 滚动到 "Workflow permissions"
3. 选择 **"Read and write permissions"**
4. 勾选 "Allow GitHub Actions to create and approve pull requests"
5. 保存

**步骤2：手动运行一次**
1. 进入仓库 → Actions 标签
2. 点击左侧 "Generate Snake Animation"
3. 点击右侧 "Run workflow" → "Run workflow"
4. 等待几分钟完成（首次可能需要5-10分钟）

**步骤3：在 README.md 中使用**
```html
<div align="center">
  <img src="https://raw.githubusercontent.com/你的用户名/你的用户名/output/github-contribution-grid-snake-dark.svg" alt="snake animation" />
</div>
```

#### ✅ 效果
会在你的 README 中显示一个动画，小蛇在你的贡献图上爬行，"吃掉"你的贡献方块！

#### 🎨 颜色主题
- `github-contribution-grid-snake.svg` - 浅色主题
- `github-contribution-grid-snake-dark.svg` - 深色主题

---

## 🚀 如何启用这些工作流？

### 方法1：自动启用（推荐）
只要你把这些文件推送到 GitHub，它们就会自动启用。

### 方法2：手动触发
1. 进入仓库页面
2. 点击 "Actions" 标签
3. 选择要运行的工作流
4. 点击 "Run workflow"

---

## ⚙️ 通用配置说明

### 定时任务语法（Cron）
```yaml
schedule:
  - cron: '分 时 日 月 周'
```

**常用示例**：
- `'0 0 * * *'` - 每天 UTC 0点（北京时间早上8点）
- `'0 */12 * * *'` - 每12小时
- `'0 */6 * * *'` - 每6小时
- `'0 0 * * 1'` - 每周一
- `'0 0 1 * *'` - 每月1号

**注意**：GitHub Actions 使用 UTC 时间，北京时间 = UTC + 8小时

### workflow_dispatch
```yaml
workflow_dispatch:  # 允许手动触发
```
添加这个后，你可以在 Actions 页面手动运行工作流。

---

## 🔍 如何查看运行状态？

### 查看工作流运行历史
1. 进入仓库 → Actions 标签
2. 左侧选择工作流名称
3. 右侧显示所有运行记录
4. 点击任意记录查看详细日志

### 运行状态标识
- ✅ **绿色对勾**：运行成功
- ❌ **红色叉号**：运行失败
- 🟡 **黄色圆点**：正在运行
- ⚪ **灰色圆点**：等待中

---

## 🔧 常见问题排查

### 问题1：Actions 没有运行
**解决方案**：
- 检查仓库是否为 Public（公开）
- 确认文件路径正确：`.github/workflows/xxx.yml`
- 查看 Settings → Actions → General 是否启用了 Actions

### 问题2：WakaTime 统计不显示
**解决方案**：
- 确认已添加 `WAKATIME_API_KEY` Secret
- 检查 WakaTime 插件是否正常运行
- 至少编码一次后才会有数据
- Secret 名称必须完全匹配（区分大小写）

### 问题3：蛇动画生成失败
**解决方案**：
- 确认已设置 "Read and write permissions"
- 手动触发一次工作流
- 等待几分钟让 output 分支生成
- 检查用户名是否正确

### 问题4：博客文章不更新
**解决方案**：
- 检查 RSS feed 地址是否正确
- 确认 RSS feed 可以访问（在浏览器打开测试）
- 检查 README.md 中的注释标记是否正确
- 查看 Actions 日志了解具体错误

---

## 💡 高级技巧

### 1. 禁用某个工作流
删除对应的 `.yml` 文件即可。

### 2. 修改运行频率
修改 `cron` 表达式：
```yaml
schedule:
  - cron: '0 */6 * * *'  # 改为每6小时运行
```

### 3. 添加多个博客源
```yaml
feed_list: "https://blog1.com/feed.xml,https://blog2.com/feed.xml,https://dev.to/feed/username"
```

### 4. 自定义 WakaTime 显示
```yaml
with:
  WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
  SHOW_TITLE: true          # 显示标题
  SHOW_TIME: true           # 显示总时长
  SHOW_TOTAL_CODE_TIME: true # 显示总代码时长
  TIME_RANGE: last_30_days   # 显示最近30天
  LANG_COUNT: 10            # 显示前10种语言
```

---

## 📊 工作流对比

| 工作流 | 运行频率 | 需要配置 | 难度 | 效果 |
|--------|----------|----------|------|------|
| 博客文章 | 每天1次 | RSS地址 | ⭐ | 自动更新文章列表 |
| 编程统计 | 每天1次 | WakaTime API | ⭐⭐ | 显示编程时长统计 |
| 蛇动画 | 每12小时 | 写入权限 | ⭐⭐⭐ | 酷炫动画效果 |

---

## 🎓 学习资源

### 官方文档
- [GitHub Actions 文档](https://docs.github.com/en/actions)
- [WakaTime 文档](https://wakatime.com/help)
- [Cron 表达式](https://crontab.guru/)

### 相关项目
- [Blog Post Workflow](https://github.com/gautamkrishnar/blog-post-workflow)
- [WakaTime Readme](https://github.com/athul/waka-readme)
- [Snake Animation](https://github.com/Platane/snk)

---

## ✅ 快速检查清单

设置完成后，使用此清单确认：

- [ ] 文件已推送到 GitHub
- [ ] Actions 已启用（Settings → Actions）
- [ ] WakaTime API Key 已添加到 Secrets
- [ ] 已修改博客 RSS 地址
- [ ] README.md 中有对应的注释标记
- [ ] 已设置 Actions 写入权限
- [ ] 手动运行一次蛇动画工作流
- [ ] 所有工作流运行成功（绿色对勾）
- [ ] README.md 显示正确

---

## 🎯 总结

这三个 GitHub Actions 工作流让你的个人主页**自动化、动态化**：

1. **博客文章自动更新** - 展示你的最新内容，无需手动维护
2. **编程时长统计** - 展示你的努力和专业性
3. **贡献蛇动画** - 增加视觉吸引力，让页面更生动

**最大的优势**：一次设置，永久自动更新，展示你的持续活跃度！

---

<div align="center">
  <sub>需要帮助？查看 <a href="SETUP_GUIDE.md">完整配置指南</a> 或提交 Issue</sub>
</div>