# container_scans
Information regarding tools and configurations to carry out Docker container scans

#### Install Red Hat's OpenScap scanner via a container

```
sudo atomic install registry.access.redhat.com/rhel7/openscap
```
For disconnected environments you can mirror RH's oval definitions and point your OpenScap scanner to your internal mirror.

***[URL]***
```
https://www.redhat.com/security/data/oval/
```

***[OpenScap configuration - Atomic Host]***
```
/etc/oscapd/config.ini
```

```
[CVEScanner]
fetch-cve = yes # change to yes
#fetch-cve-url = https://www.redhat.com/security/data/oval/
fetch-cve-url = http://<internal_mirror.com>/oscap_oval-oscap_oval/ # set to internal repository
fetch-cve-timeout = 600
```
Results after running an atomic scan on a Docker image

![scan image](/images/atomic_scan_image.jpg)
