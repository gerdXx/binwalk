Before You Start
================

Binwalk supports Python 2.7 - 3.x. Although most systems have Python2.7 set as their default Python interpreter, binwalk does run faster in Python3. Installation procedures for both are provided below.

Installation
============

Installation follows the typical Python installation procedure:

```bash
# Python2.7
$ sudo python setup.py install
```

```bash
# Python3.x
$ sudo python3 setup.py install
```

Dependencies
============

Besides a Python interpreter, there are no installation dependencies for binwalk. All dependencies are optional run-time dependencies, and unless otherwise specified, are available from most Linux package managers.

Although all binwalk run-time dependencies are optional, the `python-lzma` module is highly recommended for improving the reliability of signature scans. This module is included by default in Python3, but must be installed separately for Python2.7:

```bash
$ sudo apt-get install python-lzma
```

Binwalk uses [pyqtgraph](http://www.pyqtgraph.org) to generate graphs and visualizations, which requires the following: 

```bash
# Python2.7
$ sudo apt-get install libqt4-opengl python-opengl python-qt4 python-qt4-gl python-numpy python-scipy python-pip
$ sudo pip install pyqtgraph
```

```bash
# Python3.x
$ sudo apt-get install libqt4-opengl python3-opengl python3-pyqt4 python3-pyqt4.qtopengl python3-numpy python3-scipy python3-pip
$ sudo pip3 install pyqtgraph
```

Binwalk's `--disasm` option requires the [Capstone](http://www.capstone-engine.org/) disassembly framework and its corresponding Python bindings:

```bash
$ wget http://www.capstone-engine.org/download/2.1.2/capstone-2.1.2.tgz
$ tar -zxvf capstone-2.1.2.tgz
$ (cd capstone-2.1.2 && ./make.sh && sudo make install)
$ (cd capstone-2.1.2/bindings/python && sudo python ./setup.py install)
```

Binwalk relies on multiple external utilties in order to automatically extract/decompress files and data:

```bash
# Install standard extraction utilities
$ sudo apt-get install mtd-utils gzip bzip2 tar arj lhasa p7zip p7zip-full cabextract cramfsprogs cramfsswap squashfs-tools
```

```bash
# Install sasquatch to extract non-standard SquashFS images
$ sudo apt-get install zlib1g-dev liblzma-dev liblzo2-dev
$ git clone https://github.com/devttys0/sasquatch
$ (cd sasquatch && make && sudo make install)
```

```bash
# Install unstuff (closed source) to extract StuffIt archive files
$ wget -O - http://my.smithmicro.com/downloads/files/stuffit520.611linux-i386.tar.gz | tar -zxv
$ sudo cp bin/unstuff /usr/local/bin/
```

Installing the IDA Plugin
=========================

If IDA is installed on your system, you may optionally install the binwalk IDA plugin by simply copying the `src/scripts/binida.py` file into IDA's `plugins` directory.


Uninstalling Binwalk
====================

If binwalk has been installed to a standard system location (e.g., via `setup.py install`), it can be removed by running:

```bash
# Python2.7
$ sudo python setup.py uninstall
```

```bash
# Python3
$ sudo python3 setup.py uninstall
```

Note that this does _not_ remove any of the manually installed dependencies.

