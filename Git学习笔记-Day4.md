# Git Day 4 学习笔记

> 学习日期：2026 年 4 月 20 日
> 学习主题：GitHub 协作 — Fork 与 Pull Request

---

## 📌 一、核心概念

### Fork 是什么？

**Fork = 把别人的仓库复制一份到自己的账号**

```
原仓库（A）
https://github.com/别人/项目名
        ↓ Fork
你的仓库（B）
https://github.com/你/项目名
```

- 你可以在 B 上随便改，完全不影响 A 的原始代码
- 适合：参与开源项目、贡献代码

---

### Pull Request（PR）是什么？

**PR = 申请把你的改动合并到原仓库**

```
你的 Fork 仓库
   your-branch
        ↓
     PR 申请
        ↓
原仓库作者审查
        ↓
  接受 → 合并到主分支
  拒绝 → 关闭 PR
```

---

## 📌 二、完整工作流程

```
1. 在 GitHub 找到想参与的项目
         ↓
2. 点 Fork → 复制到自己账号
         ↓
3. 在自己的 Fork 上修改文件
         ↓
4. 点 Contribute → Open pull request
         ↓
5. 原作者收到通知，审查代码
         ↓
6. 作者同意 → 合并到主仓库 ✅
```

---

## 📌 三、本日实操记录

### 1. Fork 练习仓库

目标仓库：https://github.com/firstcontributions/first-contributions

操作：
1. 打开仓库页面
2. 点右上角 **Fork** 按钮
3. 等待跳转完成
4. 确认地址变为：`https://github.com/Snowtimes/first-contributions`

---

### 2. 在 GitHub 网页直接修改文件

目标：在 Contributors.md 末尾添加自己的名字

操作：
1. 打开自己的 Fork 仓库
2. 点击 `Contributors.md` 文件
3. 点右上角 **铅笔图标** ✏️
4. 末尾添加：`[snow](https://github.com/Snowtimes)`
5. 点 **Commit changes** 确认

---

### 3. 发起 Pull Request

操作：
1. 回到仓库主页
2. 点顶部 **Contribute** 按钮
3. 点 **Open pull request**
4. 确认改动内容
5. 点 **Create pull request**

---

### 4. PR 被合并

结果：
```
Pull request successfully merged and closed
You're all set — the branch has been merged.
```

意味着：你的名字已正式加入项目的全球贡献者列表！

---

## 📌 四、常用命令补充

### Fork 后同步上游更新

```powershell
# 添加上游仓库地址（只需要做一次）
git remote add upstream https://github.com/原仓库地址.git

# 获取上游最新代码
git fetch upstream

# 合并到本地主分支
git switch master
git merge upstream/master
```

---

## 📌 五、GitHub 协作场景速查

| 场景 | 操作位置 |
|------|---------|
| Fork 项目 | GitHub 网页，点 Fork |
| 修改文件 | GitHub 网页，点铅笔图标 |
| 提交改动 | GitHub 网页，Commit changes |
| 创建分支 | GitHub 网页，Branch 下拉菜单 |
| 发起 PR | GitHub 网页，Contribute → Open pull request |
| 查看 PR 状态 | 原仓库的 Pull requests 页面 |

---

## 📌 六、易错点提醒

> ⚠️ **不要在原仓库上直接修改** —— 应该先 Fork 到自己账号

> ⚠️ **PR 合并需要原仓库作者审核** —— 不是自己点了就能合并

> ⚠️ **Fork 的仓库和原仓库是两套独立的代码** —— 需要通过 PR 才能同步改动

---

## 📌 七、同步进度更新

| 天数 | 状态 |
|------|------|
| Day 1 | ✅ Git 安装、配置、本地操作 |
| Day 2 | ✅ 进阶操作：diff / restore / log |
| Day 3 | ✅ 分支操作：branch / switch / merge |
| Day 4 | ✅ GitHub 协作：Fork / PR |
| Day 5 | ⬜ 待学 |
| Day 6 | ⬜ 待学 |
| Day 7 | ⬜ 待学 |

---

*笔记整理：星辰 ✦ | 2026-04-20*
