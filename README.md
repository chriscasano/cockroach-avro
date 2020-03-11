
# Import all columns

Databricks Sample: https://docs.databricks.com/_static/misc/episodes.avro

#### Download avro file

wget https://docs.databricks.com/_static/misc/episodes.avro

#### Copy to S3

cp episodes.avro s3://chrisc-test/sample-data/episodes.avro

#### Run import with only some fields

`cockroach sql --insecure --host=localhost`

`import table episodes
(
title string,
air_date string,
doctor int
)
avro data (
's3://chrisc-test/sample-data/episodes.avro?AWS_ACCESS_KEY_ID=[placeholder]&AWS_SECRET_ACCESS_KEY=[placeholder]'
);`


# Import only partial columns

#### Download avro file

Samoa Sample: https://cwiki.apache.org/confluence/display/SAMOA/Sample+Avro+Datasets

#### Copy to S3

`aws s3 cp covtypeNorm_binary.avro s3://chrisc-test/sample-data/`

#### Run import with only some fields

`cockroach sql --insecure --host=localhost`

`import table covtypenorm
(
Elevation float,
Aspect float,
Slope float,
Horizontal_Distance_To_Hydrology float
)
avro data (
's3://chrisc-test/sample-data/covtypeNorm_binary.avro?AWS_ACCESS_KEY_ID=[placeholder]&AWS_SECRET_ACCESS_KEY=[placeholder]'
);`
