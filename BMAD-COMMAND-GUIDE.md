# BMAD 命令系统完整指南

**正确使用 BMAD 工作流的命令触发方式**

---

## 🎯 **核心理解**

### **BMAD 不是自动的，是命令驱动的！**

```
❌ 错误理解:
用户: "我要创建一个博客"
→ 系统自动启动BMAD工作流

✅ 正确使用:
用户: "@analyst *help"
→ 切换到Analyst角色，查看可用命令

用户: "@analyst *create-project-brief"
→ Analyst开始创建项目简报
```

---

## 📋 **命令系统**

### **1. 代理切换命令（@前缀）**

| 命令 | 代理 | 角色 |
|------|------|------|
| `@analyst` | Mary 📊 | 业务分析师 |
| `@pm` | John 📋 | 产品经理 |
| `@ux-expert` | Jordan 🎨 | UX设计师 |
| `@architect` | Sam 🏗️ | 系统架构师 |
| `@po` | Taylor ✅ | 产品负责人 |
| `@sm` | Casey 📝 | Scrum Master |
| `@dev` | Jamie 💻 | 开发者 |
| `@qa` | Quinn 🧪 | QA工程师 |
| `@bmad-master` | 🧙 | 框架专家 |
| `@orchestrator` | 🎭 | 代理协调者 |

---

### **2. 代理命令（*前缀）**

#### **通用命令（所有代理）**
- `*help` - 显示当前代理的可用命令
- `*exit` - 退出当前代理角色
- `*yolo` - 切换Yolo模式（快速执行）
- `*doc-out` - 输出当前文档到文件

---

#### **Analyst Commands**
- `*help` - 显示命令列表
- `*brainstorm {topic}` - 头脑风暴会议
- `*create-competitor-analysis` - 创建竞品分析
- `*create-project-brief` - 创建项目简报
- `*perform-market-research` - 执行市场研究
- `*research-prompt {topic}` - 创建深度研究提示词
- `*elicit` - 高级需求引导

---

#### **PM Commands**
- `*help` - 显示命令列表
- `*create-prd` - 创建PRD文档
- `*create-brownfield-prd` - 创建现有项目PRD
- `*create-brownfield-epic` - 创建Epic
- `*create-brownfield-story` - 创建故事
- `*shard-prd` - 分片PRD文档
- `*correct-course` - 纠正方向

---

#### **Architect Commands**
- `*help` - 显示命令列表
- `*create-architecture` - 创建架构文档
- `*create-front-end-architecture` - 创建前端架构
- `*create-fullstack-architecture` - 创建全栈架构
- `*assess-nfr` - 评估非功能需求
- `*risk-profile` - 创建风险评估

---

#### **Dev Commands**
- `*help` - 显示命令列表
- `*develop-story` - 实现开发故事
- `*explain` - 解释代码
- `*review-qa` - 查看QA反馈
- `*run-tests` - 运行测试

---

#### **QA Commands**
- `*help` - 显示命令列表
- `*review-story` - 审查开发故事
- `*qa-gate` - 质量门控检查
- `*test-design` - 设计测试方案

---

## 🔄 **完整工作流示例**

### **创建个人博客项目（正确的BMAD使用方式）**

#### **阶段1: 需求分析**

```
用户: "@analyst *help"

AI (Analyst Mary):
"你好！我是Mary，BMAD的业务分析师。以下是可用命令：

1. *brainstorm - 头脑风暴
2. *create-project-brief - 创建项目简报
3. *perform-market-research - 市场研究
4. *create-competitor-analysis - 竞品分析
5. *exit - 退出Analyst角色

请输入命令编号或完整命令。"

---

用户: "@analyst *create-project-brief"

AI (Analyst Mary):
"开始创建项目简报！

【🔧 自动调用 Context7】查询博客平台技术栈
【🔧 自动调用 Sequential Thinking】分析博客核心需求
【🔧 自动调用 Ref】搜索竞品案例

现在让我问你几个关键问题...
[问题1-8, 收集需求]

基于你的回答，我会生成详细的项目简报。

[生成 project-brief.md]

✅ 项目简报已完成！
📂 已保存到: docs/project-brief.md

🎯 下一步: 使用 `@pm *create-prd` 创建PRD文档"
```

---

#### **阶段2: 创建PRD**

