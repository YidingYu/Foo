# Install NS3 on Ubuntu 16.04

1. Install required compilers and additional packages
```
sudo apt-get install gcc g++ python3 python3-dev
sudo apt-get install mercurial python3-setuptools git
```
2. qt4 development tools are needed for Netanim animator
```
sudo apt-get install qt4-dev-tools libqt4-dev
```
3. Compilation packages
```
sudo apt-get install cmake libc6-dev libc6-dev-i386 g++-multilib
```
4. Debugging tools, valgrind for memory debugging
```
sudo apt-get install gdb valgrind
```
5. GNU Scientific Library (GSL) support for more accurate WiFi error models
```
sudo apt-get install gsl-bin libgsl2 libgsl-dev
```
6. For flex lexical analyzer and bison parser generator
```
sudo apt-get install flex bison libfl-dev
```
7. To read pcap packet traces
```
sudo apt-get install tcpdump
```
8. Database support for statistics framework
```
sudo apt-get install sqlite sqlite3 libsqlite3-dev
```
9. For Xml library support
```
sudo apt-get install libxml2 libxml2-dev
```
10. For creating graphical user interface
```
sudo apt-get install libgtk2.0-0 libgtk2.0-dev
```
11. For virtual machines and ns-3
```
sudo apt-get install vtun lxc
```
12. For source code modification
```
sudo apt-get install uncrustify
```
13. For editting image and texlive for documentation
```
sudo apt-get install doxygen graphviz imagemagick
sudo apt-get install texlive texlive-extra-utils texlive-latex-extra texlive-font-utils
sudo apt-get install python-sphinx dia
```
14. For pyviz visualizer
```
sudo apt-get install python-pygraphviz python-kiwi python-pygoocanvas libgoocanvas-dev ipython
```
15. For openflow module
```
sudo apt-get install libboost-signals-dev libboost-filesystem-dev
```
16. For MPI-based distribution emulation
```
sudo apt-get install openmpi-bin openmpi-common openmpi-doc libopenmpi-dev
```
17. Create a directory NS3 under home directory for downloading ns3 files
···
cd ~
mkdir NS3
cd NS3
hg clone http://code.nsnam.org/ns-3-allinone
···
As the hg (Mercurial) command executes, you should see something like the following displays
```
destination directory: ns-3-allinone
requesting all changes
adding changesets
adding maniftest
adding file changes
added 26 changesets with 40 changes to 7 files
7 files updated, 0 files merged, 0 files removed, 0 files unresolved
```
18. After the clone command completes, you find directory ns-3-allione under your /home/NS3 directory. Run the python file to download and build the ns-3 distribution
```
cd ns-3-allinone
./download.py -n ns-3-dev
```
After download process completes, you can find several new directories under /home/NS3/ns-3-allinone as below
```
build.py* constant.pyc download.py* nsc/ README util.pyc
constants.py dist.py* ns-3-dev/ pybindgen/ util.py
```
19. Now complile and build the packages. Run build python file
```
./build.py
```
20 Configuration with Waf
```
cd ns-3-dev
CXXFLAGS="-03" ./waf configure
./waf -d optimized configure
./waf -d debug configure
./waf
./waf --enable-examples configure
./waf --enable-tests configure
```
21. Now verifyu installation
```
./test.py
```
You wil get output as below
```
PASS: TestSuite histoggram
PASS: TestSuite ns3-wifi-interference
PASS: TestSuite ns3-tcp-cwnd
PASS: TestSuite ns3-tcp-interoperability
PASS: TestSuite sample
```
Run hello simulator
```
./waf --run hello-simulator
```


