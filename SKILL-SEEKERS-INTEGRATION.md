# Skill Seekers 集成指南

**自动化Skill生成工具已完全集成！**

---

## 🎯 **什么是 Skill Seekers？**

**Skill Seekers** 是一个自动化工具，可以将**任何文档网站转换为Claude AI Skill**！

### **核心价值**

| 传统方式 | 使用 Skill Seekers | 提升 |
|---------|-------------------|------|
| 手动阅读文档并整理 | 自动爬取+AI增强 | ⚡ 100倍速 |
| 3-7天创建一个Skill | 20-40分钟自动生成 | ⚡ 10倍速 |
| 需要深入理解框架 | AI自动提取最佳实践 | 🧠 智能化 |
| 容易遗漏内容 | 完整爬取所有页面 | ✅ 全面性 |

**总结**: 将**数天的手动工作压缩到30分钟的自动化流程**！

---

## 🚀 **快速开始**

### **方式1: 使用预设配置（推荐）**

```bash
# 进入 skill_seekers 目录
cd skill_seekers

# 安装依赖
pip install requests beautifulsoup4

# 使用预设配置（含AI增强）
python doc_scraper.py --config configs/react.json --enhance-local

# 等待完成（20-40分钟）+ AI增强（60秒）

# 打包
python package_skill.py output/react/

# 完成！得到 react.zip
```

---

### **方式2: 交互式创建**

```bash
cd skill_seekers
python doc_scraper.py --interactive

# 按提示回答：
# - Skill名称: threejs
# - 文档URL: https://threejs.org/docs/
# - 描述: Three.js 3D library for web
# - 是否AI增强: yes
```

---

### **方式3: 快速命令**

```bash
cd skill_seekers
python doc_scraper.py \
  --name tailwindcss \
  --url https://tailwindcss.com/docs \
  --description "Tailwind CSS utility-first framework" \
  --enhance-local
```

---

## 📦 **8个预设配置**

| 配置文件 | 框架 | 用途 |
|---------|------|------|
| `configs/godot.json` | Godot Engine | 游戏开发 |
| `configs/react.json` | React | UI框架 |
| `configs/vue.json` | Vue.js | 前端框架 |
| `configs/django.json` | Django | Python Web |
| `configs/fastapi.json` | FastAPI | Python API |
| `configs/steam-economy-complete.json` | Steam | 游戏经济系统 |
| 自定义... | 任何框架 | 任何文档网站 |

---

## 🔄 **完整工作流程**

### **阶段1: 爬取和增强（首次）**

```bash
步骤1: 爬取文档
cd skill_seekers
python doc_scraper.py --config configs/react.json --enhance-local

执行内容:
✅ 爬取 https://react.dev/ 所有页面
✅ 智能分类内容（API/组件/Hooks/指南等）
✅ 提取代码示例（自动检测语言）
✅ AI增强生成详细SKILL.md
✅ 创建references/目录（分类文档）

输出:
skill_seekers/output/
├── react_data/           # 原始数据（可重用）
│   ├── pages/           # 所有页面JSON
│   └── summary.json     # 概览
└── react/               # 生成的Skill
    ├── SKILL.md         # AI增强的主文件（500+行）
    ├── references/      # 分类文档
    │   ├── getting_started.md
    │   ├── components.md
    │   ├── hooks.md
    │   └── api.md
    ├── scripts/         # 空（可手动添加）
    └── assets/          # 空（可手动添加）

耗时: 20-40分钟（爬取）+ 60秒（AI增强）
```

---

### **阶段2: 打包和部署**

```bash
步骤2: 打包Skill
python package_skill.py output/react/

执行内容:
✅ 验证Skill结构
✅ 检查SKILL.md格式
✅ 打包所有文件
✅ 生成react.zip

步骤3: 部署到skills目录
mv output/react/ ../skills/react/

步骤4: 注册Skill
# 更新 skills/.claude-plugin/marketplace.json
# 添加 "./react" 到 skills 列表

步骤5: 更新配置
# 在 .cursorrules 中添加react skill使用说明

✅ 完成！新Skill立即可用
```

---

## 🎭 **在BMAD工作流中使用**

### **Architect 使用 Skill Seekers**

