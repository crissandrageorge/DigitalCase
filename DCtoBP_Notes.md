# Notes on the DigitalCase to BePress Migration

- Contacted BePress to see if they will help
- contact discovery garden and see if they will help
- deduplication of some records needs to happen
- weird double-indexing occuring on some of the records
- need to have urls with a path to the pdf on a local server to then put into an excel format
- OIS file within Islandora does seem to have a path, but I am not sure that this leads to a local server
- file path is: /tmp/ksl-2006070176.PDF.pdf
- cd /var/tmp is a directory on the ingest server
## Found in this directory

```
$ pwd
/var/tmp
$ ls -l
total 20
drwxrwxrwt 2 root root 4096 May 11 18:31 cloud-init
drwx------ 3 root root 4096 May 11 18:31 systemd-private-5b99f153f3d94a6881017ddb79b89ed2-nagios-nrpe-server.service-AfAtXg
drwx------ 3 root root 4096 May 11 18:31 systemd-private-5b99f153f3d94a6881017ddb79b89ed2-systemd-logind.service-Pmrfxg
drwx------ 3 root root 4096 May 11 18:31 systemd-private-5b99f153f3d94a6881017ddb79b89ed2-systemd-resolved.service-nTtIgh
drwx------ 3 root root 4096 May 11 18:31 systemd-private-5b99f153f3d94a6881017ddb79b89ed2-systemd-timesyncd.service-GdYymh
```

> when trying other locations, I was unable to find any area on local servers with the links I had seen on Islandora. This must be something that Discovery 
Garden has access to, but not DC. 