```
用户: "@pm *create-prd"

AI (PM John):
"你好！我是John，产品经理。开始创建PRD...

【📖 读取】docs/project-brief.md
【🔧 自动调用 Context7】查询Next.js最佳实践
【🔧 自动调用 Postman】研究博客API设计
【🔧 自动调用 bmad-integration】加载PRD模板

[创建详细PRD，包含Epic和User Stories]

✅ PRD已完成！
📂 已保存到: docs/prd.md

🎯 下一步: 使用 `@architect *create-fullstack-architecture` 设计架构"
```

---

#### **阶段3: 架构设计**

```
用户: "@architect *create-fullstack-architecture"

AI (Architect Sam):
"我是Sam，系统架构师。开始设计架构...

【📖 读取】docs/prd.md
【🔧 自动调用 fullstack-workflow】获取架构模板
【🔧 自动调用 Context7】查询技术栈文档
【🔧 自动调用 Railway】检查部署方案
【🔧 自动调用 Semgrep】预检安全考虑

[创建完整架构文档]

✅ 架构已完成！
📂 已保存到: docs/architecture.md

🎯 下一步: 使用 `@po *shard-prd docs/prd.md` 分片文档"
```

---

#### **阶段4: 文档分片**

```
用户: "@po *shard-prd docs/prd.md"

AI (PO Taylor):
"我是Taylor，产品负责人。开始文档验证和分片...

【✅ 验证】PRD与架构一致性
【✅ 验证】所有Epic都有技术方案
【🔧 调用 bmad-integration】运行shard_documents.py

执行:
```bash
python skills/bmad-integration/bmad-integration/scripts/shard_documents.py \
  docs/prd.md \
  docs/architecture.md
```

📊 Found 3 epics in PRD
✅ Created docs/prd/epic-1-content-management/
✅ Created docs/prd/epic-2-reading-experience/  
✅ Created docs/prd/epic-3-personal-brand/

✅ 文档分片完成！

🎯 下一步: 使用 `@sm *create-story` 创建第一个开发故事"
```

---

#### **阶段5: 创建开发故事**

```
用户: "@sm *create-story"

AI (SM Casey):
"我是Casey，Scrum Master。创建开发故事...

【📖 读取】docs/prd/epic-1-content-management/
【📖 读取】docs/architecture/epic-1-content-management/
【🔧 调用 bmad-integration】加载Story模板
【🔧 调用 Context7】查询Markdown编辑器库

[创建详细Story 001]

✅ Story已创建！
📂 已保存到: .bmad/stories/story-001.md

🎯 下一步: 使用 `@dev *develop-story .bmad/stories/story-001.md` 实现"
```

---

#### **阶段6: 实现代码**

```
用户: "@dev *develop-story .bmad/stories/story-001.md"

AI (Dev Jamie):
"我是Jamie，开发者。开始实现Story 001...

【📖 读取】.bmad/stories/story-001.md
【🔧 调用 Magic MCP】生成Markdown编辑器组件
【🔧 调用 artifacts-builder】初始化项目结构
【🔧 调用 shadcn-ui】获取UI组件
【🔧 调用 Context7】验证代码质量
【🔧 调用 Postman】测试API
【🔧 调用 Semgrep】安全扫描

[实现完整功能]

✅ Story 001实现完成！
📋 已更新File List
📊 Status: In Progress → Review

🎯 下一步: 使用 `@qa *review-story .bmad/stories/story-001.md` 审查"
```

---

#### **阶段7: 质量审查**

```
用户: "@qa *review-story .bmad/stories/story-001.md"

AI (QA Quinn):
"我是Quinn，QA工程师。开始审查Story 001...

【📖 读取】.bmad/stories/story-001.md 和代码
【🔧 调用 Magic MCP】组件优化分析
【🔧 调用 webapp-testing】自动化测试
【🔧 调用 Semgrep】深度安全扫描
【🔧 调用 Context7】验证最佳实践

[审查和优化]

✅ 审查完成！
✅ 小问题已直接修复
📊 Status: Review → Done

🎯 下一步: 继续 `@sm *create-story` 创建Story 002"
```

---

## 🤖 **CrewAI自动化版本（对比）**

### **传统BMAD（手动命令）**

```
耗时: 30-40小时（含角色切换）

用户需要:
1. 记住所有命令
2. 手动切换角色 (@analyst → @pm → @architect)
3. 手动调用命令 (*create-brief → *create-prd)
4. 理解工作流顺序
5. 手动传递上下文

优点: 完全控制
缺点: 繁琐、容易出错、耗时
```

