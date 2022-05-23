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