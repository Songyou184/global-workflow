GFS V16.2.2 RELEASE NOTES

-------
PRELUDE
-------

The upstream dependency system RTOFS is upgraded to v2.3. This results in a version file change within the GFS.

IMPLEMENTATION INSTRUCTIONS
---------------------------

The NOAA VLab and both the NOAA-EMC and NCAR organization spaces on GitHub.com are used to manage the GFS.v16.2.2 code. The SPA(s) handling the GFS.v16.2.2 implementation need to have permissions to clone VLab gerrit repositories and the private NCAR UPP_GTG repository. All NOAA-EMC organization repositories are publicly readable and do not require access permissions. Please follow the following steps to install the package on WCOSS2:

```bash
cd $PACKAGEROOT
mkdir gfs.v16.2.2
cd gfs.v16.2.2
git clone -b EMC-v16.2.2 https://github.com/NOAA-EMC/global-workflow.git .
cd sorc
./checkout.sh -o
```

The checkout script extracts the following GFS components:

| Component | Tag         | POC               |
| --------- | ----------- | ----------------- |
| MODEL     | GFS.v16.2.0   | Jun.Wang@noaa.gov |
| GSI       | gfsda.v16.2.0 | Russ.Treadon@noaa.gov |
| GLDAS     | gldas_gfsv16_release.v.2.0.0 | Helin.Wei@noaa.gov |
| UFS_UTILS | ops-gfsv16.2.0 | George.Gayno@noaa.gov |
| POST      | upp_v8.1.2 | Wen.Meng@noaa.gov |
| WAFS      | gfs_wafs.v6.2.8 | Yali.Mao@noaa.gov |

To build all the GFS components, execute:
```bash
./build_all.sh
```
The `build_all.sh` script compiles all GFS components. Runtime output from the build for each package is written to log files in directory logs. To build an individual program, for instance, gsi, use `build_gsi.sh`.

Next, link the executables, fix files, parm files etc in their final respective locations by executing:
```bash
./link_fv3gfs.sh nco wcoss2
```

Lastly, link the ecf scripts by moving back up to the ecf folder and executing:
```bash
cd ../ecf
./setup_ecf_links.sh
```

SORC CHANGES
------------

* No changes from GFS v16.2.1

FIX CHANGES
-----------

* No changes from GFS v16.2.1

PARM/CONFIG CHANGES
-------------------

* No changes from GFS v16.2.1

JOBS CHANGES
------------

* No changes from GFS v16.2.1

SCRIPT CHANGES
--------------

* No changes from GFS v16.2.1

MODULE CHANGES
--------------

* No changes from GFS v16.2.1

VERSION CHANGES
---------------

The "rtofs_ver" version variable changes from v2.2. to v2.3.

CHANGES TO RESOURCES AND FILE SIZES
-----------------------------------

* File sizes
  * No change to GFSv16.2.1
* Resource changes
  * No change to GFSv16.2.1

PRE-IMPLEMENTATION TESTING REQUIREMENTS
---------------------------------------

* Which production jobs should be tested as part of this implementation?
  * The entire GFS v16.2.2 package needs to be installed and tested.
* Does this change require a 30-day evaluation?
  * No.

DISSEMINATION INFORMATION
-------------------------

* Where should this output be sent?
  * No change from GFS v16.2.1
* Who are the users?
  * No change from GFS v16.2.1
* Which output files should be transferred from PROD WCOSS2 to DEV WCOSS2?
  * No change from GFS v16.2.1
* Directory changes
  * No change from GFS v16.2.1
* File changes
  * No change from GFS v16.2.1

HPSS ARCHIVE
------------

* No change from GFS v16.2.1

JOB DEPENDENCIES AND FLOW DIAGRAM
---------------------------------
* No change from GFS v16.2.1