# Oracle Pluggable Database (PDB) Management — Assignment II

## 📌 Overview

This repository documents the completion of **Individual Assignment II: Oracle Pluggable Databases (PDB) Management** for the course *Database Development with PL/SQL (INSY 8311)*.

The assignment covers four tasks:
1. Creating a new Pluggable Database (PDB) and a user inside it
2. Creating and deleting a temporary PDB
3. Verifying the environment through Oracle Enterprise Manager (OEM) Database Express
4. Documenting the process professionally in this repository

All tasks were performed individually using Oracle Database 21c Express Edition (XE).

---

## 🖥️ Oracle Environment Used

| Item | Detail |
|---|---|
| Database Edition | Oracle Database 21c Express Edition (XE) |
| Version | 21.3.0.0.0 |
| Platform | Microsoft Windows x86 64-bit |
| Tool | Oracle SQL Developer |
| Container Database (CDB) | XE |
| Management Console | Oracle Enterprise Manager Database Express (OEM) |

---

## ✅ Task 1: Create a New Pluggable Database

**Naming convention used:**
- PDB Name: `HO_PDB_29683`
- Username inside PDB: `honore_plsqlauca_29683`

**What was done:**
- Connected to the container database as `sys` with `SYSDBA` privileges
- Created the pluggable database `HO_PDB_29683` using `CREATE PLUGGABLE DATABASE`
- Opened the PDB and saved its state so it opens automatically on future restarts
- Created a dedicated user `honore_plsqlauca_29683` inside the PDB with `CONNECT`, `RESOURCE`, and `DBA` privileges and an unlimited quota on the `USERS` tablespace
- This user account will be reused for all future coursework in this PDB

**Evidence:** see `screenshots/task1_pdb_created.png`, `screenshots/task1_user_created.png`

---

## ✅ Task 2: Create and Delete a PDB

**Naming convention used:**
- Temporary PDB Name: `HO_TO_DELETE_PDB_29683`

**What was done:**
- Created a temporary pluggable database `HO_TO_DELETE_PDB_29683`
- Opened it and verified its existence using `SHOW PDBS`
- Closed the PDB and dropped it completely using `DROP PLUGGABLE DATABASE ... INCLUDING DATAFILES`
- Re-ran `SHOW PDBS` to confirm the temporary PDB no longer exists, while `HO_PDB_29683` (from Task 1) remains untouched

**Evidence:** see `screenshots/task2_pdb_created.png`, `screenshots/task2_pdb_verified.png`, `screenshots/task2_pdb_deleted.png`

---

## ✅ Task 3: Oracle Enterprise Manager (OEM)

**What was done:**
- Accessed OEM Database Express at `https://localhost:5500/em`
- Logged in with SYSDBA privileges to view the full CDB dashboard
- Verified the dashboard reflects the current environment: **CDB (2 PDB(s))** — `HO_PDB_29683` and `XEPDB1` — confirming that `HO_TO_DELETE_PDB_29683` was successfully removed
- Confirmed database status, uptime, resource usage, and container information on the dashboard

**Evidence:** see `screenshots/task3_oem_dashboard.png`

---

## 🧩 Challenges Faced and How They Were Solved

- **OEM Express login failures with the PDB-level user:** Initially attempted to log in to OEM Express using the `honore_plsqlauca_29683` account with `HO_PDB_29683` as the Container Name, but repeatedly received "Invalid Database Credentials," even after resetting the password with `ALTER USER ... IDENTIFIED BY`. This was resolved by instead logging in as `sys` with `SYSDBA` privileges (leaving/using `CDB$ROOT` as the container), which authenticated successfully and provided full visibility into the CDB and both PDBs.
- **Password change not taking effect:** An `ALTER USER` statement was initially only selected/highlighted in SQL Developer rather than executed. Running it explicitly with **Ctrl+Enter** and confirming the `User altered.` message in the Script Output resolved this.

---

## 🔒 Integrity Statement

I, NAYIHIKI Nshuti Honore (Student ID: 29683), confirm that all tasks in this assignment were completed individually, without copying from classmates, and that all screenshots and outputs included in this repository are my own work performed on my own Oracle environment.

---

## 📤 Submission Details

| Field | Detail |
|---|---|
| Full Name | NAYIHIKI Nshuti Honore |
| Student ID | 29683 |
| Course | Database Development with PL/SQL (INSY 8311) |
| Group | C |
| Instructor | Eric Maniraguha |
| Teaching Assistant | Afanyu Emmanuel |
| GitHub Repository (Public) | `oracle_pdb_ass_II_29683_honore` |
| Repository Link | https://github.com/Nshutihonore/oracle_pdb_ass_II_29683_honore |
| Submission Date | September 22, 2026 |

---

*"Excellence is never an accident; it is the result of discipline, commitment, and integrity."*