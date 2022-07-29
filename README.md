
## Table of Contents
1. [ Project Description. ](#desc)
2. [About Nigeria HFR](#about)
3. [ Project Development](#dcue)
4. [ References ](#ref)

[//]: # (I must include tools section and add tools images, check proper README design tutorial)


<a name="desc"></a>
# 📌Project Description

####  *`Project source` - [udacity](https://www.udacity.com/course/data-engineer-nanodegree--nd027?gclid=Cj0KCQjw54iXBhCXARIsADWpsG_BlcJSeJxX-UsroqSGrf8Hjb6KF3mnYvdS3kfU3juwMWFCgxkelAAaAgHbEALw_wcB&utm_campaign=12948014301_c_individuals_career&utm_campaign=12948014301_c_individuals&utm_keyword=udacity%20data%20engineering_e&utm_keyword=udacity%20data%20engineering_e&utm_medium=ads_r&utm_medium=ads_r&utm_source=gsem_brand&utm_source=gsem_brand&utm_term=127442640371&utm_term=127442640371)*
</br>

This end-to-end data modeling project entails designing and implementing a data warehouse solution for a music streaming industry. The core responsibility is to model an analytical database for the data analytics team interested in understanding users' activity to improve business decisions. The current data available is operational data, JSON metadata files on the songs in the app.

</br>

# ✅ Project Objective
The project objective includes
1. The design of an optimized **data ingestion pipeline architecture** 
2. The design of the data warehouse **ERD (Entity Relationship Diagram)** for the data analytics team.
3. The implementation of **Data Extraction, Transformation and Loading (ETL)**.
4. The **Automation and Scheduling** of the processes.
5. The development **Data quality checks** to validate the source and destination data.
 
</br>

<a name='dcue'></a>
# 🛠Project Development

## Data Pipeline Architecture
##### for architecture design -  https://app.diagrams.net/

![Data-model-ETL](https://user-images.githubusercontent.com/55639062/181843973-07f241fa-5f4e-4b55-aa91-0c00c49d1273.png)

The architecture is purposely designed to achieve the project objective:
* `Data Source`: User log and song data are archived in file directories.
* `Processing`: The data are loaded into pandas for data extraction and transformation
* `Ingestion`: Since the DWH is in Postgres, SQL insert commands together with python are used to load the data in DWH because of SQL readability and simplicity across the data team.
* `Storage`: Data is stored in PostgreSQL for analytical purposes
* `Visualization`: Analytics dashboard for business decisions.
* `Validation`: Data quality check that communicates the data accuracy between the source data and final data.
* `Scheduler`: Since the data comes in batches, the pipeline is triggered when a new file drops in the file directory.


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
