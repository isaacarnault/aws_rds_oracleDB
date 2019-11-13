[![1-BFTWWQO8gd-Rb6ah-N0-Gdbp-A.png](https://i.postimg.cc/Y9dgZrYk/1-BFTWWQO8gd-Rb6ah-N0-Gdbp-A.png)](https://postimg.cc/34DdDHtb)
  
# Starting with Oracle DB on AWS and Oracle SQL developer remotely

[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)

### What you need to complete this installation

This gist was made on a `Ubuntu 18.04 LTS`.

<b>A. Default OpenJDK - installed on your local machine</b><br>

<b>B. Oracle SQL Developer - Linux RPM installed on your local machine</b><br>

<b>C. Oracle DB instance hosted on AWS using RDS</b><br>

<b>D. Remote connection to your DB using Oracle SQL Developer</b><br>

<hr>

### A. Install the Default OpenJDK

```r
$ sudo apt-get update
$ sudo apt install default-jdk
$ java -version
```

<details>
<summary>🔴 See command</summary>
<p>
  
[![java.png](https://i.postimg.cc/G3NdQWVy/java.png)](https://postimg.cc/MXyCZFW6)

</p>
</details>

<hr>

### B. Install Oracle SQL Developer - Linux RPM

Go to https://www.oracle.com/database/technologies/appdev/sql-developer.html > download<br>

To `Linux RPM` click on Download.

<details>
<summary>🔴 See command</summary>
<p>
  
[![linux-rpm.png](https://i.postimg.cc/44KmsQTp/linux-rpm.png)](https://postimg.cc/c6SscYCJ)

</p>
</details>

Open your Terminal, create a folder <b>oracleSQL</b> and move the "sqldeveloper-19.2.1.247.2212.noarch.rpm" file you've downloaded in that folder.

<details>
<summary>🔴 See command</summary>
<p>
  
[![RPM.png](https://i.postimg.cc/9MwC51qM/RPM.png)](https://postimg.cc/tZbLF3kQ)

</p>
</details>

##### Install Alien

Alien converts an RPM package file into a Debian package file or Alien can install an RPM file directly.<br>

Open a new Terminal window, and use as follows: <br>

```r
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install alien
```

Go to your <b>oracleSQL</b> folder, and use as follows:<br>

sudo alien <name_of_package>.rpm (e.g: I'm using sqldeveloper-19.2.1.247.2212.noarch.rpm).

Once command completed...

```r
$ ls
$ sudo dpkg -i <name_of_package>.deb
```
Your directory should now look like this ...

<details>
<summary>🔴 See executable</summary>
<p>
  
[![config.png](https://i.postimg.cc/GhK0f6SK/config.png)](https://postimg.cc/CzR6Br0n)

</p>
</details>

The executable should be located in the opt/sqldeveloper ...

<details>
<summary>🔴 See command</summary>
<p>
  
[![executable.png](https://i.postimg.cc/FRVGRXSn/executable.png)](https://postimg.cc/vgD5qj3W)

</p>
</details>

#### Launch Oracle SQL Developer

```r
$ ./sqldeveloper.sh
```

<hr>

### C. Connect to a database remotely

  > If you have an `AWS`, `Azure` or `GCP` account, you can connect to your database using Oracle SQL Developer.<br>
  
I'm here using an `Oracle RDS` instance on my `AWS` account.

#### 3. Create an Oracle DB instance hosted on AWS with RDS

On your `AWS Management Console`, go to Services > RDS.<br>

Go to Databases > Create database > Choose Standard create > Configuration: Oracle as engine type<br>

<details>
<summary>🔴 See configuration</summary>
<p>
  
[![standard-create.png](https://i.postimg.cc/bvcpSKM0/standard-create.png)](https://postimg.cc/18HLLYy4)

</p>
</details>

Edition: choose Oracle Standard Edition Two<br> Version: select Oracle 12.1.0.2.v2

Templates: choose Dev/Test<br>

DB instance identifier: ORCL-DB-Test<br>

Master username: choose a username <br>

Master password: choose a password

<details>
<summary>🔴 See configuration</summary>
<p>
  
[![DBidentifier.png](https://i.postimg.cc/NFTRynpS/DBidentifier.png)](https://postimg.cc/q6JNS1fx)

</p>
</details>

DB instance size: choose Burstable classes > select db.t3.micro

DB instance size: select Burstable classes (includes t classes) > db.t3.small

Storage > Allocated storage: 20 GiB

Disable "storage Auto Scaling"

<details>
<summary>🔴 See configuration</summary>
<p>
  
[![DBinstance-Size.png](https://i.postimg.cc/W3zWN4n5/DBinstance-Size.png)](https://postimg.cc/34MC9YzG)

</p>
</details>

Connectivity: set Publicaly accessible to <b>Yes</b>

<details>
<summary>🔴 See configuration</summary>
<p>
  
[![connectivity.png](https://i.postimg.cc/qMVPL8Q0/connectivity.png)](https://postimg.cc/HjzvW8fP)

</p>
</details>

Then <b>Create database</b>. When your DB is up and running...

[![dbrunning.png](https://i.postimg.cc/L627pvcs/dbrunning.png)](https://postimg.cc/yWpnhhYq)

#### 4. Connect and provision your DB remotely using Oracle SQL DB

Go back to `Oracle SQL Developer` locally and connect to your DB credentials.<br>

On <b>Connections</b> click on the "plus" button.<br>

Connect with the information provided upon the DB creation on RDS.

[![Selection-056.png](https://i.postimg.cc/bwHpb6jK/Selection-056.png)](https://postimg.cc/hXjkR1vr)

Here you go! You are now connected to your Oracle DB remotely using Oracle SQL Developer.<br>

In your left panel, you are connected to a database. Now you can create tables and start interracting with your DB.<br>

#### Basic SQL syntax

We are here using basic SQL syntax to show how our DB works.<br>

```r
CREATE TABLE students 
  ( 
     contact_id     NUMBER(10) NOT NULL, 
     last_name      VARCHAR2(50) NOT NULL, 
     first_name     VARCHAR2(50) NOT NULL, 
     address        VARCHAR2(50), 
     city           VARCHAR2(50), 
     uni_assignment VARCHAR2(50), 
     CONSTRAINT students_pk PRIMARY KEY (contact_id) 
  ); 
```

[![isaac-arnault-oracle.png](https://i.postimg.cc/4xDshmyF/isaac-arnault-oracle.png)](https://postimg.cc/Hr9fqWQQ)


You can create and provision tables in Oracle DB using PL/SQL syntax for more advanced needs.<br>

If you enjoyed this gist, feel free to fork and share it! Thanks.

## Author

* **Isaac Arnault** - Start with Oracle SQL Developer on Linux.
