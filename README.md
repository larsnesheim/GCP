# Setup GCP cluster
1. Go to GCP console and choose hardware. Start VM.
  1. Choose C2 cpu with N cores
  2. Boot disk at least 100GB
  3. Storage disk for data and results
  4. Use rocky linux
5. Login to VM using ssh

# install unix packages
````
sudo dnf -y wget
sudo dnf install gcc-c++
sudo dnf install git
sudo dnf install epel-release
sudo dnf install screen
sudo dnf install make
sudo dnf install tmux    # replacement for screen (don't know how to use)
````

# download intel oneAPI base kit
````
wget https://registrationcenter-download.intel.com/akdlm/IRC_NAS/e6ff8e9c-ee28-47fb-abd7-5c524c983e1c/l_BaseKit_p_2024.2.1.100.sh
````

# install intel oneAPI basekit 
````
sudo sh ./l_BaseKit_p_2024.2.1.100.sh -a --silent --cli --eula accept
````

# download hpc toolkit
````
wget https://registrationcenter-download.intel.com/akdlm/IRC_NAS/d461a695-6481-426f-a22f-b5644cd1fa8b/l_HPCKit_p_2024.2.1.79.sh
````

# install hpc toolkit
````
sudo sh ./l_HPCKit_p_2024.2.1.79.sh
````

# download and install NAG
````
wget https://support.nag.com/downloads/impl/nll6i302bl.tgz
tar -xvzf nll6i302bl.tgz
nll6i302bl/install.sh
````

# set up github ssh key
````
ssh-keygen -t ed25519 -C "larsnesheim71@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
````

# clone code from github
````
git clone URL
````

# upload license key
Upload the license key and store in ${NAGDIR}

# set environment variables
````
export NAG_KUSARI_FILE=/home/larsnesheim71/NAG/nag_key.txt
source /opt/intel/oneapi/setvars.sh
source /home/larsnesheim71/NAG/nll6i302bl/scripts/nagvars.sh int32 vendor static
````
