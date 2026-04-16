# Git Day 2 学习笔记

> 学习日期：2026 年 4 月 17 日
> 学习主题：Git 进阶操作 — 修改、撤销、差异查看

---

## 📌 一、上次回顾

| 命令 | 作用 |
|------|------|
| `git init` | 初始化仓库 |
| `git add` | 加入暂存区 |
| `git commit -m` | 提交存档 |
| `git push` | 推送到 GitHub |

---

## 📌 二、本日新学命令

### 1. 查看状态：`git status`

```powershell
git status
```

| 状态 | 含义 |
|------|------|
| `Untracked` | 新文件，Git 还没跟踪 |
| `Changes not staged for commit` | 文件已修改，还没 add |
| `Changes to be committed` | 已 add，已进入暂存区 |
| `nothing to commit, working tree clean` | 没有任何改动 |

> ⚠️ **易错点**：`nothing to commit` 不一定是好事 —— 可能是你忘了保存文件，也可能是真的没有改动。

---

### 2. 查看差异：`git diff`

```powershell
git diff 文件名       # 查看某个文件的改动
git diff             # 查看所有文件的改动
```

**输出格式解读：**
```diff
- 这行是旧内容（被删除了）
+ 这行是新内容（新增的）
```

> 💡 **技巧**：diff 里的 `-` 和 `+` 是相对于**上一次 commit** 来说的，不是绝对意义上的删除/新增。

---

### 3. 撤销操作：`git restore`

这是 Day 2 **最重要的命令**，分三种场景：

#### 场景 A：改了文件，但还没 add，想直接丢弃

```powershell
# 方法一（推荐）
git restore 文件名

# 方法二（旧写法）
git checkout -- 文件名
```

**效果**：文件直接还原到上一次 commit 的状态，改动全部丢失。

---

#### 场景 B：已经 add 了，想把文件从暂存区移出来

```powershell
git restore --staged 文件名
```

**效果**：文件移出暂存区，但改动保留（还是 modified 状态）。

---

#### 场景 C：commit 了，想撤销这次提交

```powershell
git reset --soft HEAD~1
```

| 参数 | 效果 |
|------|------|
| `--soft` | 撤销 commit，改动保留在暂存区 |
| `--mixed`（默认） | 撤销 commit，改动保留在 working tree |
| `--hard` | 撤销 commit，所有改动全部丢失 ⚠️ |

> ⚠️ **易错点**：`--hard` 会直接删除改动，新手慎用！用之前务必确认。

---

### 4. 查看历史：`git log`

```powershell
git log                 # 详细历史
git log --oneline       # 简洁历史（推荐）
```

**--oneline 输出示例：**
```
5c185ff (HEAD -> master) 更新 readme：添加Day2 学习记录
9f30f71 (origin/master) 添加 Git Day1 学习笔记
fda13e2 添加 readme.txt 文件
```

---

## 📌 三、本日完整操作流程

```powershell
# Step 1：进入仓库
cd D:\Git\git-practice

# Step 2：修改文件
notepad readme.txt
# → 添加新内容，保存关闭

# Step 3：查看状态
git status

# Step 4：查看改动
git diff readme.txt

# Step 5：加入暂存区
git add readme.txt

# Step 6：提交存档
git commit -m "更新 readme：添加Day2 学习记录"

# Step 7：查看历史
git log --oneline

# Step 8：同步到 GitHub
git push
```

---

## 📌 四、撤销操作速查表

| 场景 | 命令 |
|------|------|
| 改了文件，还没 add，想丢弃 | `git restore 文件名` |
| add 了，想取消暂存（保留改动） | `git restore --staged 文件名` |
| commit 了，想撤销（保留改动在 working tree） | `git reset HEAD~1` 或 `git reset --mixed HEAD~1` |
| commit 了，想撤销（保留改动在暂存区） | `git reset --soft HEAD~1` |
| commit 了，想全部丢弃 | `git reset --hard HEAD~1` ⚠️ |

---

## 📌 五、HEAD 指针概念

`HEAD` 是一个指针，指向当前分支的最新一次 commit。

```
HEAD → master → 5c185ff (最新提交)
                9f30f71 (上一个提交)
                fda13e2 (第一个提交)
```

- `HEAD~1` = 上一次 commit
- `HEAD~2` = 上两次 commit
- 以此类推

---

## 📌 六、本日遇到的坑

### 坑：git push 报错 "Failed to connect to github.com port 443"

```
fatal: unable to access 'https://github.com/Snowtimes/git-practice/':
Failed to connect to github.com port 443 after 21090 ms:
Could not connect to server
```

**原因**：网络问题，GitHub 443 端口无法连接。

**解决方法**：
- 检查网络是否正常
- 重启路由器或切换网络
- 稍后再试

---

## 📌 七、常用场景总结

```
改文件
  ↓
git status        ← 看状态
  ↓
git diff          ← 看变化
  ↓
git add .         ← 暂存
  ↓
git commit -m    ← 存档
  ↓
git log --oneline ← 确认
  ↓
git push          ← 同步云端
```

---

*笔记整理：星辰 ✦ | 2026-04-17*
