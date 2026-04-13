# Git Day 1 学习笔记

> 学习日期：2026 年 4 月 13 日
> 学习主题：Git 入门 — 安装、配置、本地操作、远程同步

---

## 📌 一、安装验证

### 安装检查命令

```powershell
git --version
```

### ✅ 成功标识

```
git version 2.53.0.windows.2
```

> ⚠️ **易错点**：如果提示 `'git' 不是内部或外部命令`，说明 PATH 环境变量没配好。解决方法：重新运行 Git 安装程序，选择 "Git from the command line and also from 3rd-party software"。

---

## 📌 二、安装后必做配置

### 配置命令

```powershell
# 设置用户名
git config --global user.name "你的名字"

# 设置邮箱（建议与 GitHub 账号邮箱一致）
git config --global user.email "你的邮箱@example.com"
```

### 查看配置

```powershell
git config --global --list
```

### ✅ 正确输出示例

```
user.name=snow
user.email=happyxinghan@163.com
```

> ⚠️ **易错点**：邮箱必须和 GitHub 账号邮箱一致，否则提交记录不会关联到 GitHub 贡献统计。

---

## 📌 三、核心概念（新手必知）

| 概念 | 通俗理解 | 类比 |
|------|---------|------|
| **Repository（仓库）** | 被 Git 管理的文件夹 | 游戏存档文件夹 |
| **Commit（提交）** | 一次存档，附带说明 | 游戏存档点 |
| **Branch（分支）** | 平行宇宙，实验新功能 | 游戏不同路线 |
| **暂存区（Stage）** | 等待存档的文件集合 | 放进存档前的小篮子 |
| **Remote（远程）** | 云端备份（如 GitHub） | 游戏云存档 |

---

## 📌 四、核心命令速查表

### 本地操作

```powershell
# 初始化新仓库
git init

# 查看文件状态
git status

# 把文件加入暂存区
git add 文件名         # 单个文件
git add .             # 所有修改的文件

# 正式提交（存档）
git commit -m "备注说明"

# 查看提交历史
git log --oneline
```

### 远程操作

```powershell
# 添加远程仓库地址
git remote add origin https://github.com/用户名/仓库名.git

# 推送到远程（首次）
git push -u origin master

# 推送（之后）
git push

# 从远程拉取最新代码
git pull
```

---

## 📌 五、今日完整操作流程

### 场景：创建本地仓库并同步到 GitHub

```powershell
# Step 1：新建文件夹并进入
cd D:\Git
mkdir git-practice
cd git-practice

# Step 2：初始化仓库
git init

# Step 3：新建文件（用记事本编辑）
notepad readme.txt
# → 写内容后保存关闭

# Step 4：检查状态（此时为 Untracked）
git status

# Step 5：加入暂存区（变为绿色）
git add readme.txt
git status

# Step 6：正式提交
git commit -m "添加 readme.txt 文件"

# Step 7：查看提交记录
git log --oneline

# Step 8：连接 GitHub 远程仓库
git remote add origin https://github.com/Snowtimes/git-practice.git

# Step 9：推送到 GitHub
git push -u origin master
```

---

## 📌 六、常见问题与解决

| 问题 | 原因 | 解决方法 |
|------|------|---------|
| `'git' 不是内部命令` | PATH 没配好 | 重新安装，勾选 PATH 选项 |
| push 要输密码且报错 | GitHub 已停用密码认证 | 使用 SSH Key 或 GitHub Token |
| 所有文件都显示 changed | CRLF 换行符问题 | 安装时选 "Checkout Windows-style" 或配置 `core.autocrlf` |
| 提交不计入 contributions | 邮箱与 GitHub 不一致 | 改为一致的邮箱，重新 commit |
| Vim 不知道怎么退出 | 默认编辑器选了 Vim | 改为 VS Code 或记事本 |

---

## 📌 七、新手最常踩的 5 个坑（总结）

> 🔴 **坑 1**：安装时选了 Vim 编辑器 → commit 时弹黑框不会操作
> → 改用 VS Code 或记事本

> 🔴 **坑 2**：不配置 user.name 和 user.email → 提交记录混乱
> → 安装完第一件事就配置

> 🔴 **坑 3**：不处理 CRLF 换行符 → 所有文件显示被修改
> → Windows 用户安装时选对应选项

> 🔴 **坑 4**：PATH 没配好 → 命令找不到
> → 重新安装，选第二项 PATH 配置

> 🔴 **坑 5**：用密码 push → GitHub 拒绝认证
> → 配置 SSH Key 或使用 Token

---

## 📌 八、下一步学习路径

- [ ] **分支操作**：创建、切换、合并分支
- [ ] **撤销修改**：reset、revert、checkout 的区别
- [ ] **Git 冲突**：多人协作时的冲突处理
- [ ] **SSH Key**：配置免密登录 GitHub
- [ ] **.gitignore**：忽略不需要跟踪的文件

---

## 📌 九、推荐学习资源

- 官方文档：https://git-scm.com/book/zh/v2
- 交互式学习：https://learngitbranching.js.org/
- 视频教程：B 站搜索 "Git 入门"

---

*笔记整理：星辰 ✦ | 2026-04-13*
