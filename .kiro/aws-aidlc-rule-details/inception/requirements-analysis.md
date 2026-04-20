# 需求分析（自适应）

**承担角色**：产品负责人

**自适应阶段**：始终执行。详细级别根据问题复杂性自适应。

**参见 [depth-levels.md](../common/depth-levels.md) 了解自适应深度说明**

## 前提条件
- 工作空间检测必须完成
- 逆向工程必须完成（如果是棕地项目）

## 执行步骤

### 步骤 1：加载逆向工程上下文（如果可用）

**如果是棕地项目**：
- 加载 `aidlc-docs/inception/reverse-engineering/architecture.md`
- 加载 `aidlc-docs/inception/reverse-engineering/component-inventory.md`
- 加载 `aidlc-docs/inception/reverse-engineering/technology-stack.md`
- 在分析请求时使用这些来理解现有系统

### 步骤 2：分析用户请求（意图分析）

#### 2.1 请求清晰度
- **清晰**：具体、定义明确、可操作
- **模糊**：一般、含糊、需要澄清
- **不完整**：缺少关键信息

#### 2.2 请求类型
- **新功能**：添加新功能
- **错误修复**：修复现有问题
- **重构**：改进代码结构
- **升级**：更新依赖项或框架
- **迁移**：迁移到不同技术
- **增强**：改进现有功能
- **新项目**：从头开始

#### 2.3 初始范围估计
- **单文件**：对一个文件的变更
- **单组件**：对一个组件/包的变更
- **多组件**：跨多个组件的变更
- **系统范围**：影响整个系统的变更
- **跨系统**：影响多个系统的变更

#### 2.4 初始复杂性估计
- **琐碎**：简单、直接的变更
- **简单**：清晰的实现路径
- **中等**：一些复杂性、多个考虑因素
- **复杂**：显著的复杂性、许多考虑因素

### 步骤 3：确定需求深度

**基于请求分析，确定深度：**

**最小深度** - 使用时机：
- 请求清晰简单
- 不需要详细需求
- 只记录基本理解

**标准深度** - 使用时机：
- 请求需要澄清
- 需要功能和非功能需求
- 正常复杂性

**全面深度** - 使用时机：
- 具有多个利益相关者的复杂项目
- 高风险或关键系统
- 需要可追溯性的详细需求

### 步骤 4：评估当前需求

分析用户提供的任何内容：
   - 意图陈述或描述（已在 audit.md 中记录）
   - 现有需求文档（如果提到则搜索工作空间）
   - 粘贴的内容或文件引用
   - 将任何非 markdown 文档转换为 markdown 格式

### 步骤 5：彻底的完整性分析

**关键**：使用全面分析来评估需求完整性。当存在任何模糊性或缺失细节时，默认提问。

**强制性**：评估所有这些领域，并对任何不清楚的领域提问：
- **功能需求**：核心功能、用户交互、系统行为
- **非功能需求**：性能、安全性、可扩展性、可用性
- **用户场景**：用例、用户旅程、边缘情况、错误场景
- **业务上下文**：目标、约束、成功标准、利益相关者需求
- **技术上下文**：集成点、数据需求、系统边界
- **质量属性**：可靠性、可维护性、可测试性、可访问性

**如有疑问，提出问题** - 不完整的需求导致糟糕的实现。

### 步骤 5.1：扩展适用性问题

**强制性**：扫描所有加载的扩展文件以查找 `## Applicability Question` 部分。对于声明了该部分的每个扩展，在步骤 6 中创建的澄清问题文件中包含该问题。收到答案后，在 `aidlc-docs/aidlc-state.md` 的 `## Extension Configuration` 下记录每个扩展的启用状态：

```markdown
## Extension Configuration
| Extension | Enabled | Decided At |
|---|---|---|
| [Extension Name] | [Yes/No] | Requirements Analysis |
```

### 步骤 6：生成澄清问题（主动方法）
   - **始终**创建 `aidlc-docs/inception/requirements/requirement-verification-questions.md`，除非需求异常清晰完整
   - 对任何缺失、不清楚或模糊的领域提问
   - 关注功能需求、非功能需求、用户场景和业务上下文
   - 请求用户直接在问题文档中填写所有 [Answer]: 标签
   - 如果为答案提供多项选择选项：
     - 将选项标记为 A、B、C、D 等
     - 确保选项互斥且不重叠
     - 始终包含自定义响应选项："X) Other (please describe after [Answer]: tag below)"
   - 在文档中等待用户答案
   - **强制性**：分析所有答案的模糊性，如果需要创建后续问题
   - **强制性**：继续提问直到所有模糊性解决或用户明确要求继续

### ⛔ 门控：等待用户答案
在所有 requirement-verification-questions.md 中的问题得到回答和验证之前，不要进入步骤 7。
向用户呈现问题文件并停止。

### 步骤 7：生成需求文档
   - **前提条件**：必须通过步骤 6 门控 — 所有答案已收到并分析
   - 创建 `aidlc-docs/inception/requirements/requirements.md`
   - 在顶部包含意图分析摘要：
     - 用户请求
     - 请求类型
     - 范围估计
     - 复杂性估计
   - 包含功能和非功能需求
   - 纳入用户对澄清问题的答案
   - 提供关键需求的简要摘要

### 步骤 8：更新状态跟踪

更新 `aidlc-docs/aidlc-state.md`：

```markdown
## Stage Progress
### 🔵 INCEPTION PHASE
- [x] Workspace Detection
- [x] Reverse Engineering (if applicable)
- [x] Requirements Analysis
```

### 步骤 9：记录并继续
   - 在 `aidlc-docs/audit.md` 中记录带时间戳的批准提示
   - 按此结构呈现完成消息：
     1. **完成公告**（强制性）：始终以此开始：

```markdown
# 🔍 Requirements Analysis Complete
```

     2. **AI 摘要**（可选）：提供需求的结构化要点摘要
        - 格式："需求分析已识别 [项目类型/复杂性]："
        - 列出关键功能需求（要点）
        - 列出关键非功能需求（要点）
        - 如果相关，提及架构考虑或技术决策
        - 不要包含工作流说明（"请审查"、"让我知道"、"进入下一阶段"、"在我们继续之前"）
        - 保持事实和内容为中心
     3. **格式化的工作流消息**（强制性）：始终以此确切格式结束：

```markdown
> **📋 <u>**REVIEW REQUIRED:**</u>**  
> Please examine the requirements document at: `aidlc-docs/inception/requirements/requirements.md`



> **🚀 <u>**WHAT'S NEXT?**</u>**
>
> **You may:**
>
> 🔧 **Request Changes** -  Ask for modifications to the requirements if required based on your review 
> [IF User Stories will be skipped, add this option:]
> 📝 **Add User Stories** - Choose to Include **User Stories** stage (currently skipped based on project simplicity)  
> ✅ **Approve & Continue** - Approve requirements and proceed to **[User Stories/Workflow Planning]**

---
```

**注意**：仅当用户故事阶段将被跳过时才包含"Add User Stories"选项。将 [User Stories/Workflow Planning] 替换为实际的下一阶段名称。

   - 在继续之前等待明确的用户批准
   - 记录带时间戳的批准响应
   - 在 aidlc-state.md 中更新需求分析阶段完成
