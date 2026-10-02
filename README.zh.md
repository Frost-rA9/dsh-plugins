# DSH 插件索引

[DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)（dsh）Web UI
的插件索引。每个插件都有自己的独立仓库，本仓库只保存索引。

English: [README.md](README.md)

## 插件列表

| 插件 | 功能 | 仓库 |
| --- | --- | --- |
| **Everforest** | 为整个界面提供完整的六套 Everforest 配色（hard / medium / soft × 深色 / 浅色），并在「设置 → 通用」提供深度选择 | [dsh-theme-everforest](https://github.com/Frost-rA9/dsh-theme-everforest) |

## 安装插件

1. 把插件仓库克隆到一个固定位置 —— profile 会链接到该路径，之后移动目录会导致链接失效：

   ```sh
   git clone https://github.com/Frost-rA9/dsh-theme-everforest
   ```

2. 在 Harness 会话中安装到当前 profile：

   ```
   plugin_manager install_bundle
     target: /absolute/path/to/dsh-theme-everforest
   ```

   `target` 必须是克隆目录的绝对路径。

3. 也可以在 Web UI 的「Plugin Manager」页面中指向同一目录完成安装。

`install_bundle` 会负责依赖安装与 bundle 选择，profile 最终指向你的本地检出；
之后在插件目录里 `git pull` 即可更新。每个插件自己的 README 说明了它的依赖与验证方式。

## 如何把插件加入索引

收录到这里的插件应满足：

- 独立仓库，命名为 `dsh-<kind>-<name>`（例如 `dsh-theme-everforest`）；
- 是可安装的 bundle：`package.json` 中声明 `dsh.bundle.patch`，用
  `cordis.patch.yml` 插入自己的 Loader 行；UI 插件还需声明 `dsh.client` 并导出 `./client`；
- 提供展示元数据，让 Plugin Manager 卡片可读：`locale/en.json` 与 `locale/zh.json`
  中的 `meta.title` / `meta.description`，以及 `icon.svg`；
- 只声明真正需要的依赖，不包含安装脚本；
- 在 `README.md` 中说明自身（中文可另建 `README.zh.md`）；
- 提交历史遵循[约定式提交](https://www.conventionalcommits.org/zh-hans/v1.0.0/)。

新增插件时，在上方表格加一行并提交 Pull Request 即可。

## 仓库结构

本索引只跟踪自己的文件：各插件的本地检出是独立的 git 仓库，已由 `.gitignore` 排除。

## 许可

索引内容采用 MIT 许可；各插件自带其许可证。
