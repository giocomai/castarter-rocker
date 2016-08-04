# rocker/rstudio #


## Quickstart

Start an RStudio server container with all pre-installed packages for `castarter`. From the docker window: 

```bash
sudo docker run -d -p 8787:8787 giocomai/castarter-rocker-rstudio
```

Use the `docker-machine ip` to determine the ip address for your local or remote machine command, then visit that address
appended with the port `:8787`.  You can now log in to the session with the default username and password.

- username: rstudio 
- password: rstudio


For customization details, including custom passwords & shared volumes see [Using the Rstudio image](https://github.com/rocker-org/rocker/wiki/Using-the-RStudio-image)

## How to run this on Digital Ocean ##
Here are the instructions to run this Docker on a cloud service such as [Digital Ocean](www.digitalocean.com/?refcode=f29f9a6f7b65). These instructions can easily be adapted for Amazon's EC2 or other services.
First, create a droplet with Docker enabled from the web interface, then login via terminal.
```
ssh root@xxx.xxx.xxx.xxx
```
If docker is installed and running, you can start the rstudio server with:
```bash
docker run -d -p 8787:8787 giocomai/castarter-rocker-rstudio
```
Keep in mind that all files created while the instance is running are temporary and will be deleted as soon as docker is terminated or the host powered off. 

In order to share data between the host and the docker container, one first needs to create a shared folder. Creating a dedicated user might be useful to deal with ownership issues. Running the following commands will create a user (`rstudio`), a folder (`/home/rstudio`), and share it between the host machine and the docker.

```
useradd rstudio
echo 'rstudio:castarter' | chpasswd
mkdir /home/rstudio
chown rstudio:rstudio -R /home/rstudio
```

And then run docker with the following command:

```bash
docker run -p 8787:8787 -v /home/rstudio:/home/rstudio/ giocomai/castarter-rocker-rstudio```
```
The instance will then be reachable via browser at the address `http://xxx.xxx.xxx.xxx:8787`


## Status ##

This docker has been created by forking [rocker-org's rstudio server docker](https://github.com/rocker-org/).

## License ##

The Dockerfiles in this repository are licensed under the GPL 2 or later.

## Trademarks ##

RStudio is a registered trademark of RStudio, Inc.  The use of the trademarked term RStudio and the distribution of the RStudio binaries through the images hosted on [hub.docker.com](https://registry.hub.docker.com/) has been granted by explicit permission of RStudio.  Please review [RStudio's trademark use policy](http://www.rstudio.com/about/trademark/) and address inquiries about further distribution or other questions to [permissions@rstudio.com](emailto:permissions@rstudio.com).
