page_main_title: v6.2.4
main_section: Platform
sub_section: Runtime
sub_sub_section: Machine image
page_title: Description of what is available in Machine Image v6.2.4
page_description: A complete list of language versions, Docker versions, packages and tools available in Machine Image v6.2.4
page_keywords: CI/CD, shippable CI/CD, documentation, shippable, config, yml, AMI, Docker

# Machine image v6.2.4 (Docker TAG v6.2.4)

**Release Date: **

**What is installed on the machine image?**

* Operating System: Ubuntu 16.04.3 LTS
* Kernel Version: 3.13.0-125-generic
* **Docker Server Version: 17.06.0-ce**
* Storage Driver: aufs
* Root Dir: /data/aufs
* Backing Filesystem: extfs
* Dirperm1 Supported: false
* Cgroup Driver: cgroupfs
* Shippable Official Docker Images with TAG: `v6.2.4`

## Shippable Official Docker Images

These are the images used to run your CI jobs. The default image is picked up based on the `language` you set in your yml. All these images are available on our [Docker drydock Hub](https://hub.docker.com/u/drydock/). The source code is available in our [GitHub dry-dock org](https://github.com/dry-dock)

If you would like to use your own CI images in place of the official images, instructions are [described here](/ci/custom-docker-image/)

These are the official language images in this version:

* [Common components](#common-624)
* [Clojure](#clojure-624)
* [Go](#gol-624)
* [Java](#jav-624)
* [Python](#pyt-624)
* [Scala](#sca-624)

<a name="common-624"></a>
### Common components

All language images are built `FROM` a base image that corresponds to the OS version. For example, the language image for Node,js `u16nodall` is built using `u16all` as the base image, and hence has all the packages, CLIs and services installed in the base image.

We have the following base images, one for each supported OS version.

| **OS**       | **Image**             | **Link**                                                                                                | **Packages**                                                                                                                                                                                                                                        | **CLIs**                                                                                                                          | **Services**                                                                                                                                                                                                             |
 |--------------|-----------------------|---------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

 | Ubuntu 16.04 | drydock/u16all:v6.2.4 | - [Docker Hub](https://hub.docker.com/r/drydock/u16all/),<br>- [GitHub](https://github.com/dry-dock/u16all) | - build-essential<br>- curl<br>- gcc<br>- gettext<br>- git<br>- htop<br>- jq<br>- libxml2-dev<br>- libxslt-dev<br>- make<br>- nano<br>- openssh-client<br>- openssl<br>- psmisc<br>- python-dev<br>- python-pip<br>- python-software-properties<br>- software-properties-common<br>- sudo<br>- texinfo<br>- unzip<br>- virtualenv<br>- wget<br>- apt-transport-https 1.2.25 | - awscli 1.11.164<br>- awsebcli 3.11.0<br>- gcloud 173.0.0<br>- jfrog-cli 1.10.1<br>- kubectl 1.8.0<br>- packer 1.1.0<br>- terraform 0.10.0<br>- azure 2.0.25 | - cassandra 3.11<br>- couchdb 2.1.1<br>- elasticsearch 6.1.1<br>- neo4j 3.3.1<br>- memcached 1.5.4<br>- mongodb 3.6.2<br>- mysql 5.7.20<br>- postgres 10<br>- rabbitmq 3.6.14<br>- redis 4.0.8<br>- rethinkdb 2.3.6<br>- riak 2.2.3<br>- selenium 3.8.1<br>- sqllite 3.22.0 |
 | Ubuntu 14.04 | drydock/u14all:v6.2.4 | - [Docker Hub](https://hub.docker.com/r/drydock/u14all/),<br>- [GitHub](https://github.com/dry-dock/u14all) | <br>- build-essential<br>- curl<br>- gcc<br>- gettext<br>- git<br>- htop<br>- jq<br>- libxml2-dev<br>- libxslt-dev<br>- make<br>- nano<br>- openssh-client<br>- openssl<br>- psmisc<br>- python-dev<br>- python-pip<br>- python-software-properties<br>- software-properties-common<br>- sudo<br>- texinfo<br>- unzip<br>- virtualenv<br>- wget | - awscli 1.11.164<br>- awsebcli 3.11.0<br>- gcloud 173.0.0<br>- jfrog-cli 1.10.1<br>- kubectl 1.8.0<br>- packer 1.1.0<br>- terraform 0.10.0<br>- azure 2.0.25 | - cassandra 3.11.2<br>- couchdb 2.1.1<br>- elasticsearch 6.1.1<br>- neo4j 3.3.1<br>- memcached 1.5.4<br>- mongodb 3.6.2<br>- mysql 5.7.20<br>- postgres 10.1<br>- rabbitmq 3.6.14<br>- redis 4.0.7<br>- rethinkdb 2.3.6<br>- riak 2.2.3<br>- selenium 3.8.1<br>- sqllite 3.22.0 |
 | Ubuntu 16.04 | drydockaarch64/u16:master | - [Docker Hub](https://hub.docker.com/r/drydockaarch64/u16/),<br>- [GitHub](https://github.com/dry-dock-aarch64/u16) | - build-essential<br>- curl<br>- gcc<br>- gettext<br>- git<br>- htop<br>- jq<br>- libxml2-dev<br>- libxslt-dev<br>- make<br>- nano<br>- openssh-client<br>- openssl<br>- psmisc<br>- python-dev<br>- python-pip<br>- python-software-properties<br>- software-properties-common<br>- sudo<br>- texinfo<br>- unzip<br>- virtualenv<br>- wget | - awscli 1.11.91<br>- awsebcli 3.9.0<br>- gcloud 160.0.0<br>- kubectl 1.5.1<br>- packer 1.2.0<br>- azure 2.0.0rc5 | |
 | CentOs 7 | drydock/c7:master | - [Docker Hub](https://hub.docker.com/r/drydock/c7/),<br>- [GitHub](https://github.com/dry-dock/c7) | - epel-release<br>- gcc<br>- gcc-c++<br>- kernel-devel<br>- make<br>- curl<br>- openssl<br>- wget<br>- nano<br>- unzip<br>- nano<br>- openssh-clients<br>- libxslt1-dev<br>- libxml2-dev<br>- htop<br>- rsync<br>- vim<br>- glibc.i686<br>- libgcc_s.so.1<br>- python35u<br>- python35u-libs<br>- python35u-devel<br>- python35u-pip<br>- virtualenv<br>- jq<br>- git<br>- git-lfs | - awscli 1.14.41<br>- gcloud 189.0.0<br>- kubectl 1.8.8<br>- doctl 1.7.0<br>- jfrog-cli 1.7.0<br>- ansible 2.3.0<br>- boto 2.46.1<br>- apache libcloud 2.0.0<br>- terraform 0.11.3<br>- packer 1.2.0<br>- azure 2.0.27 | |

---

<a name="clo-624"></a>
### Clojure

| OS           | Image                    | Link                                                                                                          | Language versions                          | Additional packages                                                           |
|--------------|--------------------------|---------------------------------------------------------------------------------------------------------------|--------------------------------------------|-------------------------------------------------------------------------------|
| Ubuntu 14.04 | drydock/u14cloall:v6.2.4 | - [Docker Hub](https://hub.docker.com/r/drydock/u14cloall/),<br>- [GitHub](https://github.com/dry-dock/u14cloall) | - 1.3.0<br>- 1.4.0<br>- 1.5.1<br>- 1.6.0<br>- 1.7.0<br>- 1.8.0<br>- 1.9.0 | - [Common components](#common-614)<br>- leiningen<br>- Java 1.8<br>- Node 7.x<br>- Ruby 2.3.3 |

---

<a name="gol-624"></a>
### Go

 | OS   | Image  | Link   | Language versions  | Additional packages   |
 |------|--------|--------|--------------------|-----------------------|
 | Ubuntu 14.04 | drydock/u14golall:v6.2.4 | - [Docker Hub](https://hub.docker.com/r/drydock/u14golall/)<br>- [Github](https://github.com/dry-dock/u14golall) | - 1.7.6<br>- 1.8.5<br>- 1.9.2    | - [Common components](#common-624)<br>- gvm 1.0.22<br>- Java 1.8.10<br>- Node 4.8.7<br>- Ruby 2.3.3 |

---


<a name="jav-624"></a>
### Java

 | OS           | Image                    | Link                                                                                                          | Language versions                                      | Additional packages                                         |
 |--------------|--------------------------|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------|
 | Ubuntu 14.04 | drydock/u14javall:v6.2.4 | - [Docker Hub](https://hub.docker.com/r/drydock/u14javall/)<br>- [Github](https://github.com/dry-dock/u14javall) | - openjdk7<br>- openjdk8<br>- openjdk9<br>- oraclejdk8<br>- oraclejdk9           | - [Common components](#common-624)<br>- Node 4.8.7<br>- Ruby 2.3.3 <br>- Gradle 4.2.1 <br>- Android-sdk 26.0.1 (to be used with openjdk8/oraclejdk8) |

---

<a name="pyt-624"></a>
### Python

 | OS           | Image                    | Link                                                                                                      | Language versions                                       | Additional packages                                                                 |
 |--------------|--------------------------|-----------------------------------------------------------------------------------------------------------|---------------------------------------------------------|-------------------------------------------------------------------------------------|
 | Ubuntu 14.04 | drydock/u14pytall:v6.2.4 | - [Docker Hub](https://hub.docker.com/r/drydock/u14pytall/)<br>- [Github](https://github.com/dry-dock/u14pytall)  | - 2.7.12<br>- 3.4.3<br>- 3.5.5<br>- 3.6.4<br>- pypy2 5.10.0<br>- pypy3 5.10.1 | - [Common components](#common-624)<br>- virtualenv<br>- Java 1.8.0<br>- Node 4.8.7<br>- Ruby 2.3.3  |

---

<a name="sca-624"></a>
### Scala

 | OS           | Image                    | Link                                                                                                          | Language versions                | Additional packages                                                          |
 |--------------|--------------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------|------------------------------------------------------------------------------|
 | Ubuntu 14.04 | drydock/u14scaall:v6.2.4 | - [Docker Hub](https://hub.docker.com/r/drydock/u14scaall/),<br>- [GitHub](https://github.com/dry-dock/u14scaall) | - 2.9.3<br>- 2.10.7<br>- 2.11.12<br>- 2.12.4 | - [Common components](#common-624)<br>- sbt<br>- Java 1.8.0<br>- Node 4.8.7<br>- Ruby 2.3.3  |

---