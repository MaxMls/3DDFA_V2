
install python 3.8

run:
```
pip3 install torch torchvision matplotlib numpy opencv-python imageio imageio-ffmpeg pyyaml tqdm argparse cython scikit-image scipy onnxruntime
```
fix problems
[first](https://github.com/cleardusk/3DDFA_V2/issues/12#issuecomment-697479173),
[second](https://github.com/cleardusk/3DDFA_V2/issues/12#issuecomment-730822625)

run:
```
cd FaceBoxes/utils
python build.py build_ext --inplace
cd ../..

cd Sim3DR
python setup.py build_ext --inplace
cd ..
```
install last version gcc.
[link](http://www.equation.com/servlet/equation.cmd?fa=fortran)

run:
```
cd utils/asset
gcc -shared -Wall -O3 render.c -o render.so -fPIC
cd ../..
```


running: 
```
# 1. running on still image, the options include: 2d_sparse, 2d_dense, 3d, depth, pncc, pose, uv_tex, ply, obj
python demo.py -f examples/inputs/emma.jpg --onnx # -o [2d_sparse, 2d_dense, 3d, depth, pncc, pose, uv_tex, ply, obj]

# 2. running on videos
python demo_video.py -f examples/inputs/videos/214.avi --onnx

# 3. running on videos smoothly by looking ahead by `n_next` frames
python demo_video_smooth.py -f examples/inputs/videos/214.avi --onnx

# 4. running on webcam
python demo_webcam_smooth.py --onnx
```