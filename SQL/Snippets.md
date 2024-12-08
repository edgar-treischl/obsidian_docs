Store XML in Postgres

```sql
CREATE TABLE lss_surveys (
    id SERIAL PRIMARY KEY,        -- Unique identifier for the record
    file_id VARCHAR(255) UNIQUE,  -- The file ID (which will be the name of the .lss file)
    master VARCHAR(255),    -- Survey title extracted from the .lss file
    survey_data XML               -- The XML content of the .lss file
);

```

Minimal working example

```sql
library(DBI)
library(RSQLite)

# Create in-memory RSQLite database
con <- dbConnect(drv = RSQLite::SQLite(), 
                 dbname = ":memory:")

#Write a table into the data base
dbWriteTable(conn = con, 
             name = "mtcars", 
             value = mtcars)

library(sqldf)
sqldf('select avg(mpg) from mtcars;')
```
