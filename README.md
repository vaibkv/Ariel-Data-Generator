# Ariel-Data-Generator
A Scala based fast, concurrent and extendable fake data generator supporting various file formats and parent-child relations

## Project Overview
Ariel is a command line based manifest/configuration driven fake data generator. It's meant to be fast and to the point. Here are the project features - 

### Technology Stack
This is a pure Scala/SBT based project.

### Usage 
For Windows - <br />
ariel.bat --verbose --conf /path/to/manifest.json

For Unix/Mac/Linux - <br /> 
./ariel.sh --verbose --conf /path/to/manifest.json

### Capabilities
The main capability is to generate multiple data files with the following features supported (via the manifest) - 

1. Supported formats - all kinds of csv (csv, psv, tsv, etc.), parquet, json, Sql Server insert statements, Postgres insert statement, MySql insert statements, Oracle insert statements, Hive insert statements, fixed width files.
2. Extensions supported - many (.txt, .parquet, .sql, .hql, .csv, etc.)
3. Ability to zip the created files (.zip, .bz2, .gzip, .tar, etc.)
4. Ability to support child - parent relationships in data files as well as self - referential files. In order to mimic real world usage there will be capability to mention what ratio of child field values have to be null/non-null.
5. Data generation capabilities - Different projects have different 