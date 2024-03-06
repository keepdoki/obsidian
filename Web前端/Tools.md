## Postman
- [教程](https://www.jianshu.com/nb/4501579)

## nvm
### 1. [Download Now](https://github.com/coreybutler/nvm-windows/releases)

### 2. Usage

- `nvm arch [32|64]`: 显示node是以32位模式还是64位模式运行。指定32或64以覆盖默认体系结构。
- `nvm current`: 查看当前版本
- `nvm install <version> [arch]`: 该版本可以是特定的版本，最新版本为“ latest”，最新的 LTS 版本为“ LTS”。还可以指定是安装32位版本还是64位版本(默认为 system arch)。
- `nvm list [available]`: 列出 node.js 的安装。在结尾处键入`available`以显示可供下载的版本列表。
- `nvm on`: 启用 node.js 版本管理。
- `nvm off`: 禁用 node.js 版本管理(不会卸载任何东西)。
- `nvm proxy [url]`: 设置用于下载的代理。保留`[url]`空白以查看当前代理。将`[url]`设置为“ none”以删除代理。
- `nvm uninstall <version>`: 卸载 < version > : 卸载特定版本。
- `nvm use <version> [arch]`: 切换到指定的版本。可以选择使用`latest,`、`lts` 或`newest`。`newest`是最新安装的版本。
- `nvm root <path>`: 设置 nvm 应该存储不同版本 node.js 的目录。如果没有设置`<path>`，将显示当前根目录(C:\Users\用户名\AppData\Roaming\nvm)。
- `nvm version`: 显示 Windows 下 NVM 的当前运行版本。
- `nvm node_mirror <node_mirror_url>`: 设置node镜像，国内可以用<https://npmmirror.com/mirrors/node/>
- `nvm npm_mirror <npm_mirror_url>`: 设置npm镜像，国内可以用<https://npmmirror.com/mirrors/npm/>
> [Install NodeJS on Windows](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-windows)