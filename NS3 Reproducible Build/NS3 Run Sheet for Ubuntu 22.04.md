```bash
sudo apt update && sudo apt upgrade -y
# Select all services to restart (don't leave defaults)
git clone https://gitlab.com/nsnam/ns-3-allinone
git clone https://github.com/edcricho/Manet9785-23-7 # Will need to be updated to new Group's forked repo
cd ns-3-allinone/
./download.py
cp /home/scitech/Manet9785-23-7/bhPatches_ns3.25/aodv-routing-protocol.cc ns-3-dev/src/aodv/model/aodv-routing-protocol.cc
cp /home/scitech/Manet9785-23-7/bhPatches_ns3.25/aodv-routing-protocol.h ns-3-dev/src/aodv/model/aodv-routing-protocol.h
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