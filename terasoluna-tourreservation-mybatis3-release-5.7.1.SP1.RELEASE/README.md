## Tour Reservation Sample Application
This is a reference application built completely using TERASOLUNA Server Framework for Java (5.x) ([http://terasoluna.org](http://terasoluna.org "http://terasoluna.org")).

This application shows **how an IDEAL project configuration and package structure must be like.** It also shows working sample of best practices recommended in TERASOLUNA Server Framework for Java (5.x) Development Guideline.

**This sample uses MyBatis3.**

### Getting started

#### Download

Download source code from [here](https://github.com/terasolunaorg/terasoluna-tourreservation-mybatis3/releases "here").
Extract the zip file at any location of choice.

#### Run PostgreSQL

Install and start PostgreSQL.
select 'P0stgres' as password for db user or select any password of choice. Be sure to remember the password. 
If 'P0stgres' is not used, some changes will be required in configuration files. Hence be sure to remember it.

### Run PostgreSQL

Install and start PostgreSQL.

create database 'tourreserve'.

#### Insert test data

It is assumed that maven is already installed.
Move to the directory where the downloaded source-code is unzipped.
If password of db user is set to 'P0stgres' its not required to edit any file and directly execute the below command.
If it is set to any other password, then update the password in `terasoluna-tourreservation-initdb/pom.xml`.

Execute the below command:

```console
$ mvn -f terasoluna-tourreservation-initdb/pom.xml sql:execute
```

Test data is currently available in Japanese only.

#### Install jars and build war

If db user password is not set to 'P0stgres', then go to `terasoluna-tourreservation-env/src/main/resources/META-INF/spring/terasoluna-tourreservation-infra.properties` and update the password. If it is set to 'P0stgres', no changes are required.

```console
$ mvn clean install
```

#### Run server and deploy war

Deploy `terasoluna-tourreservation-web/target/terasoluna-tourreservation-web.war` to your Application server (e.g. Tomcat9)

You can also use `mvn cargo:run` to test this application quickly with option `MAVEN_OPTS=-XX:MaxPermSize=256m` in environment variable.

```console
$ mvn -f terasoluna-tourreservation-web/pom.xml cargo:run
```

access [http://localhost:8080/terasoluna-tourreservation-web/](http://localhost:8080/terasoluna-tourreservation-web/)

Alternatively, these project can also be imported into Eclipse and application can be run using WTP.

#### Test with selenium

Install Firefox to run test.  
[geckodriver](https://github.com/mozilla/geckodriver/releases) (`v0.30.0` recommended) placed in application execution environment and add to `PATH`.

Run test.

```console
$ mvn -f terasoluna-tourreservation-selenium/pom.xml clean test
```

> **Note:**
>
> If GeckoDriver is not registered in the path, [webdrivermanager](https://github.com/bonigarcia/webdrivermanager) will download it automatically.
> Configure using [properties](https://github.com/bonigarcia/webdrivermanager#webdrivermanager-api) in `wdm.properties` or Java System Properties.
