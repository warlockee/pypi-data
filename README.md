# PyPi Data

The contents of the PyPi JSON API for all packages, updated every 20 minutes

## Why?

Fetching bulk data from the PyPi API in bulk is non-trivial, and using the [BigQuery dataset](https://warehouse.pypa.io/api-reference/bigquery-datasets.html) requires using BigQuery. The entire package dataset is not large and easily fits into the memory of most developer machines, so it's much more fluid to explore the data with Pandas than the heavyweight (and sometimes expensive) BigQuery.

## Release data

Each package has a unique directory within [release_data/](release_data/), prefixed with the first two
*lowercased* characters of the package name. Each package has a unique JSON compressed file containing the full API response for *all package releases* within it. 

For example: [release_data/d/j/django.json](release_data/d/j/django.json) contains:

```json
{
    "1.0.1": {
        "info": {
            "author": "Django Software Foundation",
            "author_email": "foundation at djangoproject com",
            "bugtrack_url": null,
            "classifiers": [
                "Development Status :: 5 - Production/Stable",
                "Environment :: Web Environment",
                "Framework :: Django",
                "Intended Audience :: Developers",
                "License :: OSI Approved :: BSD License",
                "Operating System :: OS Independent",
                "Programming Language :: Python",
                "Topic :: Internet :: WWW/HTTP",
                "Topic :: Internet :: WWW/HTTP :: Dynamic Content",
                "Topic :: Internet :: WWW/HTTP :: WSGI",
                "Topic :: Software Development :: Libraries :: Application Frameworks",
                "Topic :: Software Development :: Libraries :: Python Modules"
            ],
            "description": "UNKNOWN",
            "description_content_type": null,
            "docs_url": null,
            "download_url": "http://www.djangoproject.com/m/bad-installer.txt",
            "downloads": {
                "last_day": -1,
                "last_month": -1,
                "last_week": -1
            },
            "home_page": "http://www.djangoproject.com/",
            ... and other keys
```

## Changelog data

PyPi also publishes a serial changelog of events that occur to all packages. These are available in the [changelog_data/](./changelog_data) directory. 

```
❯ gzcat changelog_data/0014723119-0014734853.json.gz | head -n 30
[
    {
        "action": "new release",
        "name": "cdklabs.cdk-hyperledger-fabric-network",
        "serial": 14723119,
        "timestamp": "2022-08-11T00:22:12",
        "version": "0.8.8"
    },
    {
        "action": "add py3 file cdklabs.cdk_hyperledger_fabric_network-0.8.8-py3-none-any.whl",
        "name": "cdklabs.cdk-hyperledger-fabric-network",
        "serial": 14723120,
        "timestamp": "2022-08-11T00:22:12",
        "version": "0.8.8"
    },
```
