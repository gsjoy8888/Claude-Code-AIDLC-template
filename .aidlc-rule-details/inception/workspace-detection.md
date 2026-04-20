# 工作空间检测

**目的**：确定工作空间状态并检查现有的 AI-DLC 项目

## 步骤 1：检查现有的 AI-DLC 项目

检查 `aidlc-docs/aidlc-state.md` 是否存在：
- **如果存在**：从上一阶段恢复（从之前的阶段加载上下文）
- **如果不存在**：继续进行新项目评估

## 步骤 2：扫描工作空间中的现有代码

**确定工作空间是否有现有代码：**
- 扫描工作空间中的源代码文件（.java、.py、.js、.ts、.jsx、.tsx、.kt、.kts、.scala、.groovy、.go、.rs、.rb、.php、.c、.h、.cpp、.hpp、.cc、.cs、.fs 等）
- 检查构建文件（pom.xml、package.json、build.gradle 等）
- 查找项目结构指示器
- 识别工作空间根目录（不是 aidlc-docs/）

**记录发现：**
```markdown
## Workspace State
- **Existing Code**: [Yes/No]
- **Programming Languages**: [List if found]
- **Build System**: [Maven/Gradle/npm/etc. if found]
- **Project Structure**: [Monolith/Microservices/Library/Empty]
- **Workspace Root**: [Absolute path]
```

## 步骤 3：确定下一阶段

**如果工作空间为空（无现有代码）**：
- 设置标志：`brownfield = false`
- 下一阶段：需求分析

**如果工作空间有现有代码**：
- 设置标志：`brownfield = true`
- 检查 `aidlc-docs/inception/reverse-engineering/` 中是否存在逆向工程产物
- **如果逆向工程产物存在**：加载它们，跳转到需求分析
- **如果没有逆向工程产物**：下一阶段是逆向工程

## 步骤 4：创建初始状态文件

创建 `aidlc-docs/aidlc-state.md`：

```markdown
# AI-DLC State Tracking

## Project Information
- **Project Type**: [Greenfield/Brownfield]
- **Start Date**: [ISO timestamp]
- **Current Stage**: INCEPTION - Workspace Detection

## Workspace State
- **Existing Code**: [Yes/No]
- **Reverse Engineering Needed**: [Yes/No]
- **Workspace Root**: [Absolute path]

## Code Location Rules
- **Application Code**: Workspace root (NEVER in aidlc-docs/)
- **Documentation**: aidlc-docs/ only
- **Structure patterns**: See code-generation.md Critical Rules

## Stage Progress
[Will be populated as workflow progresses]
```

## 步骤 5：呈现完成消息

**对于棕地项目：**
```markdown
# 🔍 Workspace Detection Complete

Workspace analysis findings:
• **Project Type**: Brownfield project
• [AI-generated summary of workspace findings in bullet points]
• **Next Step**: Proceeding to **Reverse Engineering** to analyze existing codebase...
```

**对于绿地项目：**
```markdown
# 🔍 Workspace Detection Complete

Workspace analysis findings:
• **Project Type**: Greenfield project
• **Next Step**: Proceeding to **Requirements Analysis**...
```

## 步骤 6：自动继续

- **无需用户批准** - 这仅供参考
- 自动进入下一阶段：
  - **棕地项目**：逆向工程（如果没有现有产物）或需求分析（如果产物存在）
  - **绿地项目**：需求分析
