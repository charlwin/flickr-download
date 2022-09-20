# Flickr Download

## Introduction

[![Build Status](https://app.travis-ci.com/beaufour/flickr-download.svg?branch=master)](https://app.travis-ci.com/github/beaufour/flickr-download)

Simple script to download a [Flickr](http://flickr.com) set.

To use it you need to get your own Flickr API key here:
<https://www.flickr.com/services/api/misc.api_keys.html>

    flickr_download -k <api key> -s <api secret> -d <set id>

It can also list the public set ids for a given user:

    flickr_download -k <api key> -s <api secret> -l <user name>

Get a public set using the title and id to name the downloaded files:

    flickr_download -k <api key> -s <api secret> -d <set id> -n title_and_id

Download private or restricted photos by authorizing against the users account. (see below)

## Installation

To install this script use the Python pip utility bundled with your Python distribution:

    pip install flickr_download

## API key

Get your [Flickr API key](http://www.flickr.com/services/api/).

You can also set your API key and secret in `~/.flickr_download`:

    api_key: my_key
    api_secret: my_secret

## User Authentication Support

The script also allows you to authenticate as a user account. That way you can download sets that
are private and public photos that are restricted. To use this mode, initialize the authorization by
running the script with the `t` parameter to authorize the app.

    flickr_download -k <api key> -s <api secret> -t

This will save `.flickr_token` containing the authorization. Subsequent calls with `-t` will use the
stored token. For example using

    flickr_download -k <api key> -s <api secret> -l <USER>

with _USER_ set to your own username, will only fetch your publicly available sets, whereas adding `-t`

    flickr_download -k <api key> -s <api secret> -l <USER> -t

will fetch all your sets including private restricted sets.

## Optional arguments

    -h, --help            show this help message and exit
    -k API_KEY, --api_key API_KEY
                            Flickr API key
    -s API_SECRET, --api_secret API_SECRET
                            Flickr API secret
    -t, --user_auth       Enable user authentication
    -l USER, --list USER  List photosets for a user
    -d SET_ID, --download SET_ID
                            Download the given set
    -p USERNAME, --download_user_photos USERNAME
                            Download all photos for a given user
    -u USERNAME, --download_user USERNAME
                            Download all sets for a given user
    -i PHOTO_ID, --download_photo PHOTO_ID
                            Download one specific photo
    -q SIZE_LABEL, --quality SIZE_LABEL
                            Quality of the picture
    -n NAMING_MODE, --naming NAMING_MODE
                            Photo naming mode
    -m, --list_naming     List naming modes
    -o, --skip_download   Skip the actual download of the photo
