# Pandoc操作指南

## 一、基本语法

```bash
pandoc [输入文件] -o [输出文件] [选项]
```

------

## 二、常见格式转换

### 1️⃣ Markdown ↔ Word / PDF / HTML

```bash
pandoc a.md -o a.docx
pandoc a.md -o a.pdf
pandoc a.md -o a.html
pandoc a.docx -o a.md
```

### 2️⃣ 多文件合并

```bash
pandoc ch1.md ch2.md ch3.md -o book.pdf
```

------

## 三、常用选项（重点）

### 📌 指定输入/输出格式

```bash
-f markdown -t html
```

### 📌 指定模板

```bash
--template=template.tex
```

### 📌 目录（Table of Contents）

```bash
--toc --toc-depth=3
```

### 📌 数学公式支持

```bash
--mathjax        # HTML
--pdf-engine=xelatex   # PDF
```

### 📌 中文支持（PDF 必用）

```bash
--pdf-engine=xelatex -V mainfont="Songti SC"
```

------

## 四、Word（docx）进阶用法

### 📄 使用自定义 Word 样式

```bash
pandoc a.md -o a.docx --reference-doc=style.docx
```

------

## 五、PDF 生成（常用组合）

```bash
pandoc a.md -o a.pdf \
  --pdf-engine=xelatex \
  --toc \
  -V geometry:margin=2.5cm
```

------

## 六、代码高亮

```bash
--highlight-style=tango
```

------

## 七、常见问题速解

- ❌ 中文乱码 → 用 `xelatex`
- ❌ PDF 报错 → 先生成 `.tex` 排查
- ❌ Word 样式乱 → 用 `--reference-doc`

------

## 八、一句话模板（直接用）

```bash
pandoc input.md -o output.pdf --pdf-engine=xelatex --toc
```

------

