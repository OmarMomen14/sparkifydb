# Sparkify Database | Data Modeling 
---
---
This repository contains the code and documentation for designing a data model of the new straming app `sparkify`.

## Introduction
---
Sparkify -streamping app startup- is interested in buidling a database to record songs and user activity of their app. The main objective of the required database is to enable analysts to collect important information about the app usage. Doing analysis using JSON files (current situation) is not an effective way for this kind of analysis. Operations like aggregations, countings, and conditioning over different variables of the data are not possible without a properly designed relational database.

In this project, I worked on designing a relational data model that can be then deployed in a production level database. Also I implemented a complete ETL piepline. I am using Postgresql as the DBMS, I designed a proper star-schema for the DB, created properly defined tables according to the scheema design, loaded the data from the current available JSON files, inserted the data into the DB tables, and finally run some tests to ensure the integrity and robustness of the database.

## File Tree
---
The file structure of the this project:

```
.
├── data
│   ├── log_data                # song plays log data (in `json` format)
│   ├── song_data               # songs details data (in `json` format))
├── create_tables.py            # python script to drop and create tables in db
├── etl.ipynb                   # a step by step notebook to implement ETL processes
├── etl.py                      # python script to implement a complete ETL pipeline
├── sql_queries.py              # pre_defined SQL queries for tables creation and data insertion
├── test.ipynb                  # a notebook of testing operations to test the implemented database 
├── requirements.txt            # python dependancies 
└── README.md
```

## Reproducing the project results
---

### Setup Postgresql on your machine
[Installation Guide](https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-20-04-quickstart)

- Create a username by the name `student` and a password `student`
- Create a database by the name `sparkifydb`

### Cloning the repository
clone the repository:
```
$ git clone <repository url>
```

### Environment Installation
setup a python venv 
```
$ python3 -m venv env
$ source env/bin/activate
$ pip install -U setuptools pip
$ pip install -r requirements.txt
```

### Create DB tables
run the python script needed to create the tables of the database according to the schecma define in `sql_queries.py` 
```
$ python3 create_tables.py
```

### Implement ETL processes 
Go through the notebook `etl.ipynb` and implement the different ETL steps

### Implement a full ETL pipeline 
run the script `create_tables.py`  
run the script `etl.py`  

### Test the database
go through the notebook `test.ipynb` to test different parts of the database



## Project Core
---
### Data Model: Star Schema
* I chose the star schema as a model for this project as the main objective of this work was to enable analysts of quering the database with join/aggrgation/conditiong operations to capture important insights of the business.
* The `songsplay` table acts as the `Fact` table in this model, and `users`, `artists`, `songs`, `time` act as dimension tables/ 
* Each dimension table got a corresponding foriegn key in the fact table.

### ETL Pipeline
* I implemented a complete ETL pipeline:
    - started by extracting the data from JSON files using the `pandas` library.
    - did some operations on the extracted data to fit the tables entries.
    - inserted the extracted data into the DB tables 