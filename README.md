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
5. An interactive command line based tool to quickly generate an initial(or even final) manifest.
6. Data generation capabilities - Different projects have different requirements for data generation, as such Ariel has varied options to generate which I hope will suffice for most companies/projects - <br />
A. Regex based data generation - You specify a regular expression for a field and Ariel will generate random data that satisfies that regular expression. <br />
B. Seed data based data generation - You specify another file, another field or a simple in-place list as a starting point for generating data for a particular field. <br />
C. Data type based data generation - You specify nothing but a data type for a field and Ariel will generate random data for it. Supported also are Boolean, Datetime, guids, etc. <br />
D. Range and interval based data generation - You specify a range(if applicable) within which to generate data. Can also specify multiple ranges for same column with intervals, etc. <br />
E. Constant based data generation - You specify a constant to fill up all cells for a column <br />
F. Ability to specify size as well in text columns <br />
G. Date type with intervals
H. Formula support - creating data for a column based on other columns and using a given function.

### Command Line Options
TBD

### Manifest Sections and Features
TBD

### Manifest Schema
TBD

### How to navigate the project and test suite
TBD

### Architecture Overview
Draft - <br />
input manifest -> validation phase -> figure out sequence of data generation for files (and which one can be independent) -> File Generation(concurrent generation of independent files and sequential generation of files that need to be generated in a certain order) -> Data Generation (within each file concurrent generation of data for independent fields and sequential for ones that need to be generated in a certain order)

### Manifest Structure
Draft - <br />
```
{
   GlobalTargetFolder:
   zip : {
    type:
    name:
   }

   files: 
   [
    {
        name:
        rows:
        format: {field delim, row delim, extension, format, etc.}
        fields: 
        [
            {
                name:
                dataConfig: {dataType: int, nullRatio: 0.2, regex: , min: , max: , etc.}
                
            },
            {
               ...
            }
        ]
    },
    {
       ...
    }
   ]
}
```

#### Development Phases
##### Phase 1
Implementation with Unit tests of only csv files with almost all data types support but with parallel execution support. Release Ariel.

##### Phase 2
Parquet, Sql Server and other insert statement files. Release v2

##### Phase 3
All above mentioned features in. Release v3