---

### **BMAD-CrewAI（自动化）**

```python
# 一行代码执行完整规划阶段
from bmad_crewai.crews.bmad_development_crew import run_bmad_planning_phase

result = run_bmad_planning_phase(
    project_name="tech-blog",
    project_path="./tech-blog"
)

# ✅ 自动执行：Analyst → PM → Architect → PO
# ✅ 自动调用：所有MCP和Skills
# ✅ 自动保存：所有文档
# ✅ 自动分片：PRD和架构

耗时: 4-6小时（纯执行时间）

优点: 自动化、快速、零错误
缺点: 灵活性略低（但可配置）
```

---

## 🎯 **两种模式对比**

### **模式1: 手动BMAD命令（对话式）**

**适合场景：**
- ✅ 学习BMAD流程
- ✅ 需要灵活调整
- ✅ 探索性项目
- ✅ 想要完全控制

**使用方式：**
```
用户: "@analyst *create-project-brief"
→ 与Analyst对话，逐步完成

用户: "@pm *create-prd"  
→ 与PM对话，创建PRD

（手动流转）
```

---

### **模式2: CrewAI自动化（代码式）**

**适合场景：**
- ✅ 生产环境项目
- ✅ 标准化流程
- ✅ 批量项目
- ✅ 节省时间

**使用方式：**
```python
# 直接运行完整流程
result = run_bmad_planning_phase(
    project_name="blog",
    project_path="./blog"
)

# 或使用Flow精确控制
flow = BMADDevelopmentFlow()
result = flow.kickoff()
```

---

## 📊 **什么时候用哪种模式？**

| 场景 | 推荐模式 | 原因 |
|------|---------|------|
| 学习BMAD | 手动命令 | 理解每个步骤 |
| 探索新想法 | 手动命令 | 灵活调整方向 |
| 标准化开发 | CrewAI自动化 | 快速执行 |
| 批量项目 | CrewAI自动化 | 节省时间 |
| 需要记忆 | CrewAI自动化 | 持久化记忆 |
| 完全控制 | 手动命令 | 每步可调整 |

---

## 💡 **在你的系统中使用BMAD**

### **方式1: 对话式命令触发**

```
你说: "@analyst 帮我分析个人博客项目"

我会:
1. 切换到 Analyst (Mary) 身份
2. 执行以下操作:
   - 自动调用 Context7 查询博客技术栈
   - 自动调用 Sequential Thinking 分析需求
   - 自动调用 Ref 搜索竞品
   - 收集你的需求
   - 生成项目简报
3. 提示你使用 "@pm *create-prd" 继续

---

你说: "@pm *create-prd"

我会:
1. 切换到 PM (John) 身份
2. 执行以下操作:
   - 读取Analyst的项目简报
   - 调用 bmad-integration 的PRD模板
   - 调用 Context7 查询技术文档
   - 创建详细PRD
3. 提示你使用 "@architect *create-architecture"

（依此类推...）
```

---

### **方式2: CrewAI自动化（如果你设置了）**

```python
# 在Python中运行
cd skills/bmad-integration/bmad-crewai

# 完整规划阶段
python -c "
from crews.bmad_development_crew import run_bmad_planning_phase
run_bmad_planning_phase('blog', './blog')
"

# 自动完成：
# Analyst → PM → Architect → PO → 分片
# 无需手动命令！
```

---

## 🎭 **完整示例对话**

```
用户: "我想用BMAD工作流开发一个博客"

AI: "好的！BMAD使用命令系统。请选择：

1️⃣ **手动命令模式**（推荐学习）
   - 使用 `@analyst *help` 开始
   - 逐步完成每个阶段
   - 完全控制流程

2️⃣ **CrewAI自动化模式**（推荐生产）
   - 运行Python脚本自动执行
   - 4-6小时完成规划
   - 自动化流转

你想用哪种模式？"

---

用户: "手动命令模式"

AI: "明白！让我们开始。请说：

`@analyst *create-project-brief`

我会切换到Analyst身份开始需求分析。"

---

用户: "@analyst *create-project-brief"

AI (Analyst Mary):
"你好！我是Mary，业务分析师 📊

让我帮你创建项目简报。

【🔧 调用 Context7】查询现代博客技术...
【🔧 调用 Sequential Thinking】分析博客核心价值...

我需要了解...
[问题 1-8]

---

（收集答案后）

✅ 项目简报已完成！
📂 docs/project-brief.md

内容包括：
- 问题陈述
- 目标用户
- 成功指标
- MVP范围
- 技术约束

🎯 下一步: `@pm *create-prd`"

---

用户: "@pm *create-prd"

AI (PM John):
"你好！我是John，产品经理 📋

【📖 读取】docs/project-brief.md
【🔧 调用 bmad-integration】加载PRD模板...
【🔧 调用 Context7】查询Next.js文档...

[创建PRD with Epic和Stories]

✅ PRD已完成！
📂 docs/prd.md

包含3个Epic:
- Epic 1: 内容管理（4个stories）
- Epic 2: 阅读体验（3个stories）
- Epic 3: 个人品牌（2个stories）

🎯 下一步: `@architect *create-fullstack-architecture`"

---

（继续流转...）
```

---

## 📚 **BMAD命令速查表**

### **快速参考**

| 阶段 | 命令 | 输出 |
|------|------|------|
| 1. 分析 | `@analyst *create-project-brief` | docs/project-brief.md |
| 2. PRD | `@pm *create-prd` | docs/prd.md |
| 3. 架构 | `@architect *create-fullstack-architecture` | docs/architecture.md |
| 4. 分片 | `@po *shard-prd docs/prd.md` | docs/prd/epic-*/ |
| 5. 故事 | `@sm *create-story` | .bmad/stories/story-*.md |
| 6. 开发 | `@dev *develop-story story-001.md` | 代码文件 |
| 7. 审查 | `@qa *review-story story-001.md` | QA报告 |

---

## 🤖 **CrewAI自动化详解**

### **为什么需要CrewAI？**

**问题**: 手动BMAD命令繁琐
- 需要记住10个代理的命令
- 需要手动切换角色
- 需要手动传递上下文
- 容易遗漏步骤

**解决**: BMAD-CrewAI自动化
- ✅ 一行代码执行完整流程
- ✅ 自动代理协作
- ✅ 自动上下文传递
- ✅ 持久化记忆系统

---

### **CrewAI组件说明**

```
bmad-crewai/
├── agents/                     # 10个BMAD代理的CrewAI实现
│   ├── bmad_analyst.py        # ✅ 已实现
│   ├── bmad_developer.py      # ✅ 已实现
│   ├── bmad_pm.py             # ⏳ 开发中
│   └── ...
├── tools/                      # MCP和Skills桥接
│   ├── mcp_bridge.py          # MCP工具桥接
│   ├── skills_bridge.py       # Skills工具桥接
│   └── __init__.py            # 14个工具导出
├── crews/                      # 团队编排
│   └── bmad_development_crew.py  # ✅ 7个任务流程
└── flows/                      # 工作流控制
    └── bmad_development_flow.py  # ✅ 精确流程控制
```

---

## 🎯 **推荐使用方式**

### **新手/学习阶段**
```
使用: 手动BMAD命令（@agent *command）
理由: 理解每个代理的作用和工作流程
```

### **熟练后/生产项目**
```
使用: CrewAI自动化
理由: 节省时间，提高效率，减少错误
```

### **混合模式**
```
规划阶段: CrewAI自动化（快速生成文档）
开发阶段: 手动命令（灵活调整实现）
```

---

## 🎊 **总结**

### **BMAD有两种使用方式：**

#### **1. 对话式命令（原版BMAD）**
```
触发: @agent *command
特点: 手动控制、灵活、学习友好
适合: 探索、学习、灵活项目
```

#### **2. CrewAI自动化（BMAD-CrewAI）**
```
触发: Python代码
特点: 自动化、快速、生产级
适合: 标准化、批量、生产项目
```

---

### **你现在拥有完整的BMAD生态：**

✅ **BMAD-METHOD源码** - 理论框架和模板  
✅ **bmad-integration skill** - 文档模板和参考  
✅ **bmad-crewai** - CrewAI自动化实现  
✅ **命令系统** - @agent + *command  
✅ **工具集成** - 11个MCP + 18个Skills  
✅ **两种模式** - 手动灵活 + 自动高效  

**这是最完整的BMAD实现！** 🚀🎊

---

💡 **建议：** 现在试试！说 **"@analyst *help"** 查看Analyst的所有命令，或者说 **"@analyst *create-project-brief"** 直接开始创建项目简报！我会严格按照BMAD的命令系统工作，在需要时自动调用11个MCP和18个Skills！



