## 🛠 一次性初始化（第一次把本地项目放到 GitHub 上）

1. **在 GitHub 上新建仓库**

   - 登录 [GitHub](https://github.com)，点右上角 **New repository**
   - 取个名字，比如 `MyProject`，保持空仓库（不要勾选 README / LICENSE）。

2. **打开终端进入本地文件夹**

   ```
   cd /Users/你的用户名/路径/到/项目文件夹
   ```

3. **初始化 Git 仓库（如果还没初始化过）**

   ```
   git init
   ```

4. **绑定 GitHub 远程仓库**
    替换为你自己的仓库地址：

   ```
   git remote add origin https://github.com/你的用户名/MyProject.git
   ```

5. **添加文件并提交**

   ```
   git add .
   git commit -m "first commit"
   ```

6. **推送到 GitHub**

   ```
   git branch -M main   # 把默认分支改为 main（GitHub 默认是 main）
   git push -u origin main
   ```

------

## 🔄 后续保持更新（之后每次改动时）

1. **查看文件变动**

   ```
   git status
   ```

2. **把修改加入暂存区**

   ```
   git add .
   ```

3. **提交修改**

   ```
   git commit -m "修改了xxx功能"
   ```

4. **推送到 GitHub**

   ```
   git push
   ```

5. **撤销上一次commit**

   ```sh
   git reset HEAD~1
   ```


### 🧹 如何取消 `git init`（即取消 Git 仓库化）

只需要删除 `.git` 文件夹即可：

```
rm -rf .git
```

这样，当前目录就恢复为普通文件夹，不再受 Git 管理。