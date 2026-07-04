# 🚀 1.9.0 迁移指南
> 💡 **肆说**：旧版迁移指南，新安装的不用看。

## 如何从 main/dev 分支迁移到新分支？

***推荐全新安装。*** 但如果你想用现有的 SillyTavern 副本，请按以下步骤操作。

**重要！** 做任何操作之前，先做**完整备份**。过程中你**可能丢失数据**，别忽略这个警告。

### Git 安装

1. 在 SillyTavern 安装文件夹打开终端（cmd、PowerShell、Termux 等）
2. 输入 `git fetch` 然后 `git pull` 拉取更新
3. 你可能会丢失设置。你有备份吗？`git switch release` 或 `git switch staging` 切换分支
4. 如果没报错就跳过。你可能看到类似错误：
   ```
   error: Your local changes to the following files would be overwritten by checkout:
    config.conf
    public/css/bg_load.css
    public/settings.json
   ```
   如果你不在乎这些设置文件被替换，`git switch -f release` 或 `git switch -f staging` 强制切换。如果在乎，从备份恢复。
5. 输入 `npm install` 然后 `npm run start` 测试一切是否正常

### fatal: invalid reference: release

如果你从旧的远程仓库只克隆了单个分支，可能遇到这个错误。修复：

```
git remote add st https://github.com/SillyTavern/SillyTavern
git fetch st
git checkout -t st/release
```

然后从第5步继续。

### Zip 安装

对你没有变化。照常下载分支/发布版 ZIP 即可。

---

📖 原文链接：[1.9.0 Migration Guide](https://docs.sillytavern.app/installation/updating/migration-guide-1-09/)
