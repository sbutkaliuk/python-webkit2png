**webkit2png** 
==============

About
------
Python script that takes screenshots (browsershots) using webkit

##Installation
Ubuntu
------
- Add following packages: ``apt-get install python-qt4 libqt4-webkit xvfb``
- Install the flash plugin to screenshot Adobe Flash files: ``apt-get install flashplugin-installer``

Automated installation via ```pip```
-------------------------------------
- Install pip: ```apt-get install python-pip```
- Install webkit2png: ```pip install webkit2png```

Manual installation via Git
-----------------------------
- Install git: ``apt-get install git-core``
- Create directory: ``mkdir python-webkit2png``
- Clone the project: ``git clone https://github.com/adamn/python-webkit2png.git python-webkit2png``
- Install with: ``python python-webkit2png/setup.py install``

FreeBSD
-------
- install qt4 webkit: ```www/py-qt4-webkit, www/qt4-webkit, devel/py-qt4```
- install pip: ``devel/py-pip``
- install via: ``pip install webkit2png``

Completely manual installation (with PyQt)
-----------------------------------------
- install qt4 (or qt5) core, webkit, network and gui modules
- install [SIP](http://pyqt.sourceforge.net/Docs/sip4/installation.html)
- install [PyQt4](http://pyqt.sourceforge.net/Docs/PyQt4/installation.html#configuring-pyqt4) (I used command ```python configure-ng.py --qmake /usr/bin/qmake-qt5 --sip ../sip-4.17/sipgen/sip --sip-incdir ../sip-4.17/siplib/ --no-tools --no-sip-files --no-designer-plugin --concatenate --concatenate-split 2 --confirm-license --assume-shared``` for configuring)
- check if everything is working ```python webkit2png/scripts.py --help``` and ```python webkit2png/scripts.py -d :{{yourdisplayid}} --output-dir=. http://www.google.com```
- it's better to use 24 bit virtual displays if it's possible

Manual installation for Amazon AMI Linux
----------------------------------------
Amazon AMI Linux is known for it's problem with Qt5 installation (e.g. http://takeyuweb.hatenablog.com/entry/2016/03/25/134609). 

Next script can be used to install all needed dependencies for webkit2png

```bash
CORES=1
SIP="sip-4.19.3"
wget https://sourceforge.net/projects/pyqt/files/sip/$SIP/$SIP.tar.gz
tar -zxvf $SIP.tar.gz

pushd $SIP
        python configure.py
        make -j $CORES
        sudo make install
popd

if yum list installed qt5-qtwebkit-devel >/dev/null 2>&1; then
        echo "qt5-qtwebkit-devel was installed some time ago."
else
        # qt5-webkit is available through epel repository, so let's enable it
        sudo yum install -y epel-release
        sudo yum-config-manager --enable epel

        # Needed for gtk2
        sudo yum install -y ftp://ftp.icm.edu.pl/vol/rzm6/linux-slc/slc67/x86_64/Packages/gdk-pixbuf2-2.24.1-5.el6.x86_64.rpm \
                ftp://ftp.pbone.net/mirror/ftp.centos.org/6.9/os/x86_64/Packages/hicolor-icon-theme-0.11-1.1.el6.noarch.rpm \
                ftp://ftp.pbone.net/mirror/ftp.centos.org/6.9/os/x86_64/Packages/atk-1.30.0-1.el6.x86_64.rpm

        # Needed for qt5-webkit
        sudo yum install -y ftp://ftp.icm.edu.pl/vol/rzm6/linux-oracle-repo/OracleLinux/OL6/latest/x86_64/getPackage/gtk2-2.24.23-6.el6.x86_64.rpm

        # Install qt5-webkit itself
        sudo yum install -y qt5-qtwebkit-devel
fi

wget http://sourceforge.net/projects/pyqt/files/PyQt4/PyQt-4.12.1/PyQt4_gpl_x11-4.12.1.tar.gz
tar -zxvf PyQt4_gpl_x11-4.12.1.tar.gz

pushd PyQt4_gpl_x11-4.12.1
        python configure-ng.py --qmake /usr/bin/qmake-qt5 --sip ../$SIP/sipgen/sip --sip-incdir ../$SIP/siplib/ --no-tools --no-sip-files --no-designer-plugin --concatenate --concatenate-split 2 --confirm-license --assume-shared
        make -j $CORES
        sudo make install
popd

```

Usage
=====
- For help run: ``python scripts/webkit2png -h``

![Alt Text](http://24.media.tumblr.com/tumblr_m9trixXFHn1rxlmf0o1_400.gif)
