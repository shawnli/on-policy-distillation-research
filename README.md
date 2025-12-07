# On-Policy Distillation 调研资料

本仓库收集了关于 On-Policy Distillation 的学术论文、代码实现和技术资料。

## 📚 论文

### ICLR 2024: On-Policy Distillation of Language Models
- **作者**: Rishabh Agarwal et al. (Google Brain)
- **会议**: ICLR 2024
- **方法**: Generalized Knowledge Distillation (GKD)
- **论文**: [On-Policy_Distillation_ICLR2024.pdf](./On-Policy_Distillation_ICLR2024.pdf)
- **arXiv**: https://arxiv.org/abs/2306.13649
- **引用**: 203+

### Thinking Machines Lab 博客
- **标题**: On-Policy Distillation
- **作者**: Kevin Lu et al.
- **日期**: 2025-10-27
- **链接**: https://thinkingmachines.ai/blog/on-policy-distillation/

## 💻 代码实现

### 1. Hugging Face TRL
位于 `trl/` 目录，包含以下实现：

- **GKDTrainer**: Generalized Knowledge Distillation
  - 配置: `trl/trainer/gkd_config.py`
  - 训练器: `trl/trainer/gkd_trainer.py`
  - 示例: `examples/scripts/gkd.py`
  - 文档: `docs/source/gkd_trainer.md`

- **GOLD Trainer**: General On-Policy Logit Distillation
  - 实现: `trl/experimental/gold/`
  - 文档: `docs/source/gold_trainer.md`

- **MiniLLM Trainer**: TML On-Policy Distillation 的泛化版本
  - 实现: `trl/experimental/minillm/`
  - 文档: `docs/source/minillm_trainer.md`

**仓库**: https://github.com/huggingface/trl
**Stars**: 16.6k

### 2. Thinking Machines Lab - Tinker Cookbook
位于 `tinker-cookbook/` 目录，官方实现和示例。

**仓库**: https://github.com/thinking-machines-lab/tinker-cookbook
**Stars**: 2.3k

## 🎯 核心概念

On-Policy Distillation 结合了强化学习（RL）和监督微调（SFT）的优势：

| 方法 | 采样方式 | 奖励信号 |
|------|---------|---------|
| SFT (监督微调) | Off-policy | 密集 |
| RL (强化学习) | On-policy | 稀疏 |
| On-Policy Distillation | On-policy | 密集 |

### 关键优势
1. **训练效率提升**: 相比 SFT 需要 200万 prompts，OPD 只需 77K
2. **持续学习**: 缓解灾难性遗忘问题
3. **Token 级反馈**: 在每个 token 上提供密集的监督信号

## 📖 技术细节

详见 [技术原理说明文档](./技术原理说明.md)

## 🔗 相关资源

- [Hugging Face 博客: Unlocking On-Policy Distillation](https://huggingface.co/spaces/HuggingFaceH4/on-policy-distillation)
- [OpenReview 论文讨论](https://openreview.net/forum?id=3zKtaqxLhW)
- [知乎文章解读](https://www.zhihu.com/pin/1968462515513062544)

## 📝 引用

```bibtex
@inproceedings{agarwal2024onpolicy,
  title={On-Policy Distillation of Language Models: Learning from Self-Generated Mistakes},
  author={Agarwal, Rishabh and others},
  booktitle={International Conference on Learning Representations},
  year={2024}
}
```

## 📄 许可证

- TRL: Apache-2.0 License
- Tinker Cookbook: Apache-2.0 License
