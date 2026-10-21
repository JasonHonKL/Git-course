# Git 内部结构 · 自上而下读 git/git

一门中文互动课程：从 `git commit` 之后 `.git` 里多了什么开始，逐层打开对象库、索引、引用与打包。

**在线课程**：https://jasonhonkl.github.io/Git-course/

## 这个仓库是什么

这里只托管课程的**静态站点**（`docs/`）：

- 12 个教学小节，6 个模块
- 24 张 Mermaid 图，36 道选择题，12 道简答
- 3 个视频：主片 86 秒 + 两个模块短片
- 6 个实验卡（5 个核心 + 1 个可选）

GitHub Pages 不能运行服务端检查，所以页面上的「检查我的实验」在 `github.io` 上会提示你回到本地运行。阅读、视频、选择题、简答和本地保存都正常。

## 课程内容

| 模块 | 主题 | 实验 |
|---|---|---|
| 1 | 整台机器：一次 commit 留下了什么 | Lab 0 `lab-gitdir` 手搭 `.git` |
| 2 | 跟着 add / commit 走 | Lab 1 `lab-plumbing` 手工造 commit |
| 3 | 对象库：哈希、松散对象、pack | Lab 2 `lab-object-meta` 加一个 builtin |
| 4 | 索引：DIRC、stat 缓存、racy clean | Lab 4 `lab-index` 解析 index 二进制 |
| 5 | 引用与可达性：reflog、gc | Lab 3 `lab-recover` 找回丢失提交 |
| 6 | 打包与传输（扩展） | Lab 6 `lab-pack` 读 pack / idx（可选） |

源码对照：`git/git` v2.56，提交 `47fdf22`。

## 本地运行完整课程

静态仓库不包含检查器、测试用例与 `git-src`。要跑实验，请在完整的本地课程目录里：

```sh
node course/serve.mjs          # http://127.0.0.1:4173
node course/lab.mjs start all
node course/check.mjs lab-gitdir
node course/check.mjs lab-index
```

`node course/check.mjs --self-test` 会验证六个实验的检查器。

## 发布

`docs/` 由本地课程目录的以下命令生成：

```sh
sh course/publish.sh
```

它会重建 `index.html`，只同步公开的站点文件（不包含 `tests/`、`work/`、源码和检查器），然后提交到本仓库。

## License

课程文字与站点：MIT。引用的 Git 源码片段版权归 Git 项目（GPL-2.0）。
