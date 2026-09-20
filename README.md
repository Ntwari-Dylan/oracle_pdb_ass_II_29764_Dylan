# Oracle PDB Assignment II

## Student Information

**Name:** Ishimwe Ntwari Dylan  
**Student ID:** 29764  
**Course:** Database Development with PL/SQL (INSY 8311)  
**Assignment:** Individual Assignment II – Oracle Pluggable Databases (PDB) Management

---

## Overview

This assignment was about working with Oracle Pluggable Databases (PDBs) using Oracle Database.

During the assignment, I worked on:

- Creating a new PDB
- Creating and deleting a temporary PDB
- Creating a user inside the PDB
- Checking the PDB status
- Setting up Oracle Enterprise Manager (EM Express)
- Troubleshooting the OEM login
- Documenting the work using screenshots
- Organizing the evidence in a public GitHub repository

---

## Oracle Environment

- **Oracle Database:** 21c Enterprise Edition
- **Main PDB:** `dy_pdb_29764`
- **Main PDB User:** `dylan_plsqlauca_29764`
- **Temporary PDB:** `dy_to_delete_pdb_29764`
- **EM Express HTTPS Port:** `5500`
- **EM Express URL:** `https://localhost:5500/em`

---

# Task 1 – Create a New PDB

For Task 1, I created my main Pluggable Database using the required naming format.

### PDB Created

```text
dy_pdb_29764
```

After creating the PDB, I opened it and checked that it was in **READ WRITE** mode.

I then switched into the PDB and checked the user created inside it.

### User Created

```text
DYLAN_PLSQLAUCA_29764
```

The user was successfully created inside my PDB and verified after switching to the PDB.

This was my first time working with PDBs in this assignment, so I had to learn how the CDB and PDB containers work and how to move between them.

### Task 1 Result

The main PDB was successfully created, opened, and verified.

I have **3 screenshots** for Task 1 as evidence.

The screenshots are stored in:

```text
pdb_creation/
```

---

# Task 2 – Create and Delete a PDB

For Task 2, I created another PDB that was only used for testing the creation and deletion process.

### Temporary PDB

```text
dy_to_delete_pdb_29764
```

First, I created the temporary PDB and checked that it existed.

After confirming that it was created successfully, I deleted it using:

```sql
DROP PLUGGABLE DATABASE dy_to_delete_pdb_29764 INCLUDING DATAFILES;
```

After deleting it, I checked the PDB list again to confirm that the temporary PDB was no longer present.

### Task 2 Result

The temporary PDB was successfully:

1. Created
2. Verified
3. Deleted
4. Confirmed as no longer existing

Task 2 was easier for me after completing Task 1 because I already understood the basic PDB commands and how to check the PDB status.

I have **4 screenshots** for Task 2 as evidence.

The screenshots are stored in:

```text
pdb_deletion/
```

---

# Task 3 – Oracle Enterprise Manager (OEM)

For Task 3, I configured **Oracle Enterprise Manager Database Express (EM Express)**.

First, I checked the HTTPS port using:

```sql
SELECT DBMS_XDB_CONFIG.GETHTTPSPORT() FROM DUAL;
```

The result was:

```text
5500
```

I then opened EM Express using:

```text
https://localhost:5500/em
```

At first, Chrome showed a certificate warning. I continued to the localhost page and the Oracle Enterprise Manager login page appeared.

---

## OEM Login Problem

Task 3 was the hardest part for me.

At first, I tried logging in with `SYS`, but the login kept being refreshed.

I also had a problem with the **container name** because I was mixing up the container name during the login.

I checked the EM Express configuration and found that the global EM Express port was disabled.

I enabled it using:

```sql
EXEC DBMS_XDB_CONFIG.SETGLOBALPORTENABLED(TRUE);
```

I also checked the available EM Express roles:

```text
EM_EXPRESS_ALL
EM_EXPRESS_BASIC
```

The `SYSTEM` user did not originally have the EM Express role, so I granted:

```sql
GRANT EM_EXPRESS_BASIC TO SYSTEM;
```

I also verified that the `SYSTEM` user already had the DBA role.

During the troubleshooting, the `SYS` account had also been locked because of failed login attempts, so I unlocked it with:

```sql
ALTER USER SYS ACCOUNT UNLOCK;
```

I then verified the SYS password using:

```sql
CONNECT SYS AS SYSDBA
```

After fixing the configuration and using the correct container name, I was finally able to log in successfully.

---

## Successful OEM Login

**Username:**

```text
DYLAN_PLSQLAUCA_29764
```

**Container Name:**

```text
DY_PDB_29764
```

The OEM dashboard successfully opened and showed:

```text
ORCL / DY_PDB_29764 (21.3.0.0.0)
```

This confirmed that EM Express was working with my PDB.

### Task 3 Result

The OEM dashboard was successfully accessed and verified.

I have **1 screenshot** showing the working OEM dashboard.

The screenshot is stored in:

```text
oem_dashboard/
```



# Challenges Faced

The biggest challenge I faced was Task 3.

The OEM login took some time because I was mixing up the container name. The login page kept rejecting the login, so I had to check different parts of the EM Express configuration.

I found that the global EM Express port was not enabled, and the `SYSTEM` user also needed the EM Express role.

After enabling the global port, granting the required role, and using the correct container name, I was finally able to log in and see the OEM dashboard.

Task 1 also required some learning because I was still getting familiar with Oracle PDBs, CDBs, containers, and the commands used to create and open a PDB.

Task 2 became easier because I had already understood the basic PDB operations from Task 1.



