# WSVADBench

VADBench 是面向弱监督视频异常检测（WSVAD）的可插拔研究框架，用于统一视频身份、采样、编码器特征、缓存策略、训练、推理和评估。

## 框架范围

- 登记了 25 个视频编码器研究候选；运行 catalog 中包含 21 个条目，并区分 planned、integrated 与 blocked。登记不代表每个模型都已完成真实权重验证。
- 支持固定 clip 编码路径与长视频/流式状态路径，并区分视觉 token、visual memory 和 decoder KV cache 的语义。
- 提供 UCF-Crime 弱监督基线配置、数据审计、特征提取、MIL 训练、预测和帧级评估工具。
- 当前完整 UCF-Crime 数据未随仓库发布；本仓库不包含视频、模型权重或实验产物，也不声称已完成全量基准实验。

## 安装与测试

需要 Python 3.10–3.12：

```bash
uv sync --extra dev --extra train --extra video
uv run python -m pytest
```

真实编码器还需按照对应上游项目的许可证和固定 revision 准备独立环境与权重。数据、权重和生成的运行产物不属于本仓库。

GitHub Actions 的 `Core CPU tests` 在 Ubuntu / Python 3.11 上检查配置、注册器、特征与
缓存契约、采样、manifest、时间标注、UCF-Crime 标注解析、特征存储、指标和 CLI 延迟导入。
它在 PR、`main` 更新和手动触发时运行，只使用合成输入及仓库中的文本标注，无需 GPU、
视频、预训练权重或 train/video extras。依赖固定在 `.github/requirements-ci.txt`，完整
测试列表在 `.github/workflows/ci.yml`；真实编码器与训练验证继续单独执行。

## 许可

本仓库自有代码采用 MIT License。上游代码、模型权重和数据仍遵循各自许可证。
服务器辅助脚本和环境注册表中的集群路径是示例值；部署前请替换为自己的路径。

仓库包含 UCF-Crime 官方划分与时间标注 TXT 清单（带来源和 SHA-256 登记）；不包含视频本体。
