# PostgreSQL Database App for Predix Edge
The intent of this app is to allow users to install a PostgreSQL Database on the Predix Edge device, allowing postgres database functionality on the Predix Edge with the ability to read, write, and edit data from an external host or client.

## Download and Installation
The predix-edge-postgres-20181211-1.0.0.tar.gz can be directly downloaded to your Predix Edge device through PETC or Edge Manager.  Predix Edge will create the data folders, mount them, and start the postgres Docker container.  After downloading and deploying, the status of the postgres app will go to “Running”.

## Use and Database Access
To connect to your Predix Edge postgres DB, you’ll need to download and install a postgres client on your host or external computer.  There are numerous free or paid for clients for postgres.  The app was tested using the free pgAdmin4, which can be downloaded for any operating system at https://www.pgadmin.org/download/.  Installation instructions for you OS are also found on this site.  

The Predix Edge postgres DB by default exposes port 5432.  To Read, Write, or Edit your Predix Edge postgres DB, you’ll need to link the pgAdmin to your Predix Edge.  Instructions for using the pgAdmin4 client are here (https://www.pgadmin.org/docs/pgadmin4/dev/).  Once you’ve created a database, created a table, and populated it in pgAdmin, you can verify data tables are populated in the Predix Edge postgres.  Open a terminal from your Predix Edge (ssh or using your hypervisor).  From the prompt, run

	>docker ps

To get the container ID of the postgres container, then

	>docker exec -it <container_id> sh
	#psql -U <database name you created in pgAdmin4>  (default is ‘postgres’)

The psql cli comes with the PostgreSQL, and can be used to Read, Write and Edit data tables.  You can now use all the psql cli commands as found here (https://www.postgresql.org/docs/10/app-psql.html) or to simply view your data, from the prompt:

	postgres=#\dt   (list all the tables in your database)
	postgres=#\d <table_name>	(shows all the columns in your table)

To query values from your table, use the psql cli commands:

	postgres=#SELECT column1, column2, etc <Enter>
	postgres-#FROM <table_name>;<Enter>	(remember to add the ‘;’ to end your query.

This will show you all table entries in column1, column2 etc.
[![Analytics](https://predix-beacon.appspot.com/UA-82773213-1/postgres/readme?pixel)](https://github.com/PredixDev)
