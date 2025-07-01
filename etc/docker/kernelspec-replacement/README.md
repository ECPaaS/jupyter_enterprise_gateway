Please follow the steps to build the kernelspec images.
1. cd jupyter_enterprise_gateway folder 
2. docker build -f etc/docker/kernelspec-replacement/Dockerfile -t ecpaas-dockerhub.atan-networks.com.cn/jupyter_enterprise_gateway/kernelspecs-image:1.0.0 .
3. Push the kernelspecs-image into image repository. 
