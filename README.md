# Xformers Builds

Builds of facebookresearch/xformers for windows for use with idea2art-aio

Don't expect any code here. Look in the project releases for the binaries.

To reproduce builds:
  - Install Visual Studio Build Tools 2019, selecting the option "Desktop Development for C++"
  - Install CUDA toolkit 11.6 Update 2
  - Install Idea2art.aio and run install_or_update.exe
  - Rename `link.exe` inside idea2art-aio-0.0.6/env/envs/sd-grpc-server/Library/usr/bin to something else (`link.exe_` maybe)
  - Within a "Developer Command Prompt for Visual Studio 2019":
    - Change to the idea2art-aio install directory
    - Run `env\micromamba.exe run -r env -n sd-grpc-server cmd`
  - `git clone https://github.com/facebookresearch/xformers.git`
  - Use git to checkout whatever version of xformers you want to build
  - `git submodule update --init --recursive`
  - `pip install -r requirements.txt`
  - `set TORCH_CUDA_ARCH_LIST=6.0;7.0;7.5;8.0;8.6`
  - `set DISTUTILS_USE_SDK=1`
  - (Optional) `set MAX_JOBS={some number}`
  - `python setup.py build`
  - `python setup.py bdist_wheel`
