# HandGesture

## Dependencies
1.Ubuntu 18.04

2.protbuf 3.8.0

3.Python 3.6
### Step-by-step Tutorial

setting up the environment on **Jetson Nano**, compile the PyTorch model with TVM, and perform instances from camera streaming.

**run**:(may take a while...)
```
bash ./install_protobuf-3.8.0.sh
```

**install OpenCV**:
```
python3 -m pip install numpy
python3 -m pip install opencv-python

```
You also need add cv2 package to path import search path.
```
export PYTHONPATH=/usr/local/python
```

**install pytorch & torchvision**:
```
python3 -m pip install torch==1.2.0 & torchvision==0.4.0
```
Build **TVM** with following commands
```
sudo apt install llvm # install llvm which is required by tvm
git clone -b v0.6 https://github.com/apache/incubator-tvm.git
cd incubator-tvm
git submodule update --init
mkdir build
cp cmake/config.cmake build/
cd build
#[
#edit config.cmake to change
# 32 line: USE_CUDA OFF -> USE_CUDA ON
#104 line: USE_LLVM OFF -> USE_LLVM ON
#]
cmake ..
make -j4
cd ..
cd python; sudo python3 setup.py install; cd ..
cd topi/python; sudo python3 setup.py install; cd ../..
```



**install onnx**:
```
python3 -m pip install onnx==1.5.0
```
export cuda toolkit binary to path:
```
export PATH=$PATH:/usr/local/cuda/bin
```
**run**:
```
python3 main.py
```
