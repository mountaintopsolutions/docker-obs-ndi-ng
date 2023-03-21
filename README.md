# docker-obs-ndi-ng
Dockerized OBS + NDI plugin Next Generation

Based on the old style container before the latest rebase from:
https://github.com/patrickstigler/docker-obs-ndi
and 
https://github.com/Z0ink5/obs-ndi-docker which uses the old image format but doesn't quite work correctly. 

For now the newer style image based on the accetto image is not working correctly without major after build modifications. 

A working version of the legacy image is posted to the legacy branch.


#### WHATS TESTED (LEGACY VERSION)
 - [x] VNC works
 - [x] OBS works
 - [x] Nvidia GPU Encoding works
 - [x] NDI plugin works
 - [x] Streaming works

#### WHATS NOT TESTED

 - [ ] Intel Quicksync encoding (Should still work?)
 - [ ] AMD GPU encoding (no packages installed)



Update the repository URL in unraid to be 

    mountaintopsolutions/docker-obs-ndi-ng:legacy-latest

 and apply to fix your obs-ndi plugin

or run from the command line on any properly configured docker host with something like:

for all gpus: 

    docker run -v config:$pwd/config -P --shm-size=256m -e NVIDIA_VISIBLE_DEVICES=all -e NVIDIA_DRIVER_CAPABILITIES=all --runtime=nvidia --ip 192.168.1.247 -d -p 5901:5901 --net br0 --dns="192.168.1.5" docker.io/mountaintopsolutions/docker-obs-ndi-ng:legacy-latest

or only a specific gpu:

    docker run -v config:$pwd/config -P --shm-size=256m -e NVIDIA_VISIBLE_DEVICES=GPU-d64e2a1e-15b8-866f-8ada-a4e94dacc071 -e NVIDIA_DRIVER_CAPABILITIES=all --runtime=nvidia --ip 192.168.1.247 -d -p 5901:5901 --net br0 --dns="192.168.1.5" docker.io/mountaintopsolutions/docker-obs-ndi-ng:legacy-latest
