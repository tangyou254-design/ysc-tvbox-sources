# 影视仓多仓配置

点播与 LIVE 直播分别管理。整理日期：2026-11-05（北京时间）。

## 导入地址

- 全部入口（影视仓多仓配置）：https://raw.githubusercontent.com/tangyou254-design/ysc-tvbox-sources/main/duocang.json
- 仅点播多仓：https://raw.githubusercontent.com/tangyou254-design/ysc-tvbox-sources/main/vod.json
- 直播配置（TVBox 配置，含 lives）：https://raw.githubusercontent.com/tangyou254-design/ysc-tvbox-sources/main/live.json

在影视仓的多仓/仓库配置地址中填入 duocang.json。选择带【点播】前缀的线路观看点播；选择【LIVE 直播】后进入软件的直播页面切换直播列表。不同版本菜单名称和纯直播配置支持情况可能不同；若版本不接受 sites 为空的配置，请在直播设置中直接填写下面的 M3U/TXT 地址。

## 点播来源

| 名称 | GitHub 项目 | 配置 |
| --- | --- | --- |
| Qist 大而全 | https://github.com/qist/tvbox | https://raw.githubusercontent.com/qist/tvbox/master/0821.json |
| Qist 饭太硬配置 | https://github.com/qist/tvbox | https://raw.githubusercontent.com/qist/tvbox/master/0826.json |
| TVboxorg 聚合 | https://github.com/TVboxorg/TVbox | https://raw.githubusercontent.com/TVboxorg/TVbox/main/dist/official.json |

点播入口直接引用上游完整配置，保留其 spider、jar 和相对路径解析关系；上游可能自带直播。本项目按入口用途区分点播与直播，并未删除或复制改写上游内容。两条 Qist 配置有部分重叠。

## LIVE 直播来源

| 列表 | 地址 |
| --- | --- |
| IPTV-org 中国 | https://iptv-org.github.io/iptv/countries/cn.m3u |
| IPTV-org 中文 | https://iptv-org.github.io/iptv/languages/zho.m3u |
| Qist 初秋语 IPv4 | https://raw.githubusercontent.com/qist/tvbox/master/list.txt |

IPTV-org 项目：https://github.com/iptv-org/iptv 。中国与中文列表频道可能重叠。

## 格式与验证范围

- duocang.json / vod.json 使用标准 urls 数组，每项只包含 name 和 url。参考：https://github.com/TVboxorg/TVbox/blob/main/dist/tvbox.json 。
- live.json 使用独立 lives 数组，M3U/TXT 不会直接放进多仓 urls 当作点播配置。
- 已通过 GitHub API 读取并解析三份点播 JSON（86 / 54 / 160 个 sites），读取 Qist 直播 TXT，并核对 IPTV-org 官方 PLAYLISTS.md 中的中国与中文地址。
- 已校验本仓库 JSON 结构。未进行影视仓设备导入和逐频道播放测试；配置可读取不等于视频可播放。
- GitHub Raw 在部分网络可能无法直连。上游内容、可用性和播放限制会变化；本项目未设置自动检测或定时更新任务，直接引用的上游 URL 会跟随上游变化。