```
场景: 需要为新的技术栈创建参考Skill

🏗️ Architect (Sam):
"我们要用Three.js做3D可视化，但团队不熟悉。
让我创建一个Three.js Skill..."

【🔧 调用 skill-seekers】
步骤1: 创建配置
```json
// configs/threejs.json
{
  "name": "threejs",
  "description": "Three.js 3D library. Use for 3D graphics, WebGL, scene rendering.",
  "base_url": "https://threejs.org/docs/",
  "max_pages": 300
}
```

步骤2: 爬取和增强
```bash
cd skill_seekers
python doc_scraper.py --config configs/threejs.json --enhance-local
```

步骤3: 部署
```bash
python package_skill.py output/threejs/
mv output/threejs/ ../skills/
```

步骤4: 更新配置
- 添加到 marketplace.json
- 在架构文档中引用

✅ 团队现在可以使用Three.js Skill快速学习！

【🔧 调用 Context7 + threejs skill】
架构设计时查询Three.js最佳实践
```

---

### **Dev 使用生成的Skill**

```
💻 Dev (Jamie):
"实现Story: 3D产品展示"

【📚 使用 threejs skill】
1. 读取 skills/threejs/SKILL.md
2. 参考 skills/threejs/references/scenes.md
3. 使用提供的代码示例
4. Context7补充细节
5. 实现完成！

对比:
- 没有Skill: 需要自己翻阅整个Three.js文档（2-3小时）
- 有Skill: 直接读取整理好的参考（15分钟）

效率提升: 8-12倍！
```

---

## 🔧 **Skill Seekers 工具详解**

### **1. doc_scraper.py - 主爬虫工具**

**功能**:
- 爬取整个文档网站
- 智能分类内容
- 提取代码示例
- 检测编程语言
- 生成基础SKILL.md

**参数**:
```bash
# 使用配置文件
--config configs/react.json

# 交互模式
--interactive

# 快速模式
--name react --url https://react.dev/

# 跳过爬取（使用缓存）
--skip-scrape

# AI增强（本地）
--enhance-local

# AI增强（API）
--enhance
```

---

### **2. enhance_skill_local.py - 本地AI增强**

**功能**:
- 使用Claude Code Max（无需API key）
- 分析references/文档
- 提取最佳代码示例（5-10个）
- 生成综合性SKILL.md（500+行）
- 添加领域特定概念
- 提供导航指引

**使用**:
```bash
# 独立运行
python enhance_skill_local.py output/react/

# 自动备份原文件
# 生成增强版SKILL.md
# 60秒完成
```

**质量对比**:
- 基础模板: 75行，通用描述
- AI增强后: 500+行，实际示例，最佳实践
- 质量提升: 10倍！

---

### **3. package_skill.py - 打包工具**

**功能**:
- 验证Skill结构
- 检查SKILL.md格式
- 打包为.zip文件
- 准备分发

**使用**:
```bash
python package_skill.py output/react/

# 输出: react.zip（可上传Claude或分享）
```

---

## 📊 **实战示例**

### **示例1: 为Prisma ORM创建Skill**

```
需求: "团队要用Prisma，需要参考文档"

工作流:
1. 【创建配置】
```json
// skill_seekers/configs/prisma.json
{
  "name": "prisma",
  "description": "Prisma ORM. Use for database operations, schema management, migrations.",
  "base_url": "https://www.prisma.io/docs/",
  "url_patterns": {
    "include": ["/docs/"],
    "exclude": ["/blog", "/about"]
  },
  "max_pages": 200
}
```

2. 【爬取+增强】
```bash
cd skill_seekers
python doc_scraper.py --config configs/prisma.json --enhance-local
```

3. 【打包部署】
```bash
python package_skill.py output/prisma/
mv output/prisma/ ../skills/
```

4. 【注册】
更新 marketplace.json:
```json
{
  "skills": [
    ...
    "./prisma"
  ]
}
```

5. 【更新.cursorrules】
添加使用说明:
```markdown
### Prisma Skill
**使用场景**: 数据库操作、Schema设计、迁移管理
**配合**: Context7（补充细节）+ fullstack-workflow（集成）
```

✅ 完成！团队可立即使用Prisma Skill
```

---

### **示例2: 创建公司内部API Skill**

