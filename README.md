This manual covers information about necessary tools to setup before workshop.

## Install WSL
WSL - Windows Subsystem for Linux.

Run Widnows Powershell (or 
Command prompt) as administrator and execute below command
```
wsl --install -d Ubuntu-20.04
```

More detailed instructions for installation WSL ver.1 (that version is  suitable for workshop purpose).
```
https://docs.microsoft.com/en-us/windows/wsl/install
```

## Run WSL terminal
In Windows
```
press Windows logo key + R
type wsl
```
You can also find wsl application in Start menu. 
If you encounter any problem, try to run wsl app as administrator

## First things on linux
1. update your ubuntu instance `sudo apt update`
2. check you git version `git --version`
3. if git is not installed, install it `sudo apt install git` 

## Install terraform
1. install curl module `sudo apt install  software-properties-common gnupg2 curl`
2. import repository GPG key 1/2 `curl https://apt.releases.hashicorp.com/gpg | gpg --dearmor > hashicorp.gpg`
3. import repository GPG key 2/2 `sudo install -o root -g root -m 644 hashicorp.gpg /etc/apt/trusted.gpg.d/`
4. [Ubuntu 22.04] add Hashicorp repository

```sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com focal main"```

5. [Ubuntu 20.04/18.04] add Hashicorp repository

```sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main"```

6. install terraform `sudo apt install terraform`
7. check terraform version `terraform --version`. If provided you install terraform correctly. Gratulation!

## Install AWS CLI
AWS-CLI installer for Linux x86
```
sudo apt install unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

## Install EKSCTL
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```

## Install KUBECTL
```
curl -o kubectl https://amazon-eks.s3-us-west-2.amazonaws.com/1.21.2/2021-07-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
mkdir -p $HOME/bin && mv ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
kubectl version --short --client
```

## Install aws-iam-authenticator
```
curl -o aws-iam-authenticator https://amazon-eks.s3.us-west-2.amazonaws.com/1.21.2/2021-07-05/bin/linux/amd64/aws-iam-authenticator
chmod +x ./aws-iam-authenticator
mkdir -p $HOME/bin && mv ./aws-iam-authenticator $HOME/bin/aws-iam-authenticator && export PATH=$PATH:$HOME/bin
aws-iam-authenticator version
```

## Verification
Each consecutive command shall give response with one line output
```
terraform --version && aws --version && eksctl version && kubectl version --short --client && aws-iam-authenticator version
```




