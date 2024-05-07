# waste_public_data
Public repository of waste data contributed by multiple organizations

<<<<<<< Updated upstream
=======
# 2024-05-07
The following files represent data dumps from tables in the WasteMAP database:__
country.csv__
data_source.csv__
facility_emissions.csv__
facility_gas_capture.csv__
facility_projects.csv__
facility_waste.csv__
observation_type.csv__
us_states_and_territories.csv__

The tables are named to be indicative of what data they contain.  And can be joined using common columns.  These common columns are primary - foreign key relationships.

## Joins
The facility.csv table contains the facility.id column.  This column is the primary key that can be joined to any other table that starts with "facility_".
In SQL terms the join between facility.csv to facility_emissions.csv would be:

        FROM facility f
        LEFT JOIN facility_emissions fe
        ON fe.facility_id = f.id

All facility to facility_ tables follow the join syntax of "ON facility_[insert_rest_of_table_name_here].facility_id = f.id".
This is the general join structure for all the tables where you find an column that is called, or ends in, id.

        FROM table1 t1
        LEFT JOIN table2 t2
        ON t2.[insert_t1_table_name].id = t1.id

If you are looking to join in other tables such as country, data_source, etc.  Know that they also follow the above syntax.
The one exception is the us_states_and territories table.  This table joins to the facility table using a natural key relationship.

This means:

        FROM facility f
        LEFT JOIN us_states_and_territories usat
        ON usat.name_abbrev = f.state

I primarily use LEFT JOIN because there are not always 1:1 relationships.  There are facilities that may have emissions data, but no waste data.  Gas capture data, but no projects data, etc.
Using INNER JOIN woill cause facility rows to drop out of the results.  INNER JOIN will work without dropping out data on the following tables:__
country.csv__
data_source.csv__
observation_type.csv__
>>>>>>> Stashed changes
