
## Table of Contents
1. [ Project Description. ](#desc)
2. [ Project Objective. ](#obj)
3. [ Project Development](#dev)
    * [ Data Pipeline Architecture ](#dpa)
    * [ Entity Relationship Diagram ](#erd)
    * [ Project Template ](#pt)
4. [ References ](#ref)

[//]: # (I must include tools section and add tools images, check proper README design tutorial)


<a name="desc"></a>
# 📌Project Description

####  *`Project source` - [udacity](https://www.udacity.com/course/data-engineer-nanodegree--nd027?gclid=Cj0KCQjw54iXBhCXARIsADWpsG_BlcJSeJxX-UsroqSGrf8Hjb6KF3mnYvdS3kfU3juwMWFCgxkelAAaAgHbEALw_wcB&utm_campaign=12948014301_c_individuals_career&utm_campaign=12948014301_c_individuals&utm_keyword=udacity%20data%20engineering_e&utm_keyword=udacity%20data%20engineering_e&utm_medium=ads_r&utm_medium=ads_r&utm_source=gsem_brand&utm_source=gsem_brand&utm_term=127442640371&utm_term=127442640371)*
</br>

This end-to-end data modeling project entails designing and implementing a data warehouse solution for a music streaming industry. The core responsibility is to model an analytical database for the data analytics team interested in understanding users' activity to improve business decisions. The current data available is operational data, JSON metadata files on the songs in the app.

</br>

<a name='obj'></a>
# ✅ Project Objective

The project objective includes
1. The design of an optimized **data ingestion pipeline architecture** 
2. The design of the data warehouse **ERD (Entity Relationship Diagram)** for the data analytics team.
3. The implementation of **Data Extraction, Transformation and Loading (ETL)**.
 
</br>

<a name='dev'></a>
# 🛠Project Development

<a name='dpa'></a>
## Data Pipeline Architecture
##### for architecture design -  https://app.diagrams.net/

![Data-model-ETL](https://user-images.githubusercontent.com/55639062/181861496-f679bac5-061a-45db-9581-6f419ff62f05.png)

The architecture is purposely designed to achieve the project objective:
* `Data Source`: User log and song data are archived in file directories.
* `Processing`: The data are loaded into pandas for data extraction and transformation
* `Ingestion`: Since the DWH is in Postgres, SQL insert commands together with python are used to load the data in DWH because of SQL readability and simplicity across the data team.
* `Storage`: Data is stored in PostgreSQL for analytical purposes
* `Visualization`: Analytics dashboard for business decisions.

<a name='erd'></a>
## ERD (Entity Relationship Diagram) Design
The data model below shows a star schema optimized for queries on the song play analysis utilizing 3 levels of normalization (1NF, 2NF, and 3NF), where appropriate, using the song and log datasets.

### Fact Table
**songplays —** records in log data associated with song plays i.e. records with page `NextSong`
*songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent*

### Dimension Tables
**users —** users in the app
*user_id, first_name, last_name, gender, level*

**songs —** songs in the music database
*song_id, title, artist_id, year, duration*

**artists —** artists in the music database
*artist_id, name, location, latitude, longitude*

**time —** timestamps of records in songplays broken down into the specific unit
*start_time, hour, day, week, month, year, weekday*

</br>

![Screenshot (148)](https://user-images.githubusercontent.com/55639062/78468855-5e654300-7713-11ea-835a-54c1f0cdf048.png)


</br>

<a name='pt'></a>
## Project Template
In addition to the data files, the project workspace includes five files:
1. `test.ipynb` displays the first few rows of each table to check the database.
1. `create_tables.py` drops and creates the postgres table. This drops (if exists) and create tables. *Run at the start of the project*
1. `etl.ipynb` reads and processes a single file from song_data and log_data and loads the data into the tables. It contains a detailed explanation of the ETL process to the tables.
1. `etl.py` reads and processes files from song_data and log_data and loads them into the tables.
1. `sql_queries.py` contains all the SQL queries used to perform all SQL command to ingest data to DB