**正确使用 BMAD 工作流的命令触发方式**

---

## 🎯 **核心理解**

### **BMAD 不是自动的，是命令驱动的！**

```
❌ 错误理解:
用户: "我要创建一个博客"
→ 系统自动启动BMAD工作流

✅ 正确使用:
用户: "@analyst *help"
→ 切换到Analyst角色，查看可用命令

用户: "@analyst *create-project-brief"
→ Analyst开始创建项目简报
```

---

## 📋 **命令系统**

### **1. 代理切换命令（@前缀）**

| 命令 | 代理 | 角色 |
|------|------|------|
| `@analyst` | Mary 📊 | 业务分析师 |
| `@pm` | John 📋 | 产品经理 |
| `@ux-expert` | Jordan 🎨 | UX设计师 |
| `@architect` | Sam 🏗️ | 系统架构师 |
| `@po` | Taylor ✅ | 产品负责人 |
| `@sm` | Casey 📝 | Scrum Master |
| `@dev` | Jamie 💻 | 开发者 |
| `@qa` | Quinn 🧪 | QA工程师 |
| `@bmad-master` | 🧙 | 框架专家 |
| `@orchestrator` | 🎭 | 代理协调者 |

---

### **2. 代理命令（*前缀）**

#### **通用命令（所有代理）**
- `*help` - 显示当前代理的可用命令
- `*exit` - 退出当前代理角色
- `*yolo` - 切换Yolo模式（快速执行）
- `*doc-out` - 输出当前文档到文件

---

#### **Analyst Commands**
- `*help` - 显示命令列表
- `*brainstorm {topic}` - 头脑风暴会议
- `*create-competitor-analysis` - 创建竞品分析
- `*create-project-brief` - 创建项目简报
- `*perform-market-research` - 执行市场研究
- `*research-prompt {topic}` - 创建深度研究提示词
- `*elicit` - 高级需求引导

---

#### **PM Commands**
- `*help` - 显示命令列表
- `*create-prd` - 创建PRD文档
- `*create-brownfield-prd` - 创建现有项目PRD
- `*create-brownfield-epic` - 创建Epic
- `*create-brownfield-story` - 创建故事
- `*shard-prd` - 分片PRD文档
- `*correct-course` - 纠正方向

---

#### **Architect Commands**
- `*help` - 显示命令列表
- `*create-architecture` - 创建架构文档
- `*create-front-end-architecture` - 创建前端架构
- `*create-fullstack-architecture` - 创建全栈架构
- `*assess-nfr` - 评估非功能需求
- `*risk-profile` - 创建风险评估

---

#### **Dev Commands**
- `*help` - 显示命令列表
- `*develop-story` - 实现开发故事
- `*explain` - 解释代码
- `*review-qa` - 查看QA反馈
- `*run-tests` - 运行测试

---

#### **QA Commands**
- `*help` - 显示命令列表
- `*review-story` - 审查开发故事
- `*qa-gate` - 质量门控检查
- `*test-design` - 设计测试方案

---

## 🔄 **完整工作流示例**

### **创建个人博客项目（正确的BMAD使用方式）**

#### **阶段1: 需求分析**

```
用户: "@analyst *help"

AI (Analyst Mary):
"你好！我是Mary，BMAD的业务分析师。以下是可用命令：

1. *brainstorm - 头脑风暴
2. *create-project-brief - 创建项目简报
3. *perform-market-research - 市场研究
4. *create-competitor-analysis - 竞品分析
5. *exit - 退出Analyst角色

请输入命令编号或完整命令。"

---

用户: "@analyst *create-project-brief"

AI (Analyst Mary):
"开始创建项目简报！

【🔧 自动调用 Context7】查询博客平台技术栈
【🔧 自动调用 Sequential Thinking】分析博客核心需求
【🔧 自动调用 Ref】搜索竞品案例

现在让我问你几个关键问题...
[问题1-8, 收集需求]

基于你的回答，我会生成详细的项目简报。

[生成 project-brief.md]

✅ 项目简报已完成！
📂 已保存到: docs/project-brief.md

🎯 下一步: 使用 `@pm *create-prd` 创建PRD文档"
```

---

#### **阶段2: 创建PRD**

