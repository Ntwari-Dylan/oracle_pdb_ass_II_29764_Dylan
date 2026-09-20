# Oracle PDB Assignment II

## Student Information

**Name:** Dylan
**Student ID:** 29764
**Course:** Database Development with PL/SQL (INSY 8311)
**Assignment:** Individual Assignment II – Oracle Pluggable Databases (PDB) Management

## Overview

This assignment was about working with Oracle Pluggable Databases (PDBs). I worked on creating a PDB, creating and deleting a temporary PDB, and setting up Oracle Enterprise Manager (EM Express).

I also documented the work using screenshots and organized the evidence in this GitHub repository.

## Oracle Environment

* **Oracle Database:** 21c Enterprise Edition
* **EM Express HTTPS Port:** 5500
* **Main PDB:** `dy_pdb_29764`
* **Main PDB User:** `dylan_plsqlauca_29764`
* **Temporary PDB:** `dy_to_delete_pdb_29764`

## Task 1 – Create a New PDB

For Task 1, I created the PDB named `dy_pdb_29764`.

After creating it, I opened the PDB and checked its status to make sure it was in **READ WRITE** mode. I also switched into the PDB and verified the user `DYLAN_PLSQLAUCA_29764`.

This was my first task with PDBs, so I had to understand how the CDB and PDB containers work and how to switch between them.

The screenshots for this task are included in the repository.

## Task 2 – Create and Delete a PDB

For Task 2, I created a temporary PDB called `dy_to_delete_pdb_29764`.

I checked that the PDB was created successfully. After that, I deleted it completely using the required command:

```sql
DROP PLUGGABLE DATABASE dy_to_delete_pdb_29764 INCLUDING DATAFILES;
```

Finally, I checked the PDB list again to confirm that the temporary PDB was no longer there.

Task 2 was easier for me after completing Task 1 because I already understood the basic PDB commands and how to check the PDB status.

The screenshots for the creation, checking, and deletion of the temporary PDB are included in the repository.

## Task 3 – Oracle Enterprise Manager (OEM)

For Task 3, I configured Oracle Enterprise Manager Database Express.

The EM Express HTTPS port was **5500**, so I accessed it through:

`https://localhost:5500/em`

At first, I had some problems logging in. I was mixing up the container name during the login, and the login page kept rejecting or refreshing the login.

I checked the EM Express configuration and found that the global EM Express port was not enabled. I enabled it and also made sure that the required EM Express role was available to the `SYSTEM` user.

After fixing the configuration and using the correct container name, I was able to log in successfully using:

* **Username:** SYSTEM
* **Container Name:** DY_PDB_29764

The OEM dashboard then opened and showed my Oracle environment and the PDB `DY_PDB_29764`.

A screenshot of the working OEM dashboard is included in the `oem_dashboard` folder.

## Challenges Faced

The main challenge for me was Task 3. The OEM login did not work at first because I was using the wrong container name and I also had to check the EM Express configuration.

I spent some time troubleshooting the login and checking the EM Express settings. After enabling the global EM Express port and using the correct PDB container name, the login worked and I was able to access the dashboard.

Task 1 also required some learning because I was still getting familiar with PDBs, containers, and the commands used to create and open a PDB.

## Evidence

The screenshots are organized into the following folders:

* `pdb_creation/` – evidence for PDB creation
* `pdb_deletion/` – evidence for creating and deleting the temporary PDB
* `oem_dashboard/` – OEM dashboard screenshot
* `screenshots/` – additional screenshots/evidence

## Integrity Statement

I confirm that this assignment represents my own work and that I performed the Oracle tasks myself. The screenshots in this repository are from my own Oracle environment.

## Submission Details

**Issues Encountered:** Yes
**PDB Name Created:** `dy_pdb_29764`
**Repository Link:** [Paste your GitHub repository link here]

## Conclusion

All four tasks were completed. I created and managed the PDB, created and deleted the temporary PDB, configured and accessed Oracle Enterprise Manager, and documented the work in this GitHub repository.