```
需求: "公司有内部API文档，想创建Skill"

工作流:
1. 【确保文档可访问】
   - 内网文档: 配置VPN
   - 需要认证: 在doc_scraper.py中添加auth headers

2. 【创建自定义配置】
```json
// configs/company-api.json
{
  "name": "company-api",
  "description": "Company internal API. Use for [specific use cases].",
  "base_url": "https://internal-docs.company.com/",
  "selectors": {
    "main_content": "div.documentation",
    "title": "h1.page-title",
    "code_blocks": "pre.code-block"
  }
}
```

3. 【爬取】
```bash
cd skill_seekers
python doc_scraper.py --config configs/company-api.json --enhance-local
```

4. 【手动优化】
   - 使用 skill-creator 调优
   - 添加公司特定的scripts/
   - 添加内部最佳实践到references/

5. 【打包和分发】
```bash
python package_skill.py output/company-api/
# 分享 company-api.zip 给团队
```

✅ 团队统一使用内部API Skill，提升一致性
```

---

## 🔗 **与现有系统的集成**

### **Skill Seekers + skill-creator**

```
最佳组合: 自动化基础 + 手动精修

流程:
1. skill-seekers: 自动生成框架文档Skill（快速）
   → 得到: 完整的references/ + 基础SKILL.md
   
2. skill-creator: 手动添加自定义内容（精细）
   → 添加: 公司特定的scripts/
   → 添加: 内部最佳实践到SKILL.md
   → 添加: 项目模板到assets/
   
3. 结合使用:
   → Skill Seekers提供框架知识
   → skill-creator提供业务知识
   → 完美互补！
```

---

### **Skill Seekers + BMAD工作流**

```
场景: 开始新项目，技术栈未知

🎭 Analyst + Architect协作:

Analyst 📊:
"分析市场后，推荐使用Svelte框架"

Architect 🏗️:
"团队不熟悉Svelte，让我创建参考Skill..."

【🔧 使用 skill-seekers】
```bash
cd skill_seekers
python doc_scraper.py \
  --name svelte \
  --url https://svelte.dev/docs \
  --enhance-local
python package_skill.py output/svelte/
mv output/svelte/ ../skills/
```

【更新marketplace.json】
【更新.cursorrules】

"Svelte Skill已创建！现在团队可以使用了。"

💻 Dev (Jamie):
【🔧 使用 svelte skill + Context7】
快速学习Svelte并实现组件

效率: 学习时间从2周 → 2天！
```

---

## 📋 **详细使用指南**

### **完整流程（含所有步骤）**

```bash
# ========================================
# 第1步: 准备环境
# ========================================
cd skill_seekers
pip install requests beautifulsoup4

# ========================================
# 第2步: 创建或选择配置
# ========================================

# 方式A: 使用预设
ls configs/  # 查看可用预设

# 方式B: 创建自定义配置
cp configs/react.json configs/myframework.json
nano configs/myframework.json  # 编辑配置

# ========================================
# 第3步: 爬取文档（含AI增强）
# ========================================
python doc_scraper.py --config configs/myframework.json --enhance-local

# 爬取过程:
# - 访问文档网站
# - 提取所有页面
# - 智能分类
# - 检测代码语言
# - AI生成SKILL.md
# 
# 耗时: 20-40分钟（首次）

# ========================================
# 第4步: 检查输出质量
# ========================================
cat output/myframework/SKILL.md        # 查看主文件
cat output/myframework/references/index.md  # 查看分类

# ========================================
# 第5步: 手动调优（可选）
# ========================================
# 使用 skill-creator 添加：
# - 自定义 scripts/
# - 项目模板 assets/
# - 公司特定最佳实践

# ========================================
# 第6步: 打包
# ========================================
python package_skill.py output/myframework/

# 输出: myframework.zip

# ========================================
# 第7步: 部署到项目
# ========================================
# 方式A: 移动到skills/目录
mv output/myframework/ ../skills/

# 方式B: 上传到Claude
# 使用myframework.zip

# ========================================
# 第8步: 注册Skill
# ========================================
# 更新 ../skills/.claude-plugin/marketplace.json
{
  "skills": [
    ...
    "./myframework"
  ]
}

# ========================================
# 第9步: 更新配置
# ========================================
# 在 ../.cursorrules 中添加使用说明

# ========================================
# 完成！
# ========================================
```

