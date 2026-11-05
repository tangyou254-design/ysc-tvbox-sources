# 影视仓多仓源：点播与 LIVE 分开

已整合 **20 个热门来源仓库**，并保留原有 TVboxorg 配置；去重后共 **30 个点播配置、41 份直播列表**。统计日期：2026-11-05。

## 直接导入

影视仓「多仓 / 仓库配置」填写：

```text
https://raw.githubusercontent.com/tangyou254-design/ysc-tvbox-sources/main/duocang.json
```

| 文件 | 用途 |
| --- | --- |
| [duocang.json](https://raw.githubusercontent.com/tangyou254-design/ysc-tvbox-sources/main/duocang.json) | 总入口，含点播、全部直播与按仓库分组的直播 |
| [vod.json](https://raw.githubusercontent.com/tangyou254-design/ysc-tvbox-sources/main/vod.json) | 仅点播多仓 |
| [live.json](https://raw.githubusercontent.com/tangyou254-design/ysc-tvbox-sources/main/live.json) | 全部直播 TVBox 配置，包含 lives 数组 |
| [live-repositories.json](https://raw.githubusercontent.com/tangyou254-design/ysc-tvbox-sources/main/live-repositories.json) | 按来源仓库切换的直播多仓 |
| [SOURCES.md](SOURCES.md) | 20 个仓库的 Star 排名、筛选口径和排除原因 |
| [sources.json](sources.json) | 每条地址的类型、来源、检查结果与限制 |

选择【点播】线路使用点播；选择【LIVE 直播】后进入播放器的直播页面切换列表。多仓采用 `{"urls":[{"name":"名称","url":"单仓配置地址"}]}`，不会将 M3U 直接当成点播 JSON，也不会把其他多仓 JSON 再套进总入口。

## 排名说明

GitHub 不公开全站访问量榜。本次以 Star 作为热度替代，GitHub 搜索 tvbox、iptv、影视仓，各取 Star 降序前 60 项后合并；筛选公开配置/列表或明确收录地址的相关仓库，再按 Star 降序取本轮核验可整合的 20 个来源仓库。不是全站访问量榜，也不保证穷尽所有同义词搜索结果。

部分入选仓库是源收录合集，所以“20 个仓库”不等于“20 套完全独立的上游”。镜像和 refs/heads 地址按上游路径去重，重复来源保留在 sources.json。不同列表里的相同频道未跨列表合并，便于切换备用列表。

## 已验证与使用限制

- 已实际请求配置/列表、检查 HTTP 200、解析 JSON 或识别 M3U/TXT；检查了所有生成文件与本仓库引用关系。HTTP 可读取不等于视频可播放。
- 尚未进行影视仓设备导入、第三方 spider/jar 运行、站内搜索和逐频道播放测试。上游点播配置保留原地址，因此原本自带的直播和相对路径不被改写。
- IPv6 列表需要 IPv6 网络；北京 IPTV 含本地网关地址，需要按自己的 IPTV 环境配置；SPX 山东移动列表有地区/运营商限制。
- SPX 无分组 TXT 已转换为 `live-lists/spx-shandong.m3u` 标准 M3U 快照；该快照不会自动更新。其他源直接引用上游地址，内容跟随上游变更。
- 如果当前影视仓版本不接受 `sites: []` 的纯直播配置，请在直播设置直接填写 live.json 中各 lives.url 的 M3U/TXT 地址。
- GitHub Raw 在部分网络可能无法访问；本次未安装代理、未配置定时任务。上游随时可能变更或失效。
