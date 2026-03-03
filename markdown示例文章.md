# Markdown 格式演示文章

## Introduction | 引言

This article demonstrates various **Markdown formatting features**. This is a *comprehensive guide* showing you how to use different elements in Markdown.

本文演示了各种 **Markdown 格式功能**。这是一个*全面的指南*，向您展示如何在 Markdown 中使用不同的元素。

---

## 1. Text Formatting | 文本格式

### 字体样式示例

- **粗体文本** - This is **bold text**
- *斜体文本* - This is *italic text*
- ***粗斜体文本*** - This is ***bold and italic***
- ~~删除线文本~~ - This is ~~strikethrough~~
- `行内代码` - This is `inline code`

### 引用示例

> This is a blockquote.
> 这是一个引用块。
>
> You can have multiple lines.
> 可以有多行内容。

---

## 2. Code Blocks | 代码块

### Python 示例 | Python Example

```python
# 计算斐波那契数列
def fibonacci(n):
    """Calculate Fibonacci sequence"""
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Print first 10 numbers
for i in range(10):
    print(f"F({i}) = {fibonacci(i)}")
```

### JavaScript 示例

```javascript
// Async function example
async function fetchData(url) {
    try {
        const response = await fetch(url);
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Error:', error);
    }
}
```

### Bash 命令示例

```bash
# List files with details
ls -la

# Create a new directory
mkdir my-project && cd my-project

# Initialize git repository
git init
```

---

## 3. Tables | 表格

### 编程语言对比表 | Programming Languages Comparison

| 语言 Language | 类型 Type | 用途 Use Case | 难度 Difficulty |
|:-------------:|:---------:|:-------------|:---------------:|
| Python | 解释型 | 数据科学、AI、Web开发 | ⭐⭐ |
| JavaScript | 解释型 | 前端、后端开发 | ⭐⭐ |
| C++ | 编译型 | 系统编程、游戏开发 | ⭐⭐⭐⭐ |
| Go | 编译型 | 云原生、微服务 | ⭐⭐⭐ |
| Rust | 编译型 | 系统编程、安全关键 | ⭐⭐⭐⭐⭐ |

### 项目进度表 | Project Progress

| 任务 Task | 状态 Status | 负责人 Owner | 截止日期 Deadline |
|----------|:-----------:|:------------|:----------------:|
| 需求分析 | ✅ 完成 | 张三 | 2024-01-15 |
| 原型设计 | 🔄 进行中 | 李四 | 2024-01-20 |
| 开发实施 | ⏳ 待开始 | 王五 | 2024-02-01 |
| 测试验收 | ⏳ 待开始 | 赵六 | 2024-02-15 |

---

## 4. Lists | 列表

### 有序列表 | Ordered List

1. 第一项 - First item
2. 第二项 - Second item
   1. 子项目 2.1 - Subitem 2.1
   2. 子项目 2.2 - Subitem 2.2
3. 第三项 - Third item

### 无序列表 | Unordered List

- 主要功能点
  - 用户认证
  - 数据管理
  - 报表生成
- 系统设置
  - 配置管理
  - 权限控制

### 任务列表 | Task List

- [x] 完成 Markdown 语法学习
- [x] 编写示例文档
- [ ] 添加更多示例
- [ ] 发布到博客

---

## 5. Links & Images | 链接与图片

### 链接示例

- [Markdown 官方文档](https://www.markdownguide.org/)
- [GitHub 风格的 Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

### 图片示例

![ProteinMPNN](/Users/hexinhao/data/paper/ProteinMPNN/ProteinMPNN.png)

*Figure 1: 图片标题说明 | Image Caption*

---

## 6. Mathematical Formulas | 数学公式

### 行内公式

爱因斯坦质能方程：$E = mc^2$

### 块级公式

二次方程求根公式：

$$
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
$$

泰勒展开：

$$
e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!} = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots
$$

---

## 7. Alerts & Callouts | 警告与提示

> **💡 提示 | Tip**
>
> Markdown 是一种轻量级标记语言，让你可以使用易读易写的纯文本格式编写文档。

> **⚠️ 警告 | Warning**
>
> 不同的 Markdown 解析器可能对某些语法的支持有所不同。

> **❌ 错误 | Error**
>
> 请确保代码块的语法正确，否则可能无法正常渲染。

---

## 8. Horizontal Rules | 分隔线

以上是 Markdown 的各种格式示例。希望这篇文章对你有所帮助！

The above demonstrates various Markdown formatting elements. Hope this article is helpful to you!

---

**文章总结 | Article Summary**

| 元素 Element | 语法示例 Syntax |
|-------------|:---------------|
| 粗体 Bold | `**text**` |
| 斜体 Italic | `*text*` |
| 代码 Code | `` `code` `` |
| 链接 Link | `[text](url)` |
| 图片 Image | `![alt](url)` |
| 表格 Table | ` \| header \|` |

---

*最后更新 | Last Updated: 2024-03-03*
