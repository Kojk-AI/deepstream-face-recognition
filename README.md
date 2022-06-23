# deepstream-face-recognition
Sample face-recognition app using Deepstream 6.0.1 with FaceNet on Jetson Nano (L4T Jetpack 4.6.1)

<div id="top"></div>

<!-- ABOUT THE PROJECT -->
## About The Project

This project is a sample face-recognition app deployed on Jetson Nano with the following features:

1. Application is self-contained in a Docker container installed with Deepstream SDK (6.0.1) and its python bindings
2. Video input is taken from device, e.g. /dev/video0 which can be a MSI camera or USB camera etc.
3. Video output is a RTSP stream, which means that the Jetson Nano can be ran headless
4. Detected objects are "person" and "face"
5. Detected objects are tracked
6. Face-recognition is done on the detected face, once per tracked face-id every X frames (to be set in the config file; 30 frames is the default)

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

### Running the sample app in a Docker container

The pre-built Docker container can be pulled from


### Prerequisites

### Installation

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage



<p align="right">(<a href="#top">back to top</a>)</p>


<!-- LICENSE -->
## License



<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
## Contact


<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* []()
* []()
* []()

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
