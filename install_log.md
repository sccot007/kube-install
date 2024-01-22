root@rb-master:/# cd root
root@rb-master:~# apt-get update
Hit:1 https://download.docker.com/linux/ubuntu jammy InRelease
Hit:3 http://ports.ubuntu.com/ubuntu-ports jammy InRelease                            
Get:4 http://ports.ubuntu.com/ubuntu-ports jammy-updates InRelease [119 kB]
Get:2 https://packages.cloud.google.com/apt kubernetes-xenial InRelease [8993 B]             
Hit:5 http://ports.ubuntu.com/ubuntu-ports jammy-backports InRelease
Get:6 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease [110 kB]
Get:7 http://ports.ubuntu.com/ubuntu-ports jammy-updates/main arm64 Packages [1118 kB]
Get:8 http://ports.ubuntu.com/ubuntu-ports jammy-security/main arm64 Packages [910 kB]
Get:9 http://ports.ubuntu.com/ubuntu-ports jammy-security/main Translation-en [202 kB]
Get:10 http://ports.ubuntu.com/ubuntu-ports jammy-security/universe arm64 Packages [767 kB]
Get:11 http://ports.ubuntu.com/ubuntu-ports jammy-security/universe Translation-en [158 kB]
Fetched 3393 kB in 5s (684 kB/s)                                 
Reading package lists... Done
root@rb-master:~# apt-get install -y apt-transport-https ca-certificates curl gpg
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
ca-certificates is already the newest version (20230311ubuntu0.22.04.1).
curl is already the newest version (7.81.0-1ubuntu1.15).
gpg is already the newest version (2.2.27-3ubuntu2.1).
gpg set to manually installed.
apt-transport-https is already the newest version (2.4.11).
0 upgraded, 0 newly installed, 0 to remove and 57 not upgraded.
root@rb-master:~# curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
root@rb-master:~# echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /
root@rb-master:~# apt-get update
Hit:1 https://download.docker.com/linux/ubuntu jammy InRelease
Get:2 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.29/deb  InRelease [1186 B]
Get:3 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.29/deb  Packages [3981 B]
Hit:4 http://ports.ubuntu.com/ubuntu-ports jammy InRelease
Hit:5 http://ports.ubuntu.com/ubuntu-ports jammy-updates InRelease
Hit:6 http://ports.ubuntu.com/ubuntu-ports jammy-backports InRelease
Hit:7 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease
Fetched 5167 B in 3s (1841 B/s)
Reading package lists... Done
root@rb-master:~# apt-get install -y kubelet kubeadm kubectl
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  conntrack cri-tools ebtables kubernetes-cni socat
The following NEW packages will be installed:
  conntrack cri-tools ebtables kubeadm kubectl kubelet kubernetes-cni socat
0 upgraded, 8 newly installed, 0 to remove and 57 not upgraded.
Need to get 82.5 MB of archives.
After this operation, 335 MB of additional disk space will be used.
Get:2 http://ports.ubuntu.com/ubuntu-ports jammy/main arm64 conntrack arm64 1:1.4.6-2build2 [32.4 kB]
Get:1 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.29/deb  cri-tools 1.29.0-1.1 [18.4 MB]
Get:7 http://ports.ubuntu.com/ubuntu-ports jammy/main arm64 ebtables arm64 2.0.11-4build2 [85.4 kB]
Get:8 http://ports.ubuntu.com/ubuntu-ports jammy/main arm64 socat arm64 1.7.4.1-3ubuntu4 [348 kB]
Get:3 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.29/deb  kubernetes-cni 1.3.0-1.1 [28.9 MB]
Get:4 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.29/deb  kubelet 1.29.1-1.1 [17.2 MB]
Get:5 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.29/deb  kubectl 1.29.1-1.1 [8989 kB]         
Get:6 https://prod-cdn.packages.k8s.io/repositories/isv:/kubernetes:/core:/stable:/v1.29/deb  kubeadm 1.29.1-1.1 [8638 kB]         
Fetched 82.5 MB in 8s (10.0 MB/s)                                                                                                  
Selecting previously unselected package conntrack.
(Reading database ... 102073 files and directories currently installed.)
Preparing to unpack .../0-conntrack_1%3a1.4.6-2build2_arm64.deb ...
Unpacking conntrack (1:1.4.6-2build2) ...
Selecting previously unselected package cri-tools.
Preparing to unpack .../1-cri-tools_1.29.0-1.1_arm64.deb ...
Unpacking cri-tools (1.29.0-1.1) ...
Selecting previously unselected package ebtables.
Preparing to unpack .../2-ebtables_2.0.11-4build2_arm64.deb ...
Unpacking ebtables (2.0.11-4build2) ...
Selecting previously unselected package kubernetes-cni.
Preparing to unpack .../3-kubernetes-cni_1.3.0-1.1_arm64.deb ...
Unpacking kubernetes-cni (1.3.0-1.1) ...
Selecting previously unselected package socat.
Preparing to unpack .../4-socat_1.7.4.1-3ubuntu4_arm64.deb ...
Unpacking socat (1.7.4.1-3ubuntu4) ...
Selecting previously unselected package kubelet.
Preparing to unpack .../5-kubelet_1.29.1-1.1_arm64.deb ...
Unpacking kubelet (1.29.1-1.1) ...
Selecting previously unselected package kubectl.
Preparing to unpack .../6-kubectl_1.29.1-1.1_arm64.deb ...
Unpacking kubectl (1.29.1-1.1) ...
Selecting previously unselected package kubeadm.
Preparing to unpack .../7-kubeadm_1.29.1-1.1_arm64.deb ...
Unpacking kubeadm (1.29.1-1.1) ...
Setting up conntrack (1:1.4.6-2build2) ...
Setting up kubectl (1.29.1-1.1) ...
Setting up ebtables (2.0.11-4build2) ...
Setting up socat (1.7.4.1-3ubuntu4) ...
Setting up cri-tools (1.29.0-1.1) ...
Setting up kubernetes-cni (1.3.0-1.1) ...
Setting up kubelet (1.29.1-1.1) ...
Setting up kubeadm (1.29.1-1.1) ...
Processing triggers for man-db (2.10.2-1) ...
Scanning processes...                                                                                                               
Scanning candidates...                                                                                                              
Scanning processor microcode...                                                                                                     
Scanning linux images...                                                                                                            

Failed to check for processor microcode upgrades.

Restarting services...
Service restarts being deferred:
 systemctl restart bluetooth.service
 /etc/needrestart/restart.d/dbus.service
 systemctl restart docker.service
 systemctl restart getty@tty1.service
 systemctl restart hciuart.service
 systemctl restart networkd-dispatcher.service
 systemctl restart systemd-logind.service
 systemctl restart unattended-upgrades.service
 systemctl restart wpa_supplicant.service

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
root@rb-master:~# apt-mark hold kubelet kubeadm kubectl
kubelet set on hold.
kubeadm set on hold.
kubectl set on hold.
