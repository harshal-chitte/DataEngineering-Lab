# Ubuntu Development VM Setup Notes

## Environment Overview

Purpose:

* Create a personal development environment for Python, SQL, PostgreSQL, GitHub, and Data Engineering learning.
* Access all tools through a web browser.
* Store code, notes, and projects in GitHub.

---

## Hardware

Host Machine:

* Intel i5
* 24 GB RAM
* Windows

Virtualization:

* VirtualBox

Guest OS:

* Ubuntu Server 24.04 LTS

---

## Network Configuration

Initially:

* NAT Adapter
* IP: 10.0.2.15
* SSH access from Windows failed.

Solution:

* Changed VirtualBox Network Adapter to Bridged Adapter.
* VM received LAN IP address.

Current Access:

SSH:
ssh harshal@192.168.0.110

Browser:
https://192.168.0.110:8080

pgAdmin:
http://192.168.0.110/pgadmin4

---

## Linux User

Username:
harshal

Home Directory:
/home/harshal

---

## Installed Software

### Python

Version:
Python 3.12.3

Verification:
python3 --version

---

### Java

Version:
OpenJDK 17.0.19

Verification:
java -version

---

### Git

Version:
Git 2.43.0

Verification:
git --version

---

### PostgreSQL

Version:
PostgreSQL 16.14

Verification:
psql --version

---

## PostgreSQL Configuration

Created User:

CREATE USER harshal WITH PASSWORD '******';

Granted Permission:

ALTER USER harshal CREATEDB;

Created Database:

CREATE DATABASE practice_db OWNER harshal;

Database:
practice_db

Owner:
harshal

---

## Timezone Configuration

Ubuntu Timezone:

sudo timedatectl set-timezone Asia/Kolkata

Verification:

timedatectl

Result:

* Asia/Kolkata
* NTP Enabled
* System Clock Synchronized

---

## PostgreSQL Timezone

Configured Globally:

ALTER SYSTEM SET timezone='Asia/Kolkata';

Verification:

SHOW timezone;

Result:

Asia/Kolkata

---

## GitHub Integration

SSH Key Generated:

ssh-keygen -t ed25519

Public Key Added To:
GitHub → Settings → SSH and GPG Keys

Verification:

ssh -T [git@github.com](mailto:git@github.com)

Result:

Hi harshal-chitte! You've successfully authenticated.

---

## Development Workspace

Root Folder:

/home/harshal/DataEngineering-Lab

Folders:

DataEngineering-Lab/
├── Notes
├── Python
├── SQL
├── PostgreSQL
├── Projects
└── Git

---

## code-server (VS Code Web)

Installed:
code-server 4.123.0

Configuration:

bind-addr: 0.0.0.0:8080

Access:

https://192.168.0.110:8080

Installed Extensions:

* Python
* Python Debugger
* Python Environments
* Jupyter
* PostgreSQL
* PgStudio

---

## pgAdmin

Installed:
pgAdmin4 Web

Access:

http://192.168.0.110/pgadmin4

Configured Server:

Name:
Local PostgreSQL

Host:
127.0.0.1

Port:
5432

Database:
practice_db

User:
harshal

---

## Service Management Script

Location:

~/scripts/labctl.sh

Commands:

labstart
labstop
labrestart
labstatus

Managed Services:

* PostgreSQL
* Apache
* code-server

---

## Current Development Stack

Operating System:
Ubuntu Server 24.04

Programming:
Python 3.12

Database:
PostgreSQL 16

IDE:
code-server

Database GUI:
pgAdmin4

Version Control:
Git + GitHub

Runtime:
Java 17

---

## Future Roadmap

Phase 1:

* Linux
* Git
* Python
* PostgreSQL
* SQL
* Jupyter

Phase 2:

* Pandas
* ETL Development
* Python Automation

Phase 3:

* Apache Airflow

Phase 4:

* Apache Spark

Not Planned Currently:

* Hive
* Trino
* Iceberg
* Docker

---

## Lessons Learned

1. Bridged networking is required for direct SSH access.
2. SSH host key errors can occur after VM reinstallation.
3. PostgreSQL timezone should match system timezone.
4. code-server provides a complete browser-based development environment.
5. pgAdmin is more reliable than VS Code PostgreSQL extensions in browser-based environments.
6. GitHub SSH authentication is preferable to password authentication.