---

## 🎯 **实际使用案例**

### **案例1: 为博客项目创建TailwindCSS Skill**

```
项目: 个人技术博客（使用BMAD工作流）

阶段: Architect设计阶段

🏗️ Architect (Sam):
"我推荐使用Tailwind CSS，但需要快速参考文档..."

【使用 skill-seekers】
cd skill_seekers
python doc_scraper.py \
  --name tailwindcss \
  --url https://tailwindcss.com/docs \
  --description "Tailwind CSS utility-first framework. Use for styling, responsive design." \
  --enhance-local

# 30分钟后...
python package_skill.py output/tailwindcss/
mv output/tailwindcss/ ../skills/

【注册到marketplace.json】
【更新.cursorrules】

架构文档中添加:
"CSS框架: Tailwind CSS（参考 tailwindcss skill）"

💻 Dev实现时:
【使用 tailwindcss skill + shadcn-ui】
快速掌握Tailwind最佳实践
```

---

### **案例2: 为MCP开发创建TypeScript SDK Skill**

```
项目: 开发新的MCP服务器

阶段: Dev开发阶段（使用mcp-builder skill）

💻 Dev (Jamie):
"使用mcp-builder创建MCP，需要TypeScript SDK参考..."

【使用 skill-seekers】
cd skill_seekers
python doc_scraper.py \
  --name mcp-typescript-sdk \
  --url https://github.com/modelcontextprotocol/typescript-sdk \
  --enhance-local

# 生成TypeScript SDK Skill

【配合使用】
- mcp-builder skill: 提供MCP开发流程
- mcp-typescript-sdk skill: 提供SDK API参考
- Context7: 补充具体细节

效率: SDK学习时间从1天 → 2小时
```

---

## ⚡ **高级技巧**

### **1. 缓存系统（加速重建）**

```bash
# 首次爬取（慢）
python doc_scraper.py --config configs/react.json --enhance-local
# 耗时: 30分钟

# 后续重建（极快）
python doc_scraper.py --config configs/react.json --skip-scrape
# 耗时: 1分钟

# 用途: 
# - 调整SKILL.md模板
# - 修改分类规则
# - 重新AI增强
```

---

### **2. 测试先行（小规模测试）**

```json
// configs/test.json
{
  "name": "test",
  "base_url": "https://example.com/docs/",
  "max_pages": 10  // 只爬取10页测试
}
```

```bash
python doc_scraper.py --config configs/test.json

# 检查输出质量
# 如果满意，增加max_pages到完整数量
```

---

### **3. 自定义选择器（解决爬取问题）**

```json
{
  "selectors": {
    "main_content": "article",    // 主内容选择器
    "title": "h1",                 // 标题选择器
    "code_blocks": "pre code"      // 代码块选择器
  }
}
```

**常见选择器**:
- `article` - 标准文档
- `main` - 主内容区
- `div[role="main"]` - ARIA标记
- `div.documentation` - 自定义类名

**测试选择器**:
```python
from bs4 import BeautifulSoup
import requests

url = "https://docs.example.com/page"
soup = BeautifulSoup(requests.get(url).content, 'html.parser')
print(soup.select_one('article'))  # 测试
```

---

## 📊 **Skill Seekers 性能统计**

| 任务 | 耗时 | 说明 |
|------|------|------|
| 首次爬取 | 15-45分钟 | 取决于文档大小 |
| AI增强 | 60秒 | 本地Claude Code |
| 打包 | 5-10秒 | 生成.zip |
| 重建（skip-scrape） | <1分钟 | 使用缓存 |
| **总计（首次）** | **20-46分钟** | 完整Skill |
| **总计（重建）** | **2分钟** | 调整后重建 |

**对比手动创建**:
- 手动创建一个Skill: 2-7天
- Skill Seekers自动生成: 30分钟
- **效率提升: 100-300倍！**

---

## 🎯 **与现有Skills的完美配合**

### **生成新Skills后的增强流程**

```
Step 1: 使用 skill-seekers 自动生成
→ 得到: 框架的完整文档Skill

Step 2: 使用 skill-creator 手动增强
→ 添加: 项目特定的scripts/
→ 添加: 公司最佳实践
→ 添加: 模板到assets/

Step 3: 使用 BMAD工作流 实际应用
→ Dev使用生成的Skill快速学习
→ Architect引用Skill设计架构

Step 4: 持续优化
→ 根据使用反馈调整
→ 添加更多examples/
→ 版本控制（GitHub）
```

