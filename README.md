# Stable Diffusion Environment
This repo is my setup for running Stable Diffusion locally.

Based on the tutorial provided by Huggingface.
https://huggingface.co/blog/diffusers-coreml

## Prereqs
- You need an account on [Hugging Face](https://huggingface.co/).

## Setup
1. Install Python and PIP. FYI, this takes a while.
```shell
make nix
```

2. Setup poetry.
```shell
make setup
```

3. Use poetry to install the project dependencies.
```shell
source .venv/bin/activate
make init
```

4. Download the Vision Models from Hugging Face. FYI, this takes a while.
```shell
make get_models
```

5. Sign into Hugging Face and get a secret token.
```shell
# Get the token from huggingface.co/settings/tokens after you've already logged in.

source .venv/bin/activate
poetry run huggingface-cli login

# The above command will prompt for the token. Copy/Paste.
```

6. Make some images. The first time this downloads a bunch of stuff from Pytorch
   and takes quite a while.
```shell
python -m python_coreml_stable_diffusion.pipeline \
  --prompt "a photo of an astronaut riding a horse on mars" \
  -i ./models/coreml-stable-diffusion-v1-4_original_packages/original/packages \
  -o ./images --compute-unit ALL --seed 93
```