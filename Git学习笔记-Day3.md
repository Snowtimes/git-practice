# Git Day 3 学习笔记

> 学习日期：2026 年 4 月 18 日
> 学习主题：Git 分支入门 — 创建、切换、合并、删除

---

## 📌 一、什么是分支？

用"平行宇宙"来理解：

```
master ──●──●──●──●──────────────▶ 主线（稳定版）
              │
           feature ──●──●──●──▶  实验分支（开发中）
```

- `master` 是主线，放稳定的代码
- 新功能在独立分支上开发，不影响主线
- 开发完了再合并回主线

> 💡 **实际工作原则**：永远不要直接在 `master` 上改代码，而是开一个新分支改完再合并。

---

## 📌 二、分支核心命令

| 命令 | 作用 |
|------|------|
| `git branch` | 查看所有分支 |
| `git branch 分支名` | 创建新分支 |
| `git switch 分支名` | 切换到某个分支 |
| `git switch -c 分支名` | 创建并切换（一步完成） |
| `git merge 分支名` | 把指定分支合并到当前分支 |
| `git branch -d 分支名` | 删除分支 |

---

## 📌 三、本日完整操作流程

```powershell
# Step 1：进入仓库
cd D:\Git\git-practice

# Step 2：查看当前分支
git branch

# Step 3：创建新分支
git branch dev

# Step 4：查看分支列表
git branch

# Step 5：切换到 dev 分支
git switch dev

# Step 6：在 dev 分支上开发
notepad readme.txt
# → 添加新内容，保存关闭

# Step 7：提交到 dev 分支
git add .
git commit -m "dev 分支：添加新功能开发记录"

# Step 8：切回 master
git switch master

# Step 9：确认 master 内容没有被影响
notepad readme.txt
# → 验证 dev 的改动没有出现在 master

# Step 10：合并 dev 到 master
git merge dev

# Step 11：确认合并后的内容
notepad readme.txt

# Step 12：删除已完成的分支
git branch -d dev

# Step 13：同步到 GitHub
git push
```

---

## 📌 四、合并模式：Fast-forward

本次合并输出：
```
Fast-forward
 readme.txt | 7 ++++++-
 1 file changed, 6 insertions(+), 1 deletion(-)
```

**Fast-forward**（快进合并）：
- 当 master 没有新的提交，纯粹落后于 dev 时
- Git 直接把 master 的指针"快进"到 dev 的位置
- 最简单、最干净的合并方式

> ⚠️ **易错点**：如果 master 上有新的提交，合并可能会产生冲突，需要手动解决。冲突处理 Day 5 会学到。

---

## 📌 五、分支操作速查表

| 场景 | 命令 |
|------|------|
| 查看所有分支 | `git branch` |
| 创建分支 | `git branch 分支名` |
| 切换分支 | `git switch 分支名` |
| 创建并切换 | `git switch -c 分支名` |
| 合并到当前分支 | `git merge 分支名` |
| 删除分支 | `git branch -d 分支名` |
| 强制删除（未合并） | `git branch -D 分支名` |

---

## 📌 六、分支命名建议

| 类型 | 示例 |
|------|------|
| 功能开发 | `feature/login`, `feature/shopping-cart` |
| 修复 bug | `bugfix/fix-login-error` |
| 发布版本 | `release/v1.0` |
| 个人练习 | `dev`, `test`, `practice` |

---

## 📌 七、HEAD 指针与分支的关系

```
HEAD → master → c8f6b6b (最新提交)
                17b6014 (上一个提交)
                ...
```

- `HEAD` 永远指向当前所在的分支
- 切换分支时，`HEAD` 跟着移动
- 每个分支都是一条独立的提交链

---

## 📌 八、实际工作流程（重点）

```
1. 从 master 拉取最新代码
   git switch master
   git pull

2. 创建新功能分支
   git switch -c feature/新功能名

3. 在新分支上开发、提交
   git add .
   git commit -m "完成 XX 功能"

4. 切换回 master，合并功能分支
   git switch master
   git merge feature/新功能名

5. 删除功能分支，推送主分支
   git branch -d feature/新功能名
   git push
```

---

## 📌 九、遇到的坑

### 坑：cat 命令显示乱码

```
cat readme.txt
杩欐槸鎴戠殑绗﹀悎鏂囦欢锛
```

**原因**：PowerShell 默认编码不是 UTF-8，汉字显示为乱码。

**解决方法**：
- 用 `notepad readme.txt` 打开查看正常中文
- 后续统一用记事本查看文件内容

---

*笔记整理：星辰 ✦ | 2026-04-18*
