GNS3 Modelling for scenario configuration and analysis

The installation depends on the type of operating system. 

##  Install on ubuntu.
For general installation guideline [GNS3 Installation Documentation](https://docs.gns3.com/1QXVIihk7dsOL7Xr7Bmz4zRzTsJ02wklfImGuHwTlaA4/)

    sudo apt-get update
    sudo apt-get upgrade
    sudo add-apt-repository ppa:gns3/ppa

    sudo apt-get update
    sudo apt-get install gns3-server
    # gui
    sudo apt-get install gns3-gui
    # support for iou (IOS on Unix)
    sudo dpkg --add-architecture i386
    sudo apt-get update 
    sudo apt-get install gns3-iou


The PPA is in the link below : (so it is possible to verify if there is release available for one's version of ubuntu )

[Personal Package Archives (PPA)](http://ppa.launchpad.net/gns3/ppa/ubuntu/pool/main/g/)

one can download the deb package and install using:
    
    # verify ubuntu release before download
    lsb_release -a 
    cat /etc/issue
    # install after download from link
    dpkg -i /path/to/downloaded_file
 
The full releases as on the gns3 github page can be found here :

[GNS3 full release](https://github.com/GNS3/gns3-gui/releases?after=v2.2.0b4)

One could download the release from the github page and install as below:


  
    # For  the gui go to the gns3-gui/server folder  install:
    # In my case, gns3-server and client was installed   from source using apt-get 
    # the server requirement file was installed to ensure everything is fine
    
    sudo pip3 install -r requirements.txt
    sudo python3 setup.py install

    #And start it 
    python3 -m gns






