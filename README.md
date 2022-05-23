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

## [Install Google Chrome](https://tecadmin.net/install-google-chrome-in-ubuntu/)
  1. add (if not added already) the Google Chrome repository on your system using the following command. While using PPA to our system we also receive the latest updates whenever you check for system updates. `wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -`
  2. create a PPA file for Google chrome on your system by running command `sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' `
  3. After adding the Google Chrome repository in our system use following commands to install the latest Google Chrome stable release. If you already have installed an older version, It will upgrade the currently installed version with the recent stable version. `sudo apt-get update ` & `sudo apt-get install google-chrome-stable ` When prompted for confirmation, Press ‘y’ and hit enter to complete Google chrome installation.

## [Install ChromeDriver](https://tecadmin.net/setup-selenium-chromedriver-on-ubuntu/)
  1. Find out the Google chrome version installed on your system. `google-chrome --version `
  2. Next, visit the [Chromedriver download page](https://chromedriver.chromium.org/downloads) and download the matching version of chromedriver on your system.
  3. In my case, Google chrome `101.0.4951.41` is running on my system. So download the following file. You must make sure to download the correct version of a file: `wget https://chromedriver.storage.googleapis.com/101.0.4951.41/chromedriver_linux64.zip`
  4. Unzip the downloaded file `unzip chromedriver_linux64.zip`
  5. You can find the latest ChromeDriver on its [official download page](https://sites.google.com/a/chromium.org/chromedriver/downloads). Now execute below commands to configure ChromeDriver on your system. `sudo mv chromedriver /usr/bin/chromedriver`, `sudo chown root:root /usr/bin/chromedriver`, `sudo chmod +x /usr/bin/chromedriver`

## [Install and configure PostgreSQL](https://medium.com/digitalcrafts/how-to-set-up-an-ec2-instance-with-github-node-js-and-postgresql-e363cb771826)
   Follow these instructions to install and configure your PostgreSQL database. Once you’ve restarted postgres, your ubuntu database should be ready to go. You can proceed as usual with database creation, or upload your existing schema with the command `psql -f yourschema.sql yourdbname`
   1. `sudo apt-get install postgresql postgresql-contrib`
   2. `sudo -i -u postgres`
   3. `psql`
   4. `create role ubuntu;`
   5. `alter role ubuntu with superuser;`
   6. `alter role ubuntu with createdb;`
   7. `alter role ubuntu with login;`
   8. `\q`
   9. `exit`
   10. `sudo vim /etc/postgresql/9.5/main/pg_hba.conf`
   11. `sudo systemctl restart postgresql`
   12. `psql -f schema.sql ubuntu`