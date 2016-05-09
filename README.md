# VLC Streaming using Mininet

#### Objective 
In this experiment, video files are streamed over a butterfly topology using a custom packet scheduler. The received video stream is captured and is compared to the source video stream to check how well the packet scheduler is working.

#### Topology
2 switches connected to each other. Each switch has `n/2` number of hosts directly attached to it, making the total number of hosts equal to `n` and total number of switches `2`. Such a topology is called a butterfly topology

#### Steps to start the streaming and collecting process
1. Place the controllers `2snh_ssim_Controller_congest.py`, `2snh_ssim_Controller_QoS.py` into the right location using the following commands
```
$ cp controllers/2snh_ssim_Controller_congest.py ~/pox/pox/misc/
$ cp controllers/2snh_ssim_Controller_QoS.py ~/pox/pox/misc/
```
2. Decide the number of hosts in the topology; 4 for example 
3. Set the controller file global variable `n = 4`
4. Start running the controller `2snh_ssim_Controller_QoS.py`:
```
$ pox/pox.py log.level --DEBUG misc.2snh_ssim_Controller_QoS
```
5. Run the python script which sets up the topology (with a total of 4 hosts as decided above) and does vlc-streaming:
```
$ sudo ./myvlctest.py 4
```