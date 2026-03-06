# 学习笔记模板

每次学习会话结束后，用此模板整理当次学习内容。文件命名格式：`YYYY-MM-DD-主题.md`。

```markdown
# 📖 学习笔记：[项目名称] - [主题]

> 日期：YYYY-MM-DD
> 学习范围：[涉及的模块/文件]

## 项目概况（如果是首次学习）
- 技术栈：...
- 核心功能：...

## 今日学习内容

### 1. [知识点标题]
**要点**：简述核心理解
**详细说明**：...
**关键代码**：
```代码片段```
**设计考量**：为什么这样实现
**个人理解**：（基于对话中用户的反馈和提问整理）

### 2. [知识点标题]
...

## 新学到的语法/特性
| 语法 | 含义 | 示例 |
|------|------|------|
| `go func()` | 启动 goroutine | `go process(data)` |

## 核心术语表
| 术语 | 解释 |
|------|------|
| ... | ... |

## 关键代码片段

关键代码直接嵌入笔记中（带注释），确保笔记长期可读——代码文件会变动、行号会漂移，但嵌入的快照不会。同时保留原始位置方便回源。

**`internal/handler/user.go:L42-L58`**（快照于 YYYY-MM-DD）
```go
// CreateUser 处理用户注册请求
func (h *Handler) CreateUser(c *gin.Context) {
    var req CreateUserRequest
    if err := c.ShouldBindJSON(&req); err != nil {  // 参数绑定 + 校验
        c.JSON(400, gin.H{"error": err.Error()})
        return
    }
    user, err := h.service.CreateUser(req)  // 调用 service 层
    if err != nil {
        c.JSON(500, gin.H{"error": "创建失败"})
        return
    }
    c.JSON(201, user)
}
```

**`internal/service/user.go:L30-L45`**（快照于 YYYY-MM-DD）
```go
// CreateUser 业务逻辑：校验 + 转换 + 持久化
func (s *Service) CreateUser(req CreateUserRequest) (*UserVO, error) {
    // ... 关键业务逻辑注释
}
```

## 架构/流程图
(嵌入学习过程中生成的 Mermaid 图)

## 常见陷阱备忘
- ⚠️ ...

## 关联笔记

标注与本次学习相关的其他笔记，逐渐构建知识网络：

- 与 [2024-01-15-入口分析.md](./2024-01-15-入口分析.md) 相关：main.go 中注册了这里的 handler
- 与 [2024-01-17-数据库操作层.md](./2024-01-17-数据库操作层.md) 相关：handler 调用 repo 层

## 待深入学习
- [ ] 模块 A 的错误处理机制
- [ ] 模块 B 的并发设计
- [ ] ...

## 学习心得
（提炼学习过程中用户表达的疑问和顿悟）
```
