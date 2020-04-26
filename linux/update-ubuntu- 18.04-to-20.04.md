# Upgrade ubuntu 18.04 - 20.04

- Ubuntu have developed their own automatic way of upgrading between releases (it essentially scripts the traditional Debian approach)
- The upgrade from 18.04 LTS isn't available yet (04/26/2020)
- I am pretty sure that there is an alternative way of doing this that is more safe. I am beginner in linux world, so face this as an exploration experience

### My approach

I've created an clean VM with ubuntu 18.04 LTS desktop version (default installation) in order to test an forced upgrade. This allows me to test without compromising my OS (especially because I am running this test on my work computer)

Actually, I've followed the steps of an very well written article. I will leave the link in the references part.

### Steps

1. Cehck our Ubuntu version

```bash
 $ lsb_release -a
 
# No LSB modules are available.
# Distributor ID:	Ubuntu
# Description:	Ubuntu 18.04.4 LTS
# Release:	18.04
# Codename:	bionic
``` 

2. Install the update manager package

```bash
$ sudo apt install update-manager-core
```

3. Upgrade

```bash
$ sudo do-release-upgrade
```
- I had the exactly issue that  the article said ("No new release found"). The article also pointed that the first recommended approach is to simply wait, but I am running on a clean VM, so lets test the -d flag

4. Force upgrade

```bash
$ sudo do-release-upgrade -d
```
5. Wait

- It took almost 30 minutes to finish and the Ubuntu asked me a couple of questions about how I want to handle the upgrade (i've chosen  default values for everything)

### Notes

- I had no problems at all 
- Ubuntu has been upgraded smoothly (i was running on a very clean VM)

### References
[Article 1](https://linuxconfig.org/how-to-upgrade-ubuntu-to-20-04-lts-focal-fossa) <br/>
[Article 2](https://www.cyberciti.biz/faq/upgrade-ubuntu-18-04-to-20-04-lts-using-command-line/)
