## Disclaimer

I'm on AMD with 16gb of VRAM. This drastically changes what tools I can use.
### Installation (Auto 1111)

```shell
# https://github.com/lshqqytiger/stable-diffusion-webui-amdgpu

sudo pacman -Syyu
sudo pacman -S python-pip
sudo pacman -S python-pytorch-rocm

yay -S python311 # do not confuse with python3.11 package # currently 3.10 3.11 are supported

# Only for 3.11
# Then set up env variable in launch script
export python_cmd="python3.11"
# or in webui-user.sh
python_cmd="python3.11"

wget -q https://raw.githubusercontent.com/lshqqytiger/stable-diffusion-webui-amdgpu/master/webui.sh

## Or clone: git clone https://github.com/lshqqytiger/stable-diffusion-webui-amdgpu

./webui.sh --skip-torch-cuda-test --precision full --no-half
```