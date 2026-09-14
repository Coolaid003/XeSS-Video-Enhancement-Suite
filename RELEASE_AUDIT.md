# R4.3 发布封包核验

2026-09-14，Windows 11 / Intel Arc B580。

- 最终 ZIP 4,487 个内容文件逐一校验，通过；真实 `runtime_manager ensure --asset` 安装后 `status compatible=true`。
- 运行库管理、R4 升级、资产和节点包装共 35 项定向测试通过；仓库校验器通过。
- 运行库 CPU DIS 引擎与旧 R4.2 的二进制哈希不同，因此另用最终节点源码和运行库补跑三个真实入口：SR 8 帧/24fps，FG 与组合各 15 帧/48fps；音轨 AAC、完整解码及解码后 PTS 通过，进程有限退出。
- 初次后验脚本误写 ffprobe 的字段分隔符，保留失败记录；修正验证器后只读取已有成片，未重复渲染、未修改产品以迎合测试。H.264 B 帧按解码后展示时间验证，不要求文件内 packet PTS 按存储顺序递增。
- 这不是完整 ComfyUI 浏览器队列或 R4.2 CPU 输出等价测试；CPU DIS 的光流虽在 CPU，XeSS 和深度仍使用 GPU。
- 打包相对已验收候选只改发布元数据，不改测试过的 EXE/DXIL。SHA256 与下载地址固定在 `runtime_manifest.json`。

GPU Block 的完整样片、数值参照和新旧画面边界见 `docs/R4_3_LITE_V4.md`。不把旧版长稳或其他显卡成绩算进本版。
