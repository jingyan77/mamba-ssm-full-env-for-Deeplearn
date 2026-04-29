# mamba-ssm-full-env-for-Deeplearn
一键mamba深度学习环境安装包于win系统(One-click Environment Installation Package.If your computer is Windows, you can try this.)

"""
"""
本一键包用于windows系统上安装Linux的mamba环境，无需在Linux中格外配置环境。
适用于RTX50系，cu130

安装包自带通用深度学习库scipy，pandas等等
和最重要要的mamba_ssm与cuasal-conv1d
"""
"""

首先你得先安装好Linux子系统，你可以在microsoft商店中下载ubuntu。
然后在下载ubuntu在里面安装miniconda。
确保你的ubuntu中有 /home/username/miniconda3


以下为在ubuntu里面安装miniconda，已安装确保你的ubuntu中有 /home/username/miniconda3，即可跳过。
------------------miniconda_setup--------------------
在下载ubuntu在里面安装miniconda
以下操作在ubuntu终端窗口执行：
wget https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda3-latest-Linux-x86_64.sh -O Miniconda3.sh
bash Miniconda3.sh

装完后搞镜像：
nano ~/.condarc

把下面这段内容复制进去
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud

按 Ctrl+O 保存，按 Enter 确认文件名，再按 Ctrl+X 退出编辑器

清理旧缓存，让新源生效
conda clean -i

------------------miniconda_setup_end--------------------


-----START------
以下操作在ubuntu终端窗口执行：
创建目标目录：
mkdir -p ~/miniconda3/envs/mamba-ssm

mamba_env.tar.gz压缩包复制到/home/~的目录下，
之后再解压命令如下：
tar -xzf ~/mamba_env.tar.gz -C ~/miniconda3/envs/mamba-ssm

激活环境并执行修复：
conda activate mamba-ssm
conda-unpack

执行完以上步骤后，用以下命令验证环境是否迁移成功：
# 验证python路径是否正确指向当前环境
which python
# 验证mamba相关库是否能正常导入
python -c "import mamba_ssm; import causal_conv1d; print('库导入成功，环境迁移完成')"

环境安装完成，可以试试再pycharm上导入wsl的mamba-ssm环境。
-----END------
