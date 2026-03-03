## 🔧 Mac 上安装 conda 的方法

通常有两种选择：

### 方法一：安装 **Miniconda（推荐，轻量级）**

👉 适合只想要 conda 功能，不需要自带一堆科学计算包的人。

1. 下载 Miniconda 安装包 (适配 Apple M1/M2 ARM 芯片)：

```
curl -fsSL https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh -o Miniconda3-latest-MacOSX-arm64.sh
```

1. 运行安装脚本：

```
bash Miniconda3-latest-MacOSX-arm64.sh
```

1. 按照提示一路回车/yes，默认安装到 `~/miniconda3`。
2. 安装完成后，初始化 conda：

```
~/miniconda3/bin/conda init zsh
```

1. 关闭终端重新打开，测试：

```
conda --version
```

------

### 方法二：安装 **Anaconda（完整版）**

👉 自带很多科学计算和数据分析包（numpy、pandas、jupyter、scikit-learn 等），但体积比较大。

1. 下载 Anaconda 安装包 (ARM 版)：

```
curl -fsSL https://repo.anaconda.com/archive/Anaconda3-2024.06-1-MacOSX-arm64.sh -o Anaconda3-MacOSX-arm64.sh
```

1. 运行安装：

```
bash Anaconda3-MacOSX-arm64.sh
```

1. 按照提示完成安装（默认路径 `~/anaconda3`）。
2. 初始化：

```
~/anaconda3/bin/conda init zsh
```

1. 重新打开终端后，测试：

```
conda --version
```

------

### 🚀 验证是否安装成功

安装后，你应该能看到类似：

```
conda 24.5.0
```