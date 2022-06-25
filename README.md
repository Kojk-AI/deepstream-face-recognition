# deepstream-face-recognition

<div id="top"></div>

<!-- ABOUT THE PROJECT -->
## About The Project

This project is a sample face-recognition app deployed on Jetson Nano with the following features:

1. Application is self-contained in a Docker container installed with Deepstream SDK (6.0.1) and its python bindings
2. Video input is taken from device, e.g. /dev/video0 which can be a MSI camera or USB camera etc.
3. Video output is a RTSP stream, which means that the Jetson Nano can be ran headless
4. Detected objects are "person" and "face"
5. Detected objects are tracked
6. Face-recognition is done on the detected faces, once per tracked face-id every X frames (to be set in the config file; 30 frames is the default)

It also features the following Deepstream python functions:

1. Output video as a RTSP stream
2. Multi-model inference
3. Deploying a custom model
4. Custom parser of the model's output using a probe function

Models used:

1. PeopleNet from Tao Toolkit for person and face detection: https://catalog.ngc.nvidia.com/orgs/nvidia/teams/tao/models/peoplenet
2. FaceNet for face recognition based on: https://github.com/nyoki-mtl/keras-facenet

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

There are 2 different ways to run the sample app:

1. Docker container
2. Install Deepstream SDK and its python bindings on machine

<br/>

### Running the sample app in a Docker container

The pre-built Docker container can be pulled 

```
docker pull kojkai/deepstream-jetson-nano:facenet
```

And ran

```
sudo docker run --runtime nvidia -it --rm --network host \
    -v /tmp/.X11-unix/:/tmp/.X11-unix \
    -v /tmp/argus_socket:/tmp/argus_socket \
    --device /dev/video0 \
    kojkai/deepstream-jetson-nano:facenet
```

  While it can be ran out of the box, the faces that are stored in the docker container are mine. 
  To adopt the docker image to your own use, you will need to first create a "database" of facial features using the notebook modify_keras_FaceNet.ipynb. The "database" will be in the form of a .npz file. 
  You will also need a list of "names" (real names or id), which corresponds to the saved facial features. Each line in the file will correspond to a single name.
  Replace both the files; embeddings.npz and names.txt, in /app/models with your own files

<br/>

### Install Deepstream SDK and its python bindings on machine

Deepstream installation
```
https://docs.nvidia.com/metropolis/deepstream/6.0.1/dev-guide/text/DS_Quickstart.html
```

Deepstream python bindings installation
```
https://github.com/NVIDIA-AI-IOT/deepstream_python_apps/tree/master/bindings
```

(As of writing)
Do take note that Jetpack 5 is not released for Jetson nano; Jetson nano will be running Jetpack 4.6.1, which does not supports Deepstream 6.1. Therefore, please take note when referring documents and discussions found online.

Models can be found at:

PeopleNet https://catalog.ngc.nvidia.com/orgs/nvidia/teams/tao/models/peoplenet

FaceNet Weights can be found https://github.com/nyoki-mtl/keras-facenet

Convert the FaceNet weights into a saved_model using the notebook modify_keras_FaceNet.ipynb and convert it into onnx format following https://github.com/onnx/tensorflow-onnx. Make sure the .onnx file follows the name in the config file. Place the models in the models folder. Do note that during the 1st run of the script, the tensorrt engine file will be generated, taking more time to load. However, once the engine file is generated and reflected in the config file, subsequent runs will load the engine files directly.

After which, you will need to first create a "database" of facial features using the notebook modify_keras_FaceNet.ipynb. The "database" will be in the form of a .npz file. You will also need a list of "names" (real names or id), which corresponds to the saved facial features. Each line in the file will correspond to a single name. Place both the files; embeddings.npz and names.txt, in /app/models together with the models.

<!-- USAGE EXAMPLES -->
## Demo

https://user-images.githubusercontent.com/107860554/175756912-11d471b3-d6c7-4880-805f-651735b122db.mp4

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- Troubleshooting -->
## Troubleshooting

- VLC player crashes/freezes while playing the stream

    I had problems with VLC player, but the default video app in Ubuntu works fine

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- LICENSE -->
## License

This software contains source code provided by NVIDIA Corporation and uses third-party packages that may be distributed under
different licensing terms.


<p align="right">(<a href="#top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

- https://docs.nvidia.com/metropolis/deepstream/dev-guide/text/DS_docker_containers.html#creating-custom-deepstream-docker-for-jetson-using-deepstreamsdk-package
- https://catalog.ngc.nvidia.com/orgs/nvidia/containers/l4t-tensorrt/tags
- https://catalog.ngc.nvidia.com/orgs/nvidia/teams/tao/models/peoplenet
- https://github.com/nyoki-mtl/keras-facenet

<p align="right">(<a href="#top">back to top</a>)</p>
