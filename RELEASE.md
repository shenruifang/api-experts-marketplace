# 发布到 GitHub 的操作步骤

已备好的东西都在本目录下：

| 文件 | 用途 |
|------|------|
| `README.md` | 仓库首页（复制一份放在仓库根目录） |
| `api-experts-marketplace/` | 市场源内容，即仓库的主体 |
| `api-experts-marketplace-v1.0.zip` | 打好的分发包，**上传到 Release**（在上一级目录） |

---

## 第 1 步：建仓库

在 GitHub 网页新建仓库，建议：

- Repository name：`api-experts-marketplace`
- 可见性：**Public**（否则别人拿不到 zip 直链）
- 勾选 Add a README（后面会被我们的 README 覆盖）

或者用命令行（需先装 `gh` 或配置好 git 凭据）：

```bash
cd D:\创建专家\github-repo
git init
git add .
git commit -m "feat: 原料药立项评估团 v1.0（精简公开版）"
git branch -M main
git remote add origin https://github.com/<你的用户名>/api-experts-marketplace.git
git push -u origin main
```

> 当前这台机器没有装 `gh`，git 已就绪（v2.55）。走命令行的话需要先配置 GitHub 凭据（PAT 或 SSH）。

## 第 2 步：发 Release

1. 进仓库页面右侧 **Releases** → **Create a new release**
2. Tag：`v1.0`，Release title：`原料药立项评估团 v1.0`
3. 把 `api-experts-marketplace-v1.0.zip` **拖进附件区**上传
4. 点 **Publish release**

Release 说明可粘贴：

```markdown
原料药立项评估团首个公开版本。

- 主理人 + 9 位成员，覆盖市场窗口、合成路线、全成本与财务、专利与注册、质量与 EHS、供应链、能力与资源、商业化、风险决策
- 方法论底座：五维决策模型（交集关系）+ 阶段门流程
- 输出：调研报告 / 立项报告 / 开题报告，决策门四结论 Go / Kill / Recycle / Hold

安装：在 WorkBuddy 中添加市场源，填入下方 zip 直链；或下载解压后手动注册（见 README）。
```

## 第 3 步：拿到市场源直链

发布完成后，zip 的直链格式为：

```
https://github.com/<你的用户名>/api-experts-marketplace/releases/download/v1.0/api-experts-marketplace-v1.0.zip
```

在 Release 页面的附件上**右键 → 复制链接地址**即可确认实际链接。

把这个链接发给别人，对方在 WorkBuddy 中添加市场源即可搜索安装。

## 第 4 步：以后更新

1. 改 `api-experts-marketplace/plugins/api-project-evaluation/` 下的内容
2. 重新打包成新版本 zip（文件名带版本号）
3. 发新 Release（`v1.1`、`v2.0`…）

**注意**：如果换了 zip 文件名，直链会变，已添加旧源的用户需要重新添加。想让老用户无缝更新，就**始终用同一个文件名**（如 `api-experts-marketplace.zip`）覆盖上传同一 Tag 的资产。

---

## 版本记录

| 版本 | 说明 |
|------|------|
| v1.0 | 首个公开版。精简版：含完整方法论框架与团队机制，不含任何企业内部资料 |
