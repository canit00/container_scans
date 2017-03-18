# container_scans
Information regarding tools and configurations to carry out Docker container scans

#### Install Red Hat's OpenScap scanner via a container

```
sudo atomic install registry.access.redhat.com/rhel7/openscap
```
For disconnected environments you can mirror RH's oval definitions and point your OpenScap scanner to your internal mirror.

***URL***
```
https://www.redhat.com/security/data/oval/
```

***configuration***
```
/etc/oscapd/config.ini
```

```
[General]
tasks-dir = /var/lib/oscapd/tasks
results-dir = /var/lib/oscapd/results
work-in-progress-dir = /var/lib/oscapd/work_in_progress
cve-feeds-dir = /var/lib/oscapd/cve_feeds
jobs = 4

[Tools]
oscap = /usr/bin/oscap
oscap-ssh = /usr/bin/oscap-ssh
oscap-vm = /usr/bin/oscap-vm
oscap-docker = /usr/bin/oscap-docker
oscap-chroot = /usr/bin/oscap-chroot
container-support = yes

[Content]
cpe-oval = /usr/share/openscap/cpe/openscap-cpe-oval.xml
ssg = /usr/share/xml/scap/ssg/content

[CVEScanner]
fetch-cve = yes
#fetch-cve-url = https://www.redhat.com/security/data/oval/
fetch-cve-url = http://<internal_mirror.com/oscap_oval-oscap_oval/
fetch-cve-timeout = 600
```
