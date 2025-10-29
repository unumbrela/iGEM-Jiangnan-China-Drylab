# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是江南大学iGEM 2025团队的项目展示网站，主题为"CytoFlow：基于AI的抗菌肽设计流程"。该网站展示了团队开发的CytoFlow框架，包含三个模型：CytoGrow（发酵优化，25%+生物量提升）、CytoGuard（活性预测，整合3个蛋白质语言模型）、CytoEvolve（序列进化，结合扩散模型和强化学习）。

## 项目架构

### 网站结构

这是一个纯静态HTML网站，采用单页应用的设计理念，全部使用英文：

```
├── index.html              # 主页：项目亮点、统计数据（25%生物量提升等）
├── pages/
│   ├── overview.html       # 项目概览：抗生素耐药危机背景、CytoFlow解决方案
│   ├── technology.html     # 技术架构：CytoGrow/CytoGuard/CytoEvolve三模块详解
│   ├── results.html        # 研究成果：25%+生物量提升、湿实验室验证
│   └── impact.html         # 社会影响：临床应用、开源贡献
├── images/
│   └── hero-bg.jpg         # 主页背景图
└── README.md
```

### 样式系统

所有页面使用内联CSS样式，遵循统一的设计系统：

**CSS变量规范：**
- `--primary-gradient`: 主色调渐变 (#667eea → #764ba2)
- `--secondary-gradient`: 次要渐变 (#ff6b6b → #feca57)
- `--success-gradient`: 成功色渐变 (#56ab2f → #a8e6cf)
- `--text-dark`: 深色文本 (#2c3e50)
- `--text-light`: 浅色文本 (#7f8c8d)
- `--bg-light`: 浅色背景 (#f8f9ff)
- `--shadow-light` / `--shadow-heavy`: 阴影效果
- `--border-radius`: 统一圆角 (12px)

**组件设计模式：**
- 导航栏：固定顶部，带滚动效果和毛玻璃背景
- 卡片系统：统一阴影、hover动画、渐变顶部边框
- 响应式断点：768px（移动端汉堡菜单）

### 外部依赖

每个页面引入以下CDN库：
- Font Awesome 6.0.0：图标系统
- AOS (Animate On Scroll) 2.3.4：滚动动画
- Particles.js 2.0.0：主页粒子背景（仅index.html）
- Chart.js 3.9.1：数据可视化（technology.html, results.html）

### 页面交互特性

**通用功能：**
- 页面转场动画（opacity fade）
- 滚动进度条
- 面包屑导航
- 响应式移动菜单
- AOS滚动动画

**主页特有功能：**
- Particles.js背景动画
- 统计数字滚动计数器（IntersectionObserver触发）
- 浮动图标动画
- Konami代码彩蛋（↑↑↓↓←→←→BA）

**图表页面（technology.html, results.html）：**
- Chart.js集成用于展示研究数据
- 响应式图表容器

## 开发工作流

### 预览网站

这是静态HTML网站，可以通过以下方式预览：

```bash
# 方法1: 使用Python内置服务器
python3 -m http.server 8000

# 方法2: 使用Node.js serve包（需先安装：npm install -g serve）
serve .

# 方法3: 直接在浏览器打开
open index.html  # macOS
xdg-open index.html  # Linux
start index.html  # Windows
```

然后访问 `http://localhost:8000`

### Git工作流

```bash
# 查看当前状态
git status

# 提交更改
git add .
git commit -m "描述更改内容"

# 推送到远程仓库
git push origin main
```

### 常见开发任务

**修改页面内容：**
- 直接编辑对应的HTML文件
- 注意保持中文简体编码（UTF-8）
- 所有页面使用 `lang="zh-CN"`

**添加新页面：**
1. 在 `pages/` 目录创建新HTML文件
2. 复用现有页面的导航栏和Footer结构
3. 保持CSS变量和组件样式一致性
4. 在 `index.html` 的快速导航区域添加链接卡片

**更新样式：**
- 样式定义在每个HTML文件的 `<style>` 标签内
- 如需全局更改，需要修改所有页面的对应CSS
- 建议未来重构为外部CSS文件以便维护

**添加图片：**
- 将图片文件放入 `images/` 目录
- 团队成员照片放入 `images/team/` 子目录
- 在HTML中使用相对路径引用：`../images/filename.jpg`

## 重要注意事项

### 内容准确性
- 核心数据：CytoGrow模型实现25%+酵母生物量提升
- CytoGuard：整合3个蛋白质语言模型+注意力机制+超图
- CytoEvolve：扩散模型+强化学习生成改进的LL-37变体
- 所有内容已更新为英文
- GitHub链接指向：https://github.com/unumbrela/igem-jiangnan-china

### 联系信息
- 邮箱：zihao3351@gmail.com
- 电话：510-85327307
- 地址：江苏省无锡市蠡湖大道1800号（江南大学）

### 代码规范
- 保持中文注释清晰
- HTML缩进使用4个空格
- JavaScript使用驼峰命名法
- 所有链接的href值需要有效（当前部分链接为占位符"#"）

### 未来优化建议
1. **CSS重构**：将内联样式提取到外部CSS文件，便于维护
2. **JavaScript模块化**：将重复的JS代码提取到单独的js文件
3. **图片优化**：添加实际的图片资源（当前hero-bg.jpg为空文件）
4. **内容完善**：补充integration.html页面（当前在导航中但未创建）
5. **国际化**：考虑添加英文版本以适应iGEM国际赛事要求
6. **性能优化**：考虑使用本地库文件替代CDN，提高中国大陆访问速度
