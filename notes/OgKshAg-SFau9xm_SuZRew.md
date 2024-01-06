---
tags: disinfo, 0archive
title: ArticleParser Installation Guide
---
# ArticleParser Installation Guide

## Install Python packages

We use Python 3.7.  Install Python dependencies with [Pipenv](https://pipenv.pypa.io/en/latest/):

```shell
$ pip install pipenv    # if you haven't have Pipenv
$ pipenv install
```

## Set up database

We use MariaDB 10.  To setup database connections:

1. Create a database.  Take a note of the database name, hostname, username, and password.
2. The database connection string will be `mysql+pymysql://<username>:<password>@<hostname>/<database name>`.  We use PyMySQL, so the connection string should starts with `mysql+pymysql` in order for SQLAlchemy to pick up the right driver.
3. Copy `.env.default` to `.env`.
4. Edit the value of `DB_URL` to be the connection string.  You can leave all other settings in `.env` as is for now.
5. Run db migrations with `pipenv run alembic upgrade head`

## Set up upstream scraper databases

ArticleParser currently gain access to upstream databases through database connections.  Each of the upstream databases is identified by a name, and has a database connection string set in `.env`.  The default upstream is called "ZeroScraper", and the database connection to it is defined by `SCRAPER_DB_URL` variable.

So the simplest way to add the default upstream database is:

1. Take a note of the database connection string to the upstream.
2. Edit the value of `SCRAPER_DB_URL` to be the connection string.

To add another upstream database, you have to add one row in the `scraper` table of the database of ArticleParser.  The values should be:

- `scraper_name` is a name unique to the upstream.
- `data` is a JSON object with the following fields:
    - `type`: only "mysql" is currently supported
    - `db_url_var`: the environment variable name that will store the connection string to this upstream
    - `site_table_name`: table name of sites in the upstream database
    - `article_table_name`: table name of articles in the upstream database
    - `snapshot_table_name`: table name of article snapshots in the upstream database

## Parse data


```shell
$ pipenv shell
$ ./ap.py parse producer
$ ./ap.py parse publication --limit 1000
```

You can run these commands multiple times to parse source data in batch.  `--limit <number>` sets the number of entries to parse for each batch.

## Check the information of producers

```shell
$ ./ap.py producer list                  # list all producer in the database
$ ./ap.py producer show <producer_id>    # show detail information about a producer
```

You can find the ID of the producers by listing them.

## Generate dataset files

To get producer dataset: 

```shell
$ ./ap.py datapublish producer > producer.jsonl
```

Because of the volume of the data usually involved, you must specify a producer by its ID, in addition to one of the `--published-at` and `--processed-at` arguments, to get the publication dataset.  The two arguments accept values of the same date range format.  Some examples are: 

```shell
# all output to STDOUT
$ ./ap.py datapublish --producer <producer_id> --processed-at today
$ ./ap.py datapublish --producer <producer_id> --processed-at yesterday
$ ./ap.py datapublish --producer <producer_id> --published-at 2020-01-01:2020-01-31
```

## Publish dataset files to Google Drive

The `ap.py datapublish` command can publish dataset files to a Google Drive folder with Google API.  You will have to setup a service account.  Follow the [instructions from Google](https://developers.google.com/identity/protocols/oauth2/service-account) to setup an account, and save the downloaded key file in the project directory.  Then,

1. Create a Google Drive folder to store the dataset files.  You can create the folder with any Google account.
2. Take a note of the ID of the Google Drive folder from its URL.  Say in the URL of [0archive public dataset](https://drive.google.com/drive/folders/1ckDs03tdXhLdeF0N2St5OP0EeqxFC1bm), folder ID is the last part: `1ckDs03tdXhLdeF0N2St5OP0EeqxFC1bm`. 
3. Share the folder with the service account you created.  The service account should be an "Editor" so that it can add and edit files in that folder.
4. Add one row in the `drive` table of the database of ArticleParser: `name` is a name unique to the Google Drive folder, and `data` is the the following JSON object:

    ```json
    {
      "dirs": {
        "root": "<folder_id>",
        "producers": {}
      },
      "files": {
        "producers": {}
      }
    }
    ```
    
    Note that `<folder_id>` is the ID of your Google Drive folder.

Suppose your service acconut key file is stored as `service.json`, you can now publish to Google Drive with:

```shell
$ ./ap.py datapublish publication --producer <producer_id> --processed-at <processed_date_range> --drive <drive_name> --service-account service.json
```

The `ap.py datapublish` command uploads dataset files to Google Drive in the following structure:

```
<root>/<producer_name> (<domain>) <producer_id>/YYYY-MM.zip
```

The dataset file `YYYY-MM.zip` contains all publications published in the given month in JSONLines.  Publications whose published date cannot be recognized by ArticleParser are all stored in `no_date.zip` under the same folder.  See the [public datasets of 0archive](https://drive.google.com/drive/folders/1ckDs03tdXhLdeF0N2St5OP0EeqxFC1bm) for an example.

The `ap.py datapublish` command keeps the information about the folders and files on Google Drive in the `drive` table.  It also only uploads the files that are actually changed by the processing within the given date range.  You can therefore run the following command everyday to upload the outcomes of the processing of the day before:

```shell
$ ./ap.py datapublish publication --producer <producer_id> --processed-at yesterday --drive <drive_name> --service-account service.json
```

An example of this setting is in the `scripts/upload-google-drive.sh` file.

## Set up cronjobs

In our deployment of ArticleParser in the 0archive project, we generally run the following cronjobs:

- `./ap.py parse producer`: hourly
- `./ap.py parse publication  --limit 5000`: hourly (highly dependent on the CPU and memory you have)
- `scripts/upload-elastic.sh`: daily
- `scripts/upload-google-drive.sh`: daily
- `scripts/runstats.sh`: daily

You can monitor the progress of ArticleParser with the `parser_result` and `parser_stats` tables in the database.


