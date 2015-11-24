# docker-build-nodejs
A dockerized app ready for use with Shippable's Docker Build Support

How to build this sample
------------------------

There are 2 ways to set up Docker build with Shippable - pre CI or post CI. 
Pre CI workflow is:  
* Build the image using Dockerfile at the root of your repo
* Pull code from GitHub/Bitbucket and test code in the container
* Push container to docker hub

Post CI workflow is:
* Pull image specified from Docker Hub (default is minv2)
* Pull code from GitHub/Bitbucket and test in container
* If CI passs, build container from Dockerfile at the root of the repo
* Push container to docker hub

To use the pre-CI workflow,

1. Fork this repository
2. Connect your Shippable account to your Docker Hub account
3. Enable the repository on Shippable
4. On the repo page, go to 'Settings'
5. Choose the following -
    * Build image : Custom Image
    * Custom image action : Build
    * Custom image name : (docker hub username)/(image name)
    * Source code path : (source code path for image you want to build)
    * Push to Docker Hub : Check
6. Make sure the Dockerfile for the image you want to build is at the root of your repo
7. Trigger a manual or webhook build
8. After the build is complete, make sure your Docker Hub account has the image you just pushed. The image should be tagged with <image name>.<build number>

To use the post-CI workflow,

1. Fork this repository
2. Connect your Shippable account to your Docker Hub account
3. Enable the repository on Shippable
4. On the repo page, go to 'Settings'
5. Choose the following -
    * Build image : Custom Image
    * Custom image action : Build
    * Custom image name : (docker hub username)/(image name)
    * Source code path : (source code path for image you want to build)
    * Docker build when finished : Check
    * Image to pull: Specify image you want to run tests on, default is shippable/minv2
    * Push to Docker Hub : Check
6. Make sure the Dockerfile for the image you want to build is at the root of your repo
7. Trigger a manual or webhook build
8. After the build is complete, make sure your Docker Hub account has the right image. The image should be tagged with <image name>.<build number> 