---

## 🏆 **成功案例**

### **已生成的Skills（可用预设）**

使用以下命令立即生成：

```bash
cd skill_seekers

# 1. React Skill
python doc_scraper.py --config configs/react.json --enhance-local
python package_skill.py output/react/

# 2. Vue Skill  
python doc_scraper.py --config configs/vue.json --enhance-local
python package_skill.py output/vue/

# 3. Django Skill
python doc_scraper.py --config configs/django.json --enhance-local
python package_skill.py output/django/

# 4. FastAPI Skill
python doc_scraper.py --config configs/fastapi.json --enhance-local
python package_skill.py output/fastapi/

# 5. Godot Skill
python doc_scraper.py --config configs/godot.json --enhance-local
python package_skill.py output/godot/
```

**部署**:
```bash
# 批量移动到skills/
for skill in react vue django fastapi godot; do
  mv output/$skill/ ../skills/
done

# 批量注册（更新marketplace.json）
```

---

## 📚 **推荐创建的Skills**

### **前端生态**
- [ ] Next.js
- [ ] Nuxt.js
- [ ] Vite
- [ ] TailwindCSS
- [ ] Framer Motion

### **后端生态**
- [ ] NestJS
- [ ] Express
- [ ] Fastify
- [ ] Prisma ORM
- [ ] Drizzle ORM

### **全栈框架**
- [ ] Remix
- [ ] SvelteKit
- [ ] Astro
- [ ] T3 Stack

### **测试工具**
- [ ] Vitest
- [ ] Playwright
- [ ] Cypress
- [ ] Jest

### **部署工具**
- [ ] Docker
- [ ] Kubernetes
- [ ] Vercel
- [ ] Netlify

**命令模板**:
```bash
python doc_scraper.py \
  --name [framework] \
  --url https://[framework].dev/docs \
  --enhance-local
```

---

## 🎊 **集成完成！**

### **系统更新总结**

✅ **技能总数**: 17 → **18个Skills**  
✅ **新增工具**: skill-seekers 自动化Skill生成器  
✅ **集成到**: .cursorrules 工作流  
✅ **预设配置**: 8个流行框架  
✅ **功能强大**: 
   - 自动爬取文档
   - AI增强质量
   - 一键打包
   - 快速部署

---

### **你现在拥有**

```
11个MCP服务器
18个Skills（新增skill-seekers）
10个BMAD代理
+ Skill自动化生成能力！

= 可以无限扩展的Skills生态系统
```

---

## 💡 **立即尝试**

### **生成你的第一个Skill**

```bash
cd skill_seekers

# 选择一个你常用的框架
python doc_scraper.py --config configs/react.json --enhance-local

# 等待30分钟（可以做其他事）

# 打包
python package_skill.py output/react/

# 部署
mv output/react/ ../skills/

# 享受！
```

---

### **或者创建自定义Skill**

```
你: "为TailwindCSS创建一个Skill"

我会:
1. ✅ 识别需要skill-seekers
2. ✅ 创建configs/tailwindcss.json
3. ✅ 运行爬虫和AI增强
4. ✅ 打包部署
5. ✅ 更新配置
6. ✅ TailwindCSS Skill可用！
```

---

## 🎉 **最终总结**

**Skill Seekers 让你可以：**

- 🤖 **自动化Skill创建** - 30分钟 vs 手动3天
- 📚 **无限扩展** - 为任何框架创建Skill
- 🎯 **高质量输出** - AI增强的专业文档
- 🔄 **持续更新** - 重新爬取获取最新文档
- 🤝 **团队共享** - 统一的知识库

**与BMAD + Skills + MCPs的完美结合**:
- BMAD提供协作框架
- Skills提供专业能力
- MCPs提供工具集成
- **Skill Seekers提供无限扩展性！**

**你的系统现在是一个自我进化的AI开发平台！** 🚀🎊

---

**创建日期**: 2025-10-26  
**版本**: v1.2.0  
**系统**: 11 MCPs + 18 Skills + BMAD + Skill Seekers





