Overview
========

Automatic media (TV, Movies, etc) systems contain a number of different components.  These compoinents can be genralized into two categories:

* Media Managers
* Downloaders

Media Managers
--------------

Two popular media managers are:

* Couch Potato (Manages Movies)
* SickBeard (Manages TV)

The media managers can be configured to look in a certain directory for new "completed" media.  Then they can post process, rename and move that media to the final destination.

The also search for new media and drop either .torrent or .nzb files into folders for the downloaders to pickup and process.

Downloaders
-----------

Two popular media downloaders are:

* SABnzdb (Uses USENET as the source)
* Transmission (Uses Torrents as the source)

Couch Potato - Movies
=====================

Using the Couch Potato Web UI, you configure it to connect to Transmission and SABnzdb, where it would put .torrent or .nzb files to be processed by said downloader.  Usually it will then look in a "completed" folder for the media and process it.

Sick Beard - TV
===============

Sick Beard can be configured to use torrent files, but prefers to use USENET.  Explanation here.

Configuration
=============

To summarize, you can get movies with either torrent files or nzb files via Couch Potato which uses Transmission and SABnzdb.

You are suggested to get TV using nzb files via Sick Beard via SABnzdb.

I would think that if you choose to use nzb files for both movies and TV, you should setup different instances of Transmission to separate the media types.

Transmission Volumes
--------------------

VOLUME /downloads
VOLUME /incomplete
VOLUME /watch
VOLUME /config

SABnzdb
-------

* /config
* /incomplete [misc]/download-dir=
* /complete   [misc]/complete-dir=

It does not look king SABnzdb has a "watch" dir to look for new .nzb files.  I think you are supposed to use the API like Sick Beard or add nzb files manually via the web interface.

Couch Potato Volumes
--------------------

VOLUME /config
VOLUME /data

VOLUME /movies
VOLUME /completed-new-movies

Sick Beard
----------

VOLUME /config
VOLUME /data
VOLUME /tv
VOLUME /complete



Directory Mapping
=================

    BASE=<whatever>
    MOVIE_LIBRARY_DIR=<whatever>
    TV_LIBRARY_DIR=<whatever>
    
    TRANSMISSION_MOVIES_CONFIG=$BASE/transmission-movies/config
    TRANSMISSION_MOVIES_INCOMPLETE=$BASE/transmission-movies/incomplete
    TRANSMISSION_MOVIES_COMPLETE=$BASE/transmission-movies/complete
    TRANSMISSION_MOVIES_WATCH=$BASE/transmission-movies/watch
    
    SABNZDB_CONFIG=$BASE/sabnzdb/config
    SABNZDB_DATA=$BASE/sabnzdb/data
    SABNZDB_INCOMPLETE=$BASE/sabnzdb/incomplete
    SABNZDB_COMPLETE=$BASE/sabnzdb/complete
    
    COUCHPOTATO_CONFIG=$BASE/couchpotato/config
    COUCHPOTATO_DATA=$BASE/couchpotato/data
    COUCHPOTATO_MOVIES=$MOVIE_LIBRARY_DIR
    COUCHPOTATO_COMPLETE=$TRANSMISSION_MOVIES_COMPLETE
    
    SICKBEARD_CONFIG=$BASE/sickbeard/config
    SICKBEARD_DATA=$BASE/sickbeard/data
    SICKBEARD_COMPLETE=$BASE/sickbeard/complete
    SICKBEARD_NZB_DIR=$BASE/sickbeard/nzb
    SICKBEARD_TORRENT_DIR=$BASE/sickbeard/torrent

And if also using Transmission for TV:
    
    TRANSMISSION_TV_CONFIG=$BASE/transmission-tv/config
    TRANSMISSION_TV_INCOMPLETE=$BASE/transmission-tv/incomplete
    TRANSMISSION_TV_COMPLETE=$BASE/transmission-tv/complete
    TRANSMISSION_TV_WATCH=$BASE/transmission-tv/watch
    


Network Ports
=============

|Application | Default Port |
|------------|-------|
| Transmission-Deaemon | 9091 |
| SABnzdb      | 8080, 9090?? |
| Couch Potato | 5050 |
| Sick Beard   | 8081 |


