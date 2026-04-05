# QEMU 训练营基础阶段 Rust

这个仓库现在是完整的 Rustlings 题库版本，作为 QEMU 训练营基础阶段的 Rust 语言练习。

## 开始练习

1. **安装 Linux 环境**。对于 Windows 用户，推荐使用 WSL2 安装 Ubuntu 22.04，也可以使用 VMware 等虚拟机进行安装。如果在这一步存在问题，请联系助教。
2. **创建 SSH key，用于 SSH 方式克隆 GitHub 代码**。在 Linux 环境下，使用 `ssh-keygen -t rsa -b 4096 -C "你的邮箱"` 命令创建 SSH key，下面的选项全部直接回车即可。随后使用 `cat ~/.ssh/id_rsa.pub` 查看生成的公钥，并完整复制下来。在 GitHub 仓库界面点击自己的头像，选择 `Settings`，进入后点击左侧的 `SSH and GPG keys`，再点击 `New SSH key`，把复制下来的内容粘贴上去并填写描述，最后点击 `Add SSH key` 完成添加。
3. **本地安装 Rust**。进入 Linux 环境后，参考 ArceOS 教程 [Rust 开发环境配置 - ArceOS Tutorial Book (rcore-os.cn)](https://rcore-os.cn/arceos-tutorial-book/ch01-02.html) 中的 Rust 开发环境配置章节完成安装，也可以顺手把后续实验需要的环境一并配置好。
4. **加入 GitHub Classroom**。点击实验邀请链接，加入 GitHub Classroom，拿到你自己的专属仓库链接。
5. **clone 实验仓库到本地**。回到本地 Linux 环境下，使用你在 GitHub Classroom 中拿到的专属仓库链接进行 clone。若使用 SSH 方式，可执行 `git clone git@github.com:gevico/********.git`。随后使用 `ls` 查看 clone 下来的文件夹，再使用 `cd` 进入该仓库根目录，执行 `cargo install --force --path . --locked` 安装 rustlings。
6. **练习 rustlings**。使用 VS Code 等编辑器打开 clone 下来的仓库根目录，并在仓库根目录执行 `rustlings watch` 查看完成情况并依次完成练习。练习源码位于 `exercises` 文件夹中。你也可以执行 `rustlings run 练习名称` 运行指定练习，执行 `rustlings hint 练习名称` 查看提示，执行 `rustlings list` 查看全部练习和当前状态。
7. **提交完成情况**。当做完部分或所有练习之后，在仓库根目录执行 `git add .`、`git commit -m "update"`、`git push`，把更新提交到 GitHub Classroom 的 CI 进行自动评测。你可以在 GitHub 仓库页面的 Actions 页面查看 CI 结果，或者在 [OpenCamp 排行榜](https://opencamp.cn/gevico/camp/2026/stage/5?tab=rank) 查看自己的评分。

## 目录说明

### `exercises`

保留完整 Rustlings 练习题和章节说明，继续作为基础阶段 Rust 语言练习使用。

### `src`

Rustlings 命令行工具本体，用来执行 `watch`、`run`、`hint`、`verify` 等练习流程。

### `tests`

Rustlings 的集成测试与评测 fixture，用来验证题库、命令行为和评分流程。

## 自动评测

当前 GitHub Actions 默认会：

1. 编译并运行 Rustlings 评测
2. 汇总题目完成情况
3. 在 `push main/master` 时把成绩回传到 OpenCamp
4. 在 `pull_request` 场景下只做评测，不回传 OpenCamp

工作流文件在 `.github/workflows/rust.yml`。

## 常用命令

```bash
cargo install --force --path . --locked   # 使用锁定依赖安装 rustlings，避免依赖版本漂移导致安装失败
rustlings watch                           # 进入自动监听模式，按顺序检查并提示当前需要完成的练习
rustlings run 练习名称                    # 单独编译并运行某一道练习，查看当前练习的执行或报错结果
rustlings hint 练习名称                   # 查看指定练习的提示信息
rustlings list                            # 列出全部练习及当前完成状态
cargo test --test cicv --verbose          # 运行仓库评测相关测试，检查题库与评测流程是否正常
```

## 说明

- 本仓库基于 rustlings 5.5.1 的完整题库整理而成。
- 评分以 GitHub Actions 结果为准。
- OpenCamp 回传用户名使用触发 workflow 的 GitHub 用户名。
