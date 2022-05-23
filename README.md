# Cloud-instance-setup(Ubuntu 20.04)
## [Install Conda](https://linuxize.com/post/how-to-install-anaconda-on-ubuntu-20-04/)
  1. Download the Anaconda installation script with your web browser or wget: `wget -P /tmp https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh`
  2. This step is optional, but it is recommended to verify the data integrity of the script. Use the sha256sum command to display the script checksum: `sha256sum /tmp/Anaconda3-2020.02-Linux-x86_64.sh`
  3. Run the script to start the installation process: `bash /tmp/Anaconda3-2020.02-Linux-x86_64.sh`
  4. To activate the Anaconda installation, you can either close and re-open your shell or load the new PATH environment variable into the current shell session by typing: `source ~/.bashrc`
  5. Updating the Anaconda is a pretty straight forward process. Open your terminal and enter: `conda update --all`
  6. Uninstalling Anaconda `rm -rf ~/anaconda3 ~/.condarc ~/.conda ~/.continuum`
  7. Install python 3.8 `conda create -n python38 python=3.8`
  8. To activate this environment `conda activate py38`
  9. To deactivate an active environment `conda deactivate`

## [Install Node.js](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04)
To install a different version of Node.js, you can use a PPA (personal package archive) maintained by NodeSource. These PPAs have more versions of Node.js available than the official Ubuntu repositories. Node.js v12, v14, and v16 are available as of the time of writing.
  1. First, we will install the PPA in order to get access to its packages. From your home directory, use curl to retrieve the installation script for your preferred version, making sure to replace 16.x with your preferred version string (if different). `cd ~`  then `curl -sL https://deb.nodesource.com/setup_16.x -o /tmp/nodesource_setup.sh`
  2. Inspect the contents of the downloaded script with nano (or your preferred text editor) `nano /tmp/nodesource_setup.sh`
  3. When you are satisfied that the script is safe to run, exit your editor, then run the script with sudo: `sudo bash /tmp/nodesource_setup.sh`
  4. The PPA will be added to your configuration and your local package cache will be updated automatically. You can now install the Node.js package in the same way you did in the previous section: `sudo apt install nodejs`
  5. Verify that you’ve installed the new version by running node with the -v version flag: `node -v`
  6. PM2 is a production process manager for Node.js applications with a built-in load balancer. It allows you to keep applications alive forever, to reload them without downtime and to facilitate common system admin tasks. `sudo npm install pm2 -g`