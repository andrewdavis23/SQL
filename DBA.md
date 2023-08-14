### How to make a column a key
```sql
-- Rename the organization column to id
ALTER TABLE organizations
RENAME COLUMN organization TO id;

-- Make id a primary key
ALTER TABLE organizations
ADD CONSTRAINT organization_pk PRIMARY KEY (id);
```

### Create a surogate key
```sql
-- Count the number of distinct rows with columns make, model
SELECT COUNT(DISTINCT(make, model)) 
FROM cars;

-- Add the id column
ALTER TABLE cars
ADD COLUMN id varchar(128);

-- Update id with make + model
UPDATE cars
SET id = CONCAT(make, model);

-- Make id a primary key
ALTER TABLE cars
ADD CONSTRAINT id_pk PRIMARY KEY(id);
```

### Datatype example
char is used for fixed length data. The main difference between char and varchar is that char will use less memory than variable memory and pad the string with spaces.
```sql
-- Create the table
CREATE TABLE students (
  last_name varchar(128) NOT NULL,
  ssn int PRIMARY KEY,
  phone_no char(12)
);
```
