#### To use custom ports list 
1. clone https://github.com/freebsd/freebsd-ports to a /work/ports/fourierportsrepo directory
2. poudriere ports -c -F -f none -M /work/ports/fourierportsrepo -p fourierportsrepo
3. poudriere ports -l //to view all port repos

#### To use  multiple make threads
* change ALLOW_MAKE_JOBS to "yes" in /usr/local/etc/poudriere.conf

#### To solve max file limit reached while building vscode
* Add MAX_FILES_vscode=4096 to poudriere.conf

* add @all to end of a port in port-list to build all flavours like 
"devel/py-pip@all"


#### Build poudriere Command:
sudo poudriere bulk -J 32 -j freebsd_12-1x64 -p fourierportsrepo -f /usr/local/etc/poudriere.d/port-list

#### Miscellaneous Information
* RepoName as of 16/05/2020 in /usr/local/etc/pkg/repos/poudriere.conf
freebsd_12-1x64-fourierportsrepo


* Paths:
Ports Path: 	/root/Documents/Robin/portrepo/ports/fourierportsrepo

* distfiles Path: /root/Documents/Robin/portrepo/ports/fourierportsrepo/distfiles

* poudriere.conf
path for build: /usr/local/etc/poudriere.conf

* poudriere.conf
path for adding remote repository: /usr/local/etc/pkg/repos/poudriere.conf

* ports-list path: /usr/local/etc/poudriere.d/port-list

* packages path: /usr/local/poudriere/data/packages/freebsd_12-1x64-fourierportsrepo


* To create distinfo for a new port:
make makesum

* To create plist for a new port:
make makeplist


