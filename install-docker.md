# How to Install Docker on Ubuntu 22.04 — A Quick Guide

In this tutorial, we will install Docker on Ubuntu 22.04.
Let’s see how to install Docker on Ubuntu 22.04.

I hope that you’ve enabled virtualization on your Windows 10 computer, installed VMware Player, and running Ubuntu on it. 
That’s the beauty of VMware Workstation, you can have multiple operating systems to work and learn with. 
Additionally, the process of booting up a VM is the same, you just need to download the relevant image.

## **1. Update the Software Repository**
All right, let’s update the system in the first place. Get inside the VM and open the terminal. Run the following command:

```bash
sudo apt update
```

It might take a little time to complete the updates.

## **2. Download Tools and Dependencies**

This step is important according to the security point of view. It is recommended to transfer the data and files using apt-transport-https to keep the environment secure.

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

I have already installed the above tools and software packages on the VM.

## **3. Add Docker's GPG Key**

GPG is an excellent method to ensure secure communication between two parties. It protects the package against tampering. GPG relies on a security concept known as public-key encryption. When you add a key with apt-key add, you trust that key to authenticate software. More importantly, this means that you will never get a modified or malicious package.
Add the key with the following command:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Make sure you copy the whole command correctly. Missing anything won’t get us the key.

## **5. Add the Official Docker Repository**
We are going to install Docker’s stable release from its official repo. Therefore, we need to add that repository to our system.

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Update the package manager again.

```bash
sudo apt update
```

## **6. Install Docker on Ubuntu 22.04**

Finally, we are ready to install Docker Community Edition [docker-ce] on our Ubuntu virtual machine. We will install the latest version of Docker from its official repository with the help of the following simple command:

```bash
sudo apt install docker-ce 
```

It’s around 504 MB download. Therefore, depending on the internet connection speed, it may take some time.

Congratulations! We have installed Docker on Ubuntu 22.04.