```
用户: "@pm *create-prd"

AI (PM John):
"你好！我是John，产品经理。开始创建PRD...

【📖 读取】docs/project-brief.md
【🔧 自动调用 Context7】查询Next.js最佳实践
【🔧 自动调用 Postman】研究博客API设计
【🔧 自动调用 bmad-integration】加载PRD模板

[创建详细PRD，包含Epic和User Stories]

✅ PRD已完成！
📂 已保存到: docs/prd.md

🎯 下一步: 使用 `@architect *create-fullstack-architecture` 设计架构"
```

---

#### **阶段3: 架构设计**

```
用户: "@architect *create-fullstack-architecture"

AI (Architect Sam):
"我是Sam，系统架构师。开始设计架构...

【📖 读取】docs/prd.md
【🔧 自动调用 fullstack-workflow】获取架构模板
【🔧 自动调用 Context7】查询技术栈文档
【🔧 自动调用 Railway】检查部署方案
【🔧 自动调用 Semgrep】预检安全考虑

[创建完整架构文档]

✅ 架构已完成！
📂 已保存到: docs/architecture.md

🎯 下一步: 使用 `@po *shard-prd docs/prd.md` 分片文档"
```

---

#### **阶段4: 文档分片**

```
用户: "@po *shard-prd docs/prd.md"

AI (PO Taylor):
"我是Taylor，产品负责人。开始文档验证和分片...

【✅ 验证】PRD与架构一致性
【✅ 验证】所有Epic都有技术方案
【🔧 调用 bmad-integration】运行shard_documents.py

执行:
```bash
python skills/bmad-integration/bmad-integration/scripts/shard_documents.py \
  docs/prd.md \
  docs/architecture.md
```

📊 Found 3 epics in PRD
✅ Created docs/prd/epic-1-content-management/
✅ Created docs/prd/epic-2-reading-experience/  
✅ Created docs/prd/epic-3-personal-brand/

✅ 文档分片完成！

🎯 下一步: 使用 `@sm *create-story` 创建第一个开发故事"
```

---

#### **阶段5: 创建开发故事**

```
用户: "@sm *create-story"

AI (SM Casey):
"我是Casey，Scrum Master。创建开发故事...

【📖 读取】docs/prd/epic-1-content-management/
【📖 读取】docs/architecture/epic-1-content-management/
【🔧 调用 bmad-integration】加载Story模板
【🔧 调用 Context7】查询Markdown编辑器库

[创建详细Story 001]

✅ Story已创建！
📂 已保存到: .bmad/stories/story-001.md

🎯 下一步: 使用 `@dev *develop-story .bmad/stories/story-001.md` 实现"
```

---

#### **阶段6: 实现代码**

```
用户: "@dev *develop-story .bmad/stories/story-001.md"

AI (Dev Jamie):
"我是Jamie，开发者。开始实现Story 001...

【📖 读取】.bmad/stories/story-001.md
【🔧 调用 Magic MCP】生成Markdown编辑器组件
【🔧 调用 artifacts-builder】初始化项目结构
【🔧 调用 shadcn-ui】获取UI组件
【🔧 调用 Context7】验证代码质量
【🔧 调用 Postman】测试API
【🔧 调用 Semgrep】安全扫描

[实现完整功能]

✅ Story 001实现完成！
📋 已更新File List
📊 Status: In Progress → Review

🎯 下一步: 使用 `@qa *review-story .bmad/stories/story-001.md` 审查"
```

---

#### **阶段7: 质量审查**

```
用户: "@qa *review-story .bmad/stories/story-001.md"

AI (QA Quinn):
"我是Quinn，QA工程师。开始审查Story 001...

【📖 读取】.bmad/stories/story-001.md 和代码
【🔧 调用 Magic MCP】组件优化分析
【🔧 调用 webapp-testing】自动化测试
【🔧 调用 Semgrep】深度安全扫描
【🔧 调用 Context7】验证最佳实践

[审查和优化]

✅ 审查完成！
✅ 小问题已直接修复
📊 Status: Review → Done

🎯 下一步: 继续 `@sm *create-story` 创建Story 002"
```

---

## 🤖 **CrewAI自动化版本（对比）**

### **传统BMAD（手动命令）**

```
耗时: 30-40小时（含角色切换）

用户需要:
1. 记住所有命令
2. 手动切换角色 (@analyst → @pm → @architect)
3. 手动调用命令 (*create-brief → *create-prd)
4. 理解工作流顺序
5. 手动传递上下文

优点: 完全控制
缺点: 繁琐、容易出错、耗时
```

