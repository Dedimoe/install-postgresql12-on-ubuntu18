# install-postgresql12-on-ubuntu18
install-postgresql12-on-ubuntu18

### 1. Prepare
```
sudo apt-get -y install bash-completion wget
```

### 2. Add the GPGkey & Postgresql12 repo
```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" |sudo tee  /etc/apt/sources.list.d/pgdg.list
```

The repo added contains :
```
postgresql-client
postgresql
libpq-dev
postgresql-server-dev
pgadmin packages
```

### 3. Update the APT repo index & install the packages
```
sudo apt-get update
sudo apt-get -y install postgresql-12 postgresql-client-12
```

### 4. Check that the Postgresql service is up and running
```
sudo systemctl status postgresql
```
The output below:
```
linux@user:~$ sudo systemctl status postgresql
● postgresql.service - PostgreSQL RDBMS
   Loaded: loaded (/lib/systemd/system/postgresql.service; enabled; vendor preset: enabled)
   Active: active (exited) since Sat 2020-07-11 02:33:52 UTC; 22s ago
 Main PID: 8290 (code=exited, status=0/SUCCESS)
    Tasks: 0 (limit: 1151)
   CGroup: /system.slice/postgresql.service

Jul 11 02:33:52 oracle-temankerja-node-dev systemd[1]: Starting PostgreSQL RDBMS...
Jul 11 02:33:52 oracle-temankerja-node-dev systemd[1]: Started PostgreSQL RDBMS.
linux@user:~$
```
### 5. Access to postgresql client
Now You can run ```sudo su postgres``` to change to the postgres system user and access the Postgresql client: 
```
sudo su - postgres
psql
```
And You should get the output shown below
```
postgres@linux:~$ psql
psql (12.3 (Ubuntu 12.3-1.pgdg18.04+1))
Type "help" for help.

postgres=#
```
