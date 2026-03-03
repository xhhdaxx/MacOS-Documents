# Conda的基本使用方法

## 🟢 1. 激活 conda 环境

```
conda activate <环境名>
```

例如激活 `base` 环境：

```
conda activate base
```

如果你遇到 `command not found: conda`，说明终端还没初始化 conda，可以先执行：

```
source ~/anaconda3/bin/activate
source /usr/local/anaconda3/bin/activate
```

（路径根据你安装的位置调整，Miniconda 可能是 `~/miniconda3/bin/activate`）

------

## 🔴 2. 退出 conda 环境

```
conda deactivate
```

- 连续执行几次可以逐级退出，直到回到系统默认环境。

------

## 🟡 3. 创建新环境

```
conda create -n <环境名> python=版本号
```

例如创建一个名为 `torch2_env` 的 Python 3.10 环境：

```
conda create -n torch2_env python=3.10

conda create -n ML_env python=3.10
```

------

## 🔵 4. 查看环境

- 查看已安装的环境：

```
conda env list
# 或
conda info --envs
```

- 查看当前环境安装的包：

```
conda list
```

------

## 🟣 5. 删除环境

```
conda remove -n <环境名> --all
```

例如删除 `torch2_env`：

```
conda remove -n torch2_env --all
```

------

## ⚪ 6. 安装/卸载包

- 安装包：

```
conda install 包名
```

例如：

```
conda install numpy
```

- 指定版本安装：

```
conda install numpy=1.23
```

- 卸载包：

```
conda remove 包名
```

------

## 🟠 7. 更新

- 更新 conda 本身：

```
conda update conda
```

- 更新环境里的所有包：

```
conda update --all
```

------

## 🟤 8. 导出/导入环境

- 导出环境配置：

```
conda env export > environment.yml
```

- 从配置文件创建环境：

```
conda env create -f environment.yml
```

------

总结一下常用流程：

1. 创建环境：`conda create -n myenv python=3.9`
2. 激活环境：`conda activate myenv`
3. 安装包：`conda install xxx`
4. 查看环境：`conda env list`
5. 退出环境：`conda deactivate`