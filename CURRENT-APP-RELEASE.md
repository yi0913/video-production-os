# 视频制作 OS v1.3.4-current.1 · 现用版同步

这是 yi0913 发布的个人仓库版本，以当前正在使用的 Mac 软件为基准。原作者为 [SJT-bright](https://github.com/SJT-bright/video-production-os)，本版不是原作者的官方新版本。

## 本次发布内容

- 将现用 v1.3.4 对应源码固定为可下载、可复现的发布版本，版本号为 `1.3.4-current.1`。
- 对照现用软件包，119 个可比源码文件与上游提交 `725e265af5d062e3fd933fadc24cb70d7dfb59c7` 完全一致。核对后仅更新版本元数据与发布文档，功能代码保持原样。
- 包含该源码已有的正文分集、按集下载、异步资产扫描、提示词状态保存等功能；具体范围见原有 v1.3.4 更新说明。
- 没有加入此前撤回的网页性能候选补丁，也没有重新引入早期网页登录兼容补丁。此次不宣称新增或独立验证了 GPT、核绘等网站整体卡顿的修复。

## 下载

[进入本版下载页](https://github.com/yi0913/video-production-os/releases/tag/v1.3.4-current.1)。

- `VideoProductionOS-Mac-v1.3.4-current.1-AppleSilicon.zip`：Apple Silicon Mac 安装包。
- GitHub 自动生成的 Source code ZIP/TAR：本版完整项目源码。
- `installed-source-provenance.json`：现用软件源码的相对路径、SHA-256 与上游基线，不包含本机目录或个人数据。
- `SHA256SUMS.txt`：安装包及附带组件源码的校验值。

安装包采用本地 ad-hoc 签名，未经过 Apple 公证。本次没有构建 Intel 或 Windows 安装包。

## 数据与安装

发布包不含用户项目、素材、剧本、数据库、Cookie 或网页登录信息。发布过程不会替换本机已安装的软件。

需要安装时先退出正在运行的软件，仅替换 App。个人数据仍按原公开版保存在用户配置目录；不要删除该目录。源码开发版本与公开下载版的数据位置不同，安装包不自动迁移开发目录。

## 构建

使用本仓库对应标签、Node.js >= 22.12.0 及锁文件依赖。先按 `scripts/build-ffmpeg.sh` 准备 LGPL 音频组件，再运行：

```sh
npm ci
VIDEO_OS_FFMPEG_BUILD_ROOT=/path/to/lgpl-media-tools npm run build:mac -- --portable --arch arm64
```

音频组件来源、许可与源码见 `THIRD-PARTY-NOTICES.md`。发布时附带对应的 FFmpeg 6.1.1 完整源码。
