
# Readme.md

**目录**


运行方法
=============
本项目所运行的基本环境为主机windows 10 64位版本，树莓派要求内核版本为armv7l
主机配置
-------------
安装驴车官方包
`git clone https://github.com/autorope/donkeycar`
`cd donkeycar`
`git checkout master`
`pip3 install -e .[pc]`
进入项目根目录，执行以下代码创建虚拟环境
`conda env create -f ./requests/windows/donkey_env.yaml`
## 树莓派配置
使用ssh工具进入树莓派，首先安装python依赖项。
`sudo apt-get install build-essential python3 python3-dev python3-pip python3-virtualenv python3-numpy python3-picamera python3-pandas python3-rpi.gpio i2c-tools avahi-utils joystick libopenjp2-7-dev libtiff5-dev gfortran libatlas-base-dev libopenblas-dev libhdf5-serial-dev libgeos-dev git ntp`
安装opencv依赖项
`sudo apt-get install libilmbase-dev libopenexr-dev libgstreamer1.0-dev libjasper-dev libwebp-dev libatlas-base-dev libavcodec-dev libavformat-dev libswscale-dev libqtgui4 libqt4-test`
创建虚拟环境并设置为开机启动，进入虚拟环境
`python3 -m virtualenv -p python3 env --system-site-packages`
`echo "source env/bin/activate" >> ~/.bashrc`
`source ~/.bashrc`
使用pip安装所需包
`pip install ./requests/raspi/donkey_env.txt`
创建工作目录
`mkdir projects`
`cd projects`
安装驴车官方包
`git clone https://github.com/autorope/donkeycar`
`cd donkeycar`
`git checkout master`
安装2.5.0版本tenorflow，与PC端适配
`./requests/raspi/tensorflow-2.5.0-cp37-none-linux_armv7l_download.sh`
`pip install tensorflow-2.5.0-cp37-none-linux_armv7l.whl`
##自动驾驶
使用ssh连接至小车，进入mycar目录，执行语句使小车使用模型运行
`python manage.py drive --model ./models/mymodel.h5`
#项目结构
##requests
储存小车运行与主机训练所需的环境的相关参数
##mycar
储存小车数据，包含训练模型、引脚配置、行驶逻辑各模块
##resource
储存在训练过程中所使用到的数据
##video
储存训练过程中的记录影像资料
#成员分工
本项目软硬件结合，故分工为两个小组，分别专攻软件部分与硬件部分。
硬件部分：杨鹏飞、李尚东
软件部分：荆浩宇、杭成宇、于汇洋
#个人贡献
杭成宇：总体进度安排与管理，文档编写，打印小车底板，辅助训练模型、删除脏数据
荆浩宇：主机与树莓派环境与驴车安装调试，修改行驶逻辑，训练模型
于汇洋：操控小车收集数据，包含有正常驾驶数据与处理特殊情况数据
杨鹏飞&李尚东：打印并组装小车，固定各模块，连接电路，操控小车行驶

### End