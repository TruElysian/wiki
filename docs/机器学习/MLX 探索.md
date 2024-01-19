---
title: MLX 探索
date: 2024-01-04
update: 2024-01-04
tags: MLX LLM macOS
---

# MLX 探索

```sh
conda create --name mlx

conda activate mlx
```

## Phi-2

---

来源 [mlx-community/phi-2](https://huggingface.co/mlx-community/phi-2)

```sh
pip install mlx
pip install transformers huggingface_hub hf_transfer
git clone https://github.com/ml-explore/mlx-examples.git
cd mlx-examples

# Download model
export HF_HUB_ENABLE_HF_TRANSFER=1 # 如果后续下载报错则执行 export HF_HUB_ENABLE_HF_TRANSFER=0
huggingface-cli download --local-dir-use-symlinks False --local-dir llms/phi2 mlx-community/phi-2

cd llms/phi2

pip install -r requirements.txt

python3 convert.py

python3 phi2.py --prompt "My name is"

# Run example
# python3 llms/phi2/phi2.py --prompt "My name is"
```

## Source Link

---

- [MLX Community](https://huggingface.co/mlx-community)
- [apple/ml-stable-diffusion](https://github.com/apple/ml-stable-diffusion)
