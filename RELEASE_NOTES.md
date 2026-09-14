# ComfyUI R4.3 / Lite V4 边界修复与搜索优化 / Source 1.4.3

GPU Block 更新为已验收的 Lite V4：修复置信度共享内存边界，优化搜索寻址。三个节点名称、字段、Arc A 兼容模式、锐化/五帧融合/抗竖纹及编码器选择保持不变。

## 更新

关闭 ComfyUI，在已有节点仓库执行 `git pull --ff-only`，重启 ComfyUI 并刷新浏览器。节点会自动下载本版固定运行库并校验 SHA256；无需手动改 Python、安装 PyTorch 或覆盖 ComfyUI 根目录。已有 R4 工作流不需要换节点；R3 工作流仍需换成 R4 节点。

离线安装请下载 `xess-comfy-runtime-windows-x64-2026.09.14-r4.3.zip`，在节点目录执行 `install_runtime.bat -AssetPath "压缩包完整路径"`。不要下载 GitHub 的 Source code 当作运行库。

## 验收和速度口径

B580 三个真实节点方法的短片后端验证通过；完整 300 帧赛车 SR、621 帧人像 SR→FG 的合法 halo10 与优化版成片逐位一致。修复版不承诺与旧越界版本画面逐位相同；完整样片已由用户确认。

B580 独立 motion：1080×1920 输入 3.478→2.630 ms/帧对，2160×3840 输入 13.770→10.475 ms/帧对（约减少 24%）；不是整个视频处理速度提升 24%。GPU DIS、AMD 光流继续实验，CPU DIS/Intel 视频接口不更换算法。新版本未另做跨显卡和长稳验证。

逐文件运行库清单随源码提供，ZIP SHA256 另附。详细说明见 `docs/R4_3_LITE_V4.md`。
