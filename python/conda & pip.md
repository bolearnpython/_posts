---
title: conda & pip
tags: 环境搭建,pip,conda,改源
---
# conda & pip
## 简单的使用
    执行python -m venv myenv1即可创建虚拟环境myenv1
    *nix系统下，使用命令pyvenv。
    Windows下命令行myenv1\Scripts\activate.bat进入环境，
    使用deactivate退出虚拟环境。
## 管理软件
    # 将anaconda的bin目录加入PATH，根据版本不同，也可能是~/anaconda3/bin
    echo 'export PATH="~/anaconda2/bin:$PATH"' >> ~/.bashrc
    # 更新bashrc以立即生效
    source ~/.bashrc
    # 创建一个名为python34的环境，指定Python版本是3.4（不用管是3.4.x，conda会为我们自动寻找3.4.x中的最新版本）
    conda create --name python34 python=3.4
    # conda create -n bunnies python=3 Astroid Babel
    # conda info -envis
    # 安装好后，使用activate激活某个环境
    activate python34 # for Windows
    source activate python34 # for Linux & Mac
    # 激活后，会发现terminal输入的地方多了python34的字样，实际上，此时系统做的事情就是把默认2.7环境从PATH中去除，再把3.4对应的命令加入PATH
    # 此时，再次输入
    python --version
    # 可以得到`Python 3.4.5 :: Anaconda 4.1.1 (64-bit)`，即系统已经切换到了3.4的环境
    # 如果想返回默认的python 2.7环境，运行
    deactivate python34 # for Windows
    source deactivate python34 # for Linux & Mac
    # 删除一个已有的环境
    conda remove --name python34 --all
    # 通过克隆来复制一个环境。这儿将通过克隆snowfllakes来创建一个称为flowers的副本。
    conda create -n flowers --clone snowflakes


    # 安装scipy
    conda install scipy
    # conda会从从远程搜索scipy的相关信息和依赖项目，对于python 3.4，conda会同时安装numpy和mkl（运算加速的库）
    # 查看当前环境下已安装的包
    conda list
    # 查看某个指定环境的已安装包
    conda list -n python34
    # 查找package信息
    conda search numpy
    # 安装package
    conda install -n python34 numpy
    # 如果不用-n指定环境名称，则被安装在当前活跃环境
    # 也可以通过-c指定通过某个channel安装
    # 更新package
    conda update -n python34 numpy
    # 删除package
    conda remove -n python34 numpy


    # 更新conda，保持conda最新
    conda update conda
    # 更新anaconda
    conda update anaconda
    # 更新python
    conda update python
    # 假设当前环境是python 3.4, conda会将python升级为3.4.x系列的当前最新版本

    # 在当前环境下安装anaconda包集合
    conda install anaconda
    # 结合创建环境的命令，以上操作可以合并为
    conda create -n python34 python=3.4 anaconda
    # 也可以不用全部安装，根据需求安装自己需要的package即可


    # 添加Anaconda的TUNA镜像
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
    # 设置搜索时显示通道地址
    conda config --set show_channel_urls yes

## 改源
### linux
    linux下运行命令
    vi ~/.pip/pip.conf
    然后写入如下内容并保存
    [global]
    trusted-host =  mirrors.aliyun.com
    index-url = http://mirrors.aliyun.com/pypi/simple
### Windows
    import os
    ini = "[global]\nindex-url = https://pypi.doubanio.com/simple/\n"
    pippath = os.environ["USERPROFILE"]+"\\pip\\"
    exec("if not os.path.exists(pippath):\n\tos.mkdir(pippath)")
    open(pippath+"/pip.ini", "w+").write(ini)
## pip
    pip install SomePackage＃最新版本
    pip install SomePackage == 1.0.4＃具体版本
    pip install'SomePackage> = 1.0.4'＃最小版本
    pip install --upgrade SomePackage
    pip download SomePackage
    show list search uninstall
    # 导出当前已经安装包
    pip freeze > requirements.txt
    pip install -r requirements.txt