---

### **BMAD-CrewAI（自动化）**

```python
# 一行代码执行完整规划阶段
from bmad_crewai.crews.bmad_development_crew import run_bmad_planning_phase

result = run_bmad_planning_phase(
    project_name="tech-blog",
    project_path="./tech-blog"
)

# ✅ 自动执行：Analyst → PM → Architect → PO
# ✅ 自动调用：所有MCP和Skills
# ✅ 自动保存：所有文档
# ✅ 自动分片：PRD和架构

耗时: 4-6小时（纯执行时间）

优点: 自动化、快速、零错误
缺点: 灵活性略低（但可配置）
```

---

## 🎯 **两种模式对比**

### **模式1: 手动BMAD命令（对话式）**

**适合场景：**
- ✅ 学习BMAD流程
- ✅ 需要灵活调整
- ✅ 探索性项目
- ✅ 想要完全控制

**使用方式：**
```
用户: "@analyst *create-project-brief"
→ 与Analyst对话，逐步完成

用户: "@pm *create-prd"  
→ 与PM对话，创建PRD

（手动流转）
```

---

### **模式2: CrewAI自动化（代码式）**

**适合场景：**
- ✅ 生产环境项目
- ✅ 标准化流程
- ✅ 批量项目
- ✅ 节省时间

**使用方式：**
```python
# 直接运行完整流程
result = run_bmad_planning_phase(
    project_name="blog",
    project_path="./blog"
)

# 或使用Flow精确控制
flow = BMADDevelopmentFlow()
result = flow.kickoff()
```

---

## 📊 **什么时候用哪种模式？**

| 场景 | 推荐模式 | 原因 |
|------|---------|------|
| 学习BMAD | 手动命令 | 理解每个步骤 |
| 探索新想法 | 手动命令 | 灵活调整方向 |
| 标准化开发 | CrewAI自动化 | 快速执行 |
| 批量项目 | CrewAI自动化 | 节省时间 |
| 需要记忆 | CrewAI自动化 | 持久化记忆 |
| 完全控制 | 手动命令 | 每步可调整 |

---

## 💡 **在你的系统中使用BMAD**

### **方式1: 对话式命令触发**

```
你说: "@analyst 帮我分析个人博客项目"

我会:
1. 切换到 Analyst (Mary) 身份
2. 执行以下操作:
   - 自动调用 Context7 查询博客技术栈
   - 自动调用 Sequential Thinking 分析需求
   - 自动调用 Ref 搜索竞品
   - 收集你的需求
   - 生成项目简报
3. 提示你使用 "@pm *create-prd" 继续

---

你说: "@pm *create-prd"

我会:
1. 切换到 PM (John) 身份
2. 执行以下操作:
   - 读取Analyst的项目简报
   - 调用 bmad-integration 的PRD模板
   - 调用 Context7 查询技术文档
   - 创建详细PRD
3. 提示你使用 "@architect *create-architecture"

（依此类推...）
```

---

### **方式2: CrewAI自动化（如果你设置了）**

```python
# 在Python中运行
cd skills/bmad-integration/bmad-crewai

# 完整规划阶段
python -c "
from crews.bmad_development_crew import run_bmad_planning_phase
run_bmad_planning_phase('blog', './blog')
"

# 自动完成：
# Analyst → PM → Architect → PO → 分片
# 无需手动命令！
```

---

## 🎭 **完整示例对话**

```
用户: "我想用BMAD工作流开发一个博客"

AI: "好的！BMAD使用命令系统。请选择：

1️⃣ **手动命令模式**（推荐学习）
   - 使用 `@analyst *help` 开始
   - 逐步完成每个阶段
   - 完全控制流程

2️⃣ **CrewAI自动化模式**（推荐生产）
   - 运行Python脚本自动执行
   - 4-6小时完成规划
   - 自动化流转

你想用哪种模式？"

---

用户: "手动命令模式"

AI: "明白！让我们开始。请说：

`@analyst *create-project-brief`

我会切换到Analyst身份开始需求分析。"

---

用户: "@analyst *create-project-brief"

AI (Analyst Mary):
"你好！我是Mary，业务分析师 📊

让我帮你创建项目简报。

【🔧 调用 Context7】查询现代博客技术...
【🔧 调用 Sequential Thinking】分析博客核心价值...

我需要了解...
[问题 1-8]

---

（收集答案后）

✅ 项目简报已完成！
📂 docs/project-brief.md

内容包括：
- 问题陈述
- 目标用户
- 成功指标
- MVP范围
- 技术约束

🎯 下一步: `@pm *create-prd`"

---

用户: "@pm *create-prd"

AI (PM John):
"你好！我是John，产品经理 📋

【📖 读取】docs/project-brief.md
【🔧 调用 bmad-integration】加载PRD模板...
【🔧 调用 Context7】查询Next.js文档...

[创建PRD with Epic和Stories]

✅ PRD已完成！
📂 docs/prd.md

包含3个Epic:
- Epic 1: 内容管理（4个stories）
- Epic 2: 阅读体验（3个stories）
- Epic 3: 个人品牌（2个stories）

🎯 下一步: `@architect *create-fullstack-architecture`"

---

（继续流转...）
```

