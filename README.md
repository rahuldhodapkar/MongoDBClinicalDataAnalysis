# Clinical Dataset for MongoDB

This folder contains a sample loading and cleaning process for a clinical
dataset into MongoDB, as well a sample Jupyter notebook to perform some
basic analysis.

## The Dataset

This demo uses the clinical trials dataset published
by the FDA on https://clinicialtrials.gov,
under the umbrella organization of the National Library of Medicine,
National Institute of Health.

The data is was originally published in an XML format, under the 
specification defined 
[here](https://clinicaltrials.gov/ct2/html/images/info/public.xsd).
This demo contains code for transforming this data into JSON for ingest and
analysis in MongoDB.

## Dependencies

[xml-to-json](https://hackage.haskell.org/package/xml-to-json)

[jq](https://stedolan.github.io/jq/)

The above libraries are just to parse XML and JSON easily,
they can be replaced fairly easily by other libraries with similar 
functionality.

[Jupyter Notebook](http://jupyter.org/)

The sample notebook uses Python 3, but should be compatible with Python 2.
I haven't yet tested this configuration.

## Running

### Start MongoDB

If you would like to connect to a non-default
MongoDB (not running on `127.0.0.1:27017`), supply a mongodb 
connection string to the import and data preparation script as

    export MONGODB_URI="mongodb://<my-connection-details>"

See the [MongoDB Documentation](https://docs.mongodb.com/manual/reference/connection-string/) 
for information on how to construct a connection string for your deployment. 

Note that the Jupyter notebook script is written to expect:

    database: "clintrials"
    collection: "clinical_studies"

but these can be altered by specifying a different database in the
`MONGODB_URI` or a different collection name in the environment
variable `MONGODB_IMPORT_COLL`.

### Run the Download / Import Script

    ./import_data.sh

### Start the Jupyter Notebook server

    cd notebooks
    jupyter notebook

### Connect to the notebook server

Jupyter should automatically open a browser window, but it is
usually running at http://localhost:8888.
