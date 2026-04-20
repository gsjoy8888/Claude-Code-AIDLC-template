# 会话连续性模板

## 欢迎回来提示模板
当用户返回继续现有 AI-DLC 项目的工作时，呈现此提示：

```markdown
**欢迎回来！我看到您有一个正在进行的 AI-DLC 项目。**

根据您的 aidlc-state.md，这是您当前的状态：
- **项目**：[project-name]
- **当前阶段**：[INCEPTION/CONSTRUCTION/OPERATIONS]
- **当前步骤**：[阶段名称]
- **最后完成**：[最后完成的步骤]
- **下一步**：[要处理的下一步]

**您今天想做什么？**

A) 从上次停下的地方继续（[下一步描述]）
B) 审查之前的阶段（[显示可用阶段]）

[Answer]: 
```

## 强制要求：会话连续性说明
1. **检测到现有项目时始终首先读取 aidlc-state.md**
2. **从工作流文件解析当前状态**以填充提示
3. **强制要求：加载先前阶段产物** - 在恢复任何阶段之前，自动读取先前阶段的所有相关产物：
   - **逆向工程**：读取 architecture.md、code-structure.md、api-documentation.md
   - **需求分析**：读取 requirements.md、requirement-verification-questions.md
   - **用户故事**：读取 stories.md、personas.md、story-generation-plan.md
   - **应用设计**：读取应用设计产物（components.md、component-methods.md、services.md）
   - **设计（单元）**：读取 unit-of-work.md、unit-of-work-dependency.md、unit-of-work-story-map.md
   - **每单元设计**：读取 functional-design.md、nfr-requirements.md、nfr-design.md、infrastructure-design.md
   - **代码阶段**：读取所有代码文件、计划和所有先前产物
4. **按阶段智能上下文加载**：
   - **早期阶段（工作区检测、逆向工程）**：加载工作区分析
   - **需求/故事**：加载逆向工程 + 需求产物
   - **设计阶段**：加载需求 + 故事 + 架构 + 设计产物
   - **代码阶段**：加载所有产物 + 现有代码文件
5. **根据架构选择和当前阶段调整选项**
6. **显示具体的下一步**而不是通用描述
7. **在 audit.md 中记录连续性提示**并附上时间戳
8. **上下文摘要**：加载产物后，为用户提供所加载内容的简要摘要
9. **提问**：始终通过将问题放在 .md 文件中来提出澄清或用户反馈问题。不要在聊天会话中内联放置多项选择问题。

## 错误处理
如果在会话恢复期间产物缺失或损坏，请参阅 [error-handling.md](error-handling.md) 了解恢复程序指南。
