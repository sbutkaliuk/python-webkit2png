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

Usage
=====
- For help run: ``python scripts/webkit2png -h``

![Alt Text](http://24.media.tumblr.com/tumblr_m9trixXFHn1rxlmf0o1_400.gif)
