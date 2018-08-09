
### 1. 下载 Anaconda 与安装 勾选添加环境变量的选项
- 验证安装是否成功 conda --version

- 添加国内镜像
`
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/ 

conda config --set show_channel_urls yes
`

### 2. 创建python虚拟环境

- conda create -n tfpy3 python=3.5

- 激活环境 activate tfpy3
- linux下激活环境 source activate tfpy3

### 3. 在虚拟环境tfpy3中安装TensorFlow

- pip install -i https://pypi.tuna.tsinghua.edu.cn/simple/ https://mirrors.tuna.tsinghua.edu.cn/tensorflow/windows/cpu/tensorflow-1.1.0-cp35-cp35m-win_amd64.whl
- deactivate
- linux下退出 source deactivate
- conda info --envs

### 4. 配置jupyter支持python的虚拟环境

- 创建目录 C:\Users\Administrator\AppData\Roaming\jupyter\kernels\tfpy3
- 在C:\Users\Administrator\AppData\Roaming\jupyter\kernels\tfpy3 目录下新建文件 kernel.json
`
{
 "language": "python",
 "display_name": "tfpy3",
 "argv": [
  "C:\\ProgramData\\Anaconda3\\envs\\tfpy3\\python.exe",
  "-m",
  "ipykernel_launcher",
  "-f",
  "{connection_file}"
 ]
}
`

- conda install -n tfpy3 ipykernel


### 5. 验证TensorFlow是否安装成功

- 在jupyter中的tfpy3环境中输入
`
import tensorflow as tf
hello = tf.constant('Hello, TensorFlow!')
sess = tf.Session()
sess.run(hello)
`