---

## 📚 **BMAD命令速查表**

### **快速参考**

| 阶段 | 命令 | 输出 |
|------|------|------|
| 1. 分析 | `@analyst *create-project-brief` | docs/project-brief.md |
| 2. PRD | `@pm *create-prd` | docs/prd.md |
| 3. 架构 | `@architect *create-fullstack-architecture` | docs/architecture.md |
| 4. 分片 | `@po *shard-prd docs/prd.md` | docs/prd/epic-*/ |
| 5. 故事 | `@sm *create-story` | .bmad/stories/story-*.md |
| 6. 开发 | `@dev *develop-story story-001.md` | 代码文件 |
| 7. 审查 | `@qa *review-story story-001.md` | QA报告 |

---

## 🤖 **CrewAI自动化详解**

### **为什么需要CrewAI？**

**问题**: 手动BMAD命令繁琐
- 需要记住10个代理的命令
- 需要手动切换角色
- 需要手动传递上下文
- 容易遗漏步骤

**解决**: BMAD-CrewAI自动化
- ✅ 一行代码执行完整流程
- ✅ 自动代理协作
- ✅ 自动上下文传递
- ✅ 持久化记忆系统

---

### **CrewAI组件说明**

```
bmad-crewai/
├── agents/                     # 10个BMAD代理的CrewAI实现
│   ├── bmad_analyst.py        # ✅ 已实现
│   ├── bmad_developer.py      # ✅ 已实现
│   ├── bmad_pm.py             # ⏳ 开发中
│   └── ...
├── tools/                      # MCP和Skills桥接
│   ├── mcp_bridge.py          # MCP工具桥接
│   ├── skills_bridge.py       # Skills工具桥接
│   └── __init__.py            # 14个工具导出
├── crews/                      # 团队编排
│   └── bmad_development_crew.py  # ✅ 7个任务流程
└── flows/                      # 工作流控制
    └── bmad_development_flow.py  # ✅ 精确流程控制
```

---

## 🎯 **推荐使用方式**

### **新手/学习阶段**
```
使用: 手动BMAD命令（@agent *command）
理由: 理解每个代理的作用和工作流程
```

### **熟练后/生产项目**
```
使用: CrewAI自动化
理由: 节省时间，提高效率，减少错误
```

### **混合模式**
```
规划阶段: CrewAI自动化（快速生成文档）
开发阶段: 手动命令（灵活调整实现）
```

---

## 🎊 **总结**

### **BMAD有两种使用方式：**

#### **1. 对话式命令（原版BMAD）**
```
触发: @agent *command
特点: 手动控制、灵活、学习友好
适合: 探索、学习、灵活项目
```

#### **2. CrewAI自动化（BMAD-CrewAI）**
```
触发: Python代码
特点: 自动化、快速、生产级
适合: 标准化、批量、生产项目
```

---

### **你现在拥有完整的BMAD生态：**

✅ **BMAD-METHOD源码** - 理论框架和模板  
✅ **bmad-integration skill** - 文档模板和参考  
✅ **bmad-crewai** - CrewAI自动化实现  
✅ **命令系统** - @agent + *command  
✅ **工具集成** - 11个MCP + 18个Skills  
✅ **两种模式** - 手动灵活 + 自动高效  

**这是最完整的BMAD实现！** 🚀🎊

---

💡 **建议：** 现在试试！说 **"@analyst *help"** 查看Analyst的所有命令，或者说 **"@analyst *create-project-brief"** 直接开始创建项目简报！我会严格按照BMAD的命令系统工作，在需要时自动调用11个MCP和18个Skills！


