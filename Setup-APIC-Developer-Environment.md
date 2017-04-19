## Set up a VMware image for APIC -related development

This document provides the steps for installing the software I use for APIC -related development to a Linux VMWare image.

1. Download VMware Workstation Pro, if you do not have it already  
1. Download the Ubuntu Operating System  
1. Create a virtual machine  
1. Install GIT  
1. Install cURL  
1. Install node.js  
1. Install API Connect Developer Toolkit  
1. Install docker  

<!-- 4. Install Java JDK 1.8 
5. Edit the system PATH
11. Install cloudfoundry CLI  
12. Install the IBM Container plugin for cloudfoundry  -->

*Not sure if this is needed:*
> For the Windows host, verify the following:  
> 1. make sure you have 22GB of available disk space (20GB for disk and 2GB for the Ubuntu iso image).  
> 2. Make sure IntelVT-X is enabled (on a Lenovo W530, in the BIOS select Security > Virtualization. Enable Intel VT-X).

### Part 1: Install VMware
* From [http://www.vmware.com/]( http://www.vmware.com/)

### Part 2: Download the Ubuntu Operating System
* From [https://www.ubuntu.com/]( https://www.ubuntu.com/). ~1.4GB .iso file. I am currently using Ubuntu 16.04.2.

### Part 3: Create a virtual machine 
* Use the Ubuntu iso file as the OS in the VMware image: create a new virtual machine, and point it to the downloaded iso file.
* I chose to store the virtual image as a single file for better performance. I do not need my development environment to be portable.

<!--
### Part 4: Install Java JDK 1.8 

The rest of the instructions apply to the image you have just created. Thus, 'In a browser...' means a browser on the image.

1. In a browser open [https://www.oracle.com]( https://www.oracle.com).  
2. In the list of menu options, hover over **Downloads** (if you cannot see it, reduce the zoom of the browser until it appears).  
3. Under Popular Downloads to the left, click **Java for Developers**.  
4. Click the download button for **Java Platform (JDK) 8u111** (Note: your minor version may be different).  
5. Under the section entitled Java SE Development Kit 8u111, click the button for **Accept License Agreement**.  
6. Select the **tgz** file for Linux 64-bit (jdk-8u111-linux-x64.tar.gz).  
7. **Save** the file.  

You now have the compressed file on your image. The next step is to move it to the correct location and unzip it.  

1. Create a directory for the file. In the Terminal, type the following:  
`sudo mkdir /usr/local/java`
2. Change to the download directory:  
`cd ~/Downloads`
3. You copy recursively (-r) the file in this directory to the location you want:  
`sudo cp -r jdk-8u111-linux-x64.tar.gz /usr/local/java`
4. Change to the new java directory:  
`cd /usr/local/java`
5. Verify that the tar.gz file was copied:  
`ls`
5. Unzip the file (if you want to see the list of unzipped files, replace _xf_ with _xvf_):  
`sudo tar xf jdk-8u111-linux-x64.tar.gz`
6. Verify that the extraction was successful:  
`cd jdk1.8.0_111`  
`ls`  
You should see 6 directories, 6 files, and 2 zip files.

### Part 5: Edit the system PATH
You add JAVA_HOME to the PATH by editing the profile file.  

1. Open the **profile** file in an editor:  
`sudo gedit /etc/profile`
2. **Add** these lines to the bottom of the file:  
`JAVA_HOME=/usr/local/java/jdk1.8.0_111`  
`PATH=$JAVA_HOME/bin:$PATH`  
`export JAVA_HOME`  
`export PATH`  
3. **Save** and **close** the profile file.  

The final step is to provide the information about the new PATH to the system. You do this with three update-alternative commands for Java, javac, and javaws:  

1. Update the java information (the final argument is the priority):  
`sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.8.0_111/jre/bin/java" 1`
2. Update the compiler information:  
`sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.8.0_111/bin/javac" 1`
3. Update the javaws information:  
`sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk1.8.0_111/bin/javaws" 1`
4. Verify that your installation of Java is recognized. Type:  
`java -version`
5. You should see information about the java version, Java runtime, and Java HotSpot.
-->

### Part 4: Install GIT
`sudo apt-get install git-all`
<!-- Git Large File Storage (LFS) https://help.github.com/articles/installing-git-large-file-storage/ -->

### Part 5: Install cURL
`sudo apt-get install curl`

### Part 6: Install Node.js v6.1.0 (includes npm 3.10.10)

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Part 7: Install API Connect Developer Toolkit
`sudo npm install -g apiconnect`

### Part 8: Install Docker & Docker Compose

1. Instructions at: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04
1. Instructions at: https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-16-04

<!--
1. Type  
`docker`  
Since it is not installed yet, the response suggests that you install it using apt install docker.io.  
2. Type the following (at the message _Do you want to continue_, type **Y**):  
`sudo apt install docker.io`  
3. Add the user to the docker group. The group may have been created automatically, in which case the first command will generate a warning message. You can ignore this and continue with the second command:  
`sudo groupadd docker`  
`gpasswd dockrr -a bmxuser`
4. When the installation has completed type  
`sudo docker run hello-world`  
You should see the response starting `Hello from Docker!`.  
**NOTE**: You may need to run the command a second time to see the correct response.  
-->


### Checking versions:
1. Ubuntu version: `lsb_release -a`
