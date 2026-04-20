# 应用设计 - 详细步骤

## 目的
**高层组件识别和服务层设计**

应用设计关注于：
- 识别主要功能组件及其职责
- 定义组件接口（不是详细的业务逻辑）
- 设计用于编排的服务层
- 建立组件依赖关系和通信模式

**注意**：详细的业务逻辑设计稍后在功能设计（每单元，构建阶段）中进行

## 前提条件
- 上下文评估必须完成
- 推荐需求评估（提供功能上下文）
- 推荐故事开发（用户故事指导设计决策）
- 执行计划必须指示应用设计阶段应执行

## 逐步执行

### 1. 分析上下文
- 阅读 `aidlc-docs/inception/requirements/requirements.md` 和 `aidlc-docs/inception/user-stories/stories.md`
- 识别关键业务能力和功能领域
- 确定设计范围和复杂性

### 2. 创建应用设计计划
- 生成带有应用设计复选框 [] 的计划
- 关注组件、职责、方法、业务规则和服务
- 每个步骤和子步骤都应该有一个复选框 []

### 3. 在计划中包含强制性设计产物
- **始终**在设计计划中包含这些强制性产物：
  - [ ] 生成带有组件定义和高层职责的 components.md
  - [ ] 生成带有方法签名的 component-methods.md（业务规则稍后在功能设计中详细说明）
  - [ ] 生成带有服务定义和编排模式的 services.md
  - [ ] 生成带有依赖关系和通信模式的 component-dependency.md
  - [ ] 验证设计完整性和一致性

### 4. 生成适合上下文的问题
**指令**：分析需求和故事，仅生成与此特定应用设计相关的问题。将以下类别用作灵感，而不是强制性检查清单。如果不适用，跳过整个类别。

- 使用 [Answer]: 标签格式嵌入问题
- 关注特定于此上下文的模糊性和缺失信息
- 仅在需要用户输入进行设计决策时生成问题

**示例问题类别**（根据需要调整）：
- **组件识别** - 仅当组件边界或组织不清楚时
- **组件方法** - 仅当方法签名需要澄清时（详细的业务规则稍后出现）
- **服务层设计** - 仅当服务编排或边界模糊时
- **组件依赖关系** - 仅当通信模式或依赖管理不清楚时
- **设计模式** - 仅当架构风格或模式选择需要用户输入时

### 5. 存储应用设计计划
- 保存为 `aidlc-docs/inception/plans/application-design-plan.md`
- 包含所有用于用户输入的 [Answer]: 标签
- 确保计划涵盖所有设计方面

### 6. 请求用户输入
- 要求用户直接在计划文档中填写 [Answer]: 标签
- 强调设计决策的重要性
- 提供关于完成 [Answer]: 标签的清晰说明

### 7. 收集答案
- 等待用户使用文档中的 [Answer]: 标签提供所有问题的答案
- 在所有 [Answer]: 标签完成之前不要继续
- 审查文档以确保没有 [Answer]: 标签留空

### 8. 分析答案（强制性）
在继续之前，您必须仔细审查所有用户答案：
- **模糊或含糊的回答**："混合"、"介于之间"、"不确定"、"取决于"
- **未定义的标准或术语**：引用没有明确定义的概念
- **矛盾的答案**：相互冲突的回答
- **缺失的设计细节**：缺乏具体指导的答案
- **组合选项的答案**：在没有明确决策规则的情况下合并不同方法的回答

### 9. 强制性后续问题
如果步骤 8 中的分析揭示了任何模糊的答案，您必须：
- 使用 [Answer]: 标签向计划文档添加具体的后续问题
- 在所有模糊性解决之前不要进入批准
- 所需后续问题的示例：
  - "您提到'A 和 B 的混合' - 什么具体标准应该决定何时使用 A vs B？"
  - "您说'介于 A 和 B 之间' - 您能定义确切的中间方法吗？"
  - "您表示'不确定' - 什么额外信息会帮助您决定？"
  - "您提到'取决于复杂性' - 您如何定义复杂性级别？"

### 10. 生成应用设计产物
- 执行批准的计划以生成设计产物
- 创建 `aidlc-docs/inception/application-design/components.md`，包含：
  - 组件名称和目的
  - 组件职责
  - 组件接口
- 创建 `aidlc-docs/inception/application-design/component-methods.md`，包含：
  - 每个组件的方法签名
  - 每个方法的高层目的
  - 输入/输出类型
  - 注意：详细的业务规则将在功能设计（每单元，构建阶段）中定义
- 创建 `aidlc-docs/inception/application-design/services.md`，包含：
  - 服务定义
  - 服务职责
  - 服务交互和编排
- 创建 `aidlc-docs/inception/application-design/component-dependency.md`，包含：
  - 显示关系的依赖矩阵
  - 组件之间的通信模式
  - 数据流图

### 11. 记录批准
- 在 `aidlc-docs/audit.md` 中记录带时间戳的批准提示
- 包含完整的批准提示文本
- 使用 ISO 8601 时间戳格式

### 12. 呈现完成消息

```markdown
# 🏗️ Application Design Complete

[AI-generated summary of application design artifacts created in bullet points]

> **📋 <u>**REVIEW REQUIRED:**</u>**  
> Please examine the application design artifacts at: `aidlc-docs/inception/application-design/`

> **🚀 <u>**WHAT'S NEXT?**</u>**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications to the application design if required
> [IF Units Generation is skipped:]
> 📝 **Add Units Generation** - Choose to include **Units Generation** stage (currently skipped)
> ✅ **Approve & Continue** - Approve design and proceed to **[Units Generation/CONSTRUCTION PHASE]**
```

### 13. 等待明确批准
- 在用户明确批准应用设计之前不要继续
- 批准必须清晰明确
- 如果用户请求变更，更新设计并重复批准过程

### 14. 记录批准响应
- 在 `aidlc-docs/audit.md` 中记录带时间戳的用户批准响应
- 包含确切的用户响应文本
- 清楚地标记批准状态

### 15. 更新进度
- 在 `aidlc-docs/aidlc-state.md` 中将应用设计阶段标记为完成
- 更新"当前状态"部分
- 准备过渡到下一阶段
