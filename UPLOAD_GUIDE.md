# 首次上传与发布 APK

已创建仓库：公开 https://github.com/1999-Lxinz/DePra，私有 https://github.com/1999-Lxinz/DePra-Source。不要混用目录或仓库地址。APK放在两个包的release-assets中，该目录被Git忽略，文件仅用作Release附件。


本次本地目录已初始化 Git（main）并完成首次提交，origin 已配置为上面对应仓库；不要重复执行 git init 或 remote add。推送状态由本次完成报告说明。

## 1. 上传仓库文件

先登录本人 GitHub。可使用 GitHub Desktop：分别把 public-distribution、private-source 添加为本地仓库，提交文件，绑定对应仓库并 Push。私有源码必须确认远端仍为 Private。

终端首次上传：先进入相应目录，执行下列命令。两个目录各自执行一次；不是在原 app-dev 工作区执行。Git 认证使用本人配置的 SSH/凭据管理器/Token，不能使用普通账号密码。不要把 Token 写入 remote URL、脚本或仓库。

公开目录 public-distribution：

```sh
git init -b main
git add .
git diff --cached --stat
git commit -m "Add DePra project introduction and screenshots"
git remote add origin https://github.com/1999-Lxinz/DePra.git
git branch -M main
git push -u origin main
```

私有目录 private-source：

```sh
git init -b main
git add .
git diff --cached --stat
git commit -m "Add DePra private source and documentation"
git remote add origin https://github.com/1999-Lxinz/DePra-Source.git
git branch -M main
git push -u origin main
```

命令按空仓库/未初始化副本编写。如果已操作过，不重复初始化、添加remote或覆盖现有提交；按实际git status继续。不要force push。如果git commit提示署名缺失，在该目录用git config user.name和user.email配置你自己的提交署名；不必使用真实隐私邮箱，可用GitHub提供的noreply邮箱。

网页方式：空仓库页面选择 uploading an existing file，上传目录内的文件和 docs（含截图），提交到main。不要上传整个ZIP，不要选release-assets、.DS_Store或私有源码到公开仓库；保留LICENSE和.gitignore。大量源码文件优先用GitHub Desktop或终端，避免遗漏隐藏文件。

## 2. 在公开仓库发布测试 APK

1. 打开 https://github.com/1999-Lxinz/DePra，先确认main已有介绍文件。
2. 点击 Releases → Draft a new release（首个版本也可能显示 Create a new release）。
3. Choose a tag 输入 v0.3.3 并创建，Target 选 main。
4. 标题写 DePra 0.3.3 测试版；描述复制公开目录 RELEASE_NOTES.md。
5. 在二进制附件上传区域添加 release-assets/DePra-0.3.3.apk、SHA256SUMS.txt、PACKAGE_INFO.txt；不是把文件加入 Git 提交。
6. 勾选 This is a pre-release，先 Save draft 核对文件与说明，再 Publish release。
7. 从 Release 的 Assets 点击 APK，复制实际下载链接。固定文件名与标签对应时应是 https://github.com/1999-Lxinz/DePra/releases/download/v0.3.3/DePra-0.3.3.apk。
8. README 已链接公开仓库的 Releases 页面，无需替换下载地址。新版本发布后，用户进入同一页面，在 Assets 下载对应 APK。

不必在私有仓库再发布一次APK，私有Release要求访问权限，不能作为普通用户公开下载入口。公共README不提供私有源码下载。

## 3. 后续更新

每次新包使用新版本/标签，递增versionCode，保留原应用签名。创建新的Release，上传对应APK与校验值，再改README下载链接。不要在同一标签下换掉不同内容的包；测试版继续标pre-release。

GitHub自动生成的Source code(zip/tar.gz)是仓库文件，不是App安装包；请让用户下载你手工上传的.apk附件。此包仍为0.3.3手机测试版，发布不代表商店验收。公开APK也可能构成专利披露；若仍计划申请专利，应先完成评估。

官方说明：https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository

## 当前执行结果（2026-10-12）

两个本地仓库已经初始化并推送 main，公开仓库仅包含说明与截图，私有仓库存放源码。官方测试 APK 已作为公开仓库 v0.3.3 的 Release 附件发布：
https://github.com/1999-Lxinz/DePra/releases/tag/v0.3.3

不要重复执行首次 git init 或 remote add。后续修改在对应目录 git add、git commit、git push 即可。APK继续作为Release附件，不进入Git提交。
