# whitewaterns-twitter
Twitterbot for WhitewaterNS twitter account, reads in water levels / forecasts and surf conditions
and tweets out information so we don't have to check a bunch of places. It checks, or will check 
the following

 * Environment Canada Swell Heigh data
 * Environment Canada hydrometric data
 * Environment Canada last 24hr rainfall amounts
 * Medway river gauge

To make it a little easier to keep track of all of these sources, I'm going to break
up the application into a few pieces. 

* `bin/` - Contains the scripts to gather info
* `/source.json` - List of sources and their required info
* `/settings.conf` - Config file with the twitter auth info
* `state/` - One file per data source, holds the last state information
* `/whitewater-twiterbot` - The program itself

#### How it works

 The script is expected to be run by CRON in /cron.hourly on each run it
 checks the /source.json and looks for sources that should be run at the
 current time then it calls the defined `bin/` script. The bin scripts
 return a json result on STDOUT. This is compared against the state/ and
 if there has been a change then a tweet is sent out. 

#### Requirements

 The following python modules are required, this script was written against Python 2.7

 * python-twitter
 * JSON 
 * tinyurl

#### Additional requirements for some gathering methods

 Wave heigh data is pulled from GRIB files as such you'll need the following Python libs in addition
 to the above to use any of the surf functions

 * numpy
 * grib
 * gribapi
 * urllib
