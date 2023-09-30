## VM Setup (Windows 10 Hyper-V)
1. New > Virtual Machine
2. Name: u23s2_capstone_retest_BHPatch
3. Generation 2
4. Memory: 4096MiB
5. Connection: Default Switch
6. Create New VHD: 60GiB
7. Install from bootable: ubuntu-22.04.2-live-server-amd64.iso
8. Finish (Don't start it, yet)
9. Settings:
	1. Security: Secure Boot Template: Microsoft UEFI Certificate Authority; Apply
	2. Processor: Virtual Processors: 2; Apply
10. Start VM
11. Connect to VM

## VM configuration (setup/install settings of Ubuntu 22.04 Guest OS)
1. Install Ubuntu
2. English (default; US)
3. Keep Keyboard defaults (US)
4. Ubuntu Server (default)
5. Keep default DHCP network connections (takes a second to load in DHCP config)
6. Don't use Proxy
7. Change Mirror address from "us..." to "au..."
8. Update to the new Installer
9. Leave default storage layout
10. Leave default filesystem configuration
11. Continue
12. Details:
	1. User: scitech
	2. server name: node_retest_3-39_bhpatched
	3. username: scitech
	4. password: ucstudent
	5. confirm pass: ucstudent
13. Skip Ubuntu Pro
14. Install OpenSSH Server
15. Skip installing server snaps
16. Wait for all installation steps to finish (prompt at bottom will change to "Reboot Now")
17. Reboot
18. Log in with scitech credentials, then run "Commands on Guest VM" commands

## Commands on Guest VM
```bash

sudo apt update && sudo apt upgrade -y

# Select all services to restart (don't leave defaults)

git clone https://gitlab.com/nsnam/ns-3-allinone

git clone https://github.com/edcricho/Manet9785-23-7

cd ns-3-allinone/

./download.py

cp /home/scitech/Manet9785-23-7/bhPatches_ns3.25/aodv-routing-protocol.cc ns-3-dev/src/aodv/model/aodv-routing-protocol.cc
#### Daniel's version -   cp /srv/sharedfolder/manet/Manet9785-23-7/bhPatches_ns3.25/aodv-routing-protocol.cc ns-3-dev/src/aodv/model/aodv-routing-protocol.cc #######

cp /home/scitech/Manet9785-23-7/bhPatches_ns3.25/aodv-routing-protocol.h ns-3-dev/src/aodv/model/aodv-routing-protocol.h
#### Daniel's version -   cp /srv/sharedfolder/manet/Manet9785-23-7/bhPatches_ns3.25/aodv-routing-protocol.h ns-3-dev/src/aodv/model/aodv-routing-protocol.h #######


sudo apt install ccache cmake g++ mercurial qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools -y

./build.py --enable-examples --enable-tests

cd ns-3-dev/

mkdir capstone

./test.py

cp src/aodv/examples/aodv.cc scratch/

vi scratch/aodv.cc # terminal text editor - only keyboard works

# Type "i" to go into "Insert" mode
# insert '#include "ns3/netanim-module.h"' at line 24
# insert 'AnimationInterface anim ("animation.xml");' at line 160
# insert 'anim.EnablePacketMetadata (true);' at line 161
# Hit ESC key
# Type ":wq" to save changes and exit the file

./ns3 run scratch/aodv.cc --cwd=capstone/ -- visual
# Change "aodv.cc" file to whatever file you need - it's the file you'll be working on (work on files inside the "scratch" directory)
```