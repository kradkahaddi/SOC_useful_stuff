### NOTE: this is a formatted .md file. Open in an IDE for better readability.
Before you start, it is a lot of hassle, so maybe try kaggle private notebooks and private data source first?

## <B>WARNING: YOU MUST USE SoCvpn FOR JUPYTER NOTEBOOKS (SEE 3.3)</B>
## 1. Steps to login to SoC
1.	Ssh into sunfire.comp.nus.edu.sg PORT 22 (use putty maybe?)
2.	Enter plain username (no domain)
3.	Enter SoC password
4.	Login to a node (`ssh <node name>`. list of nodes: https://dochub.comp.nus.edu.sg/cf/guides/compute-cluster/hardware)
5.	RUN <code>source .bashrc</code>
6.  RUN <code>nvidia-smi</code> to check GPU RAM availability.

## 2. Setting up Aanconda (miniconda)
1.  Check for nodes with /tmp/miniconda - use these since they are easier to use.
2.  RUN 
        <code>cd /temp/miniconda/bin <br></code> 
        <code>./conda create -n <envname\> <br></code>
        <code>./conda init bash <br></code>
        <code>source ~/.bashrc <br></code>
        <code>conda activate <envname\> <br></code>
3. install whatever you need


## 3. Assuming conda is setup (with jupyter installed):
1.	<code>conda activate <env\></code>
2.	<code>jupyter notebook --no-browser --port <PORT\></code> eg. 8080
3.  connect to SoC VPN (https://dochub.comp.nus.edu.sg/cf/guides/network/vpn). Install the FortiClient and follow setup. (some alum's tutorial (for mac as well): https://hansel.gitbooks.io/moodle-setup/content/accessing-sunfire.html)
4.  Open a new local terminal: <br>RUN <code>ssh -N -L localhost:<LOCAL PORT\>:localhost:<REMORT PORT\> <soc user name\>@<node name\>.comp.nus.edu.sg</code> 
<br>(tutorial: https://www.pugetsystems.com/labs/hpc/How-To-Run-Remote-Jupyter-Notebooks-with-SSH-on-Windows-10-1477/)
<br>(tutorial: https://dochub.comp.nus.edu.sg/cf/guides/compute-cluster/access)
<br>(tutorial (from conda): https://docs.anaconda.com/anaconda/user-guide/tasks/remote-jupyter-notebook/)
5. Use localhost:<LOCAL PORT\> on browser to start working http://localhost:8888/ for example

## 4. File transfer
1.  Need to use an ftp client unless on linux
2.  For psftp (PUTTY FTP): https://the.earth.li/~sgtatham/putty/0.54/htmldoc/Chapter6.html
3.  within soc cluster use scp to transfer files from node to sunfire. Node storage is subject to periodic wipes. Backup locally or via sunfire (limited to 5GB)
4.  scp tutorial - https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/
5.  if transfering between sunfire and node just use <code>scp <filename\> <soc user name\>@<node name\> </code> or <code>scp <filename\> <soc user name\>@<sunfire\> </code> depending on what you need to do.


