# ÖBB API Documentation

Inoffical documentation for common API endpoints of the [Austrian Federal Railways (ÖBB)](https://oebb.at), which are used on https://tickets.oebb.at (and probably in the mobile apps as well).

I ignored most of the optional parameters, headers etc. to provide the simpliest way of usage.

## Usage

### Connections between stations

1. [Authentication](domain/v4/get_init.md)
1. Find [Stations](hafas/v1/get_stations.md) for start and destination
1. Find [Connections](hafas/v4/post_timetable.md) between the stations

## Further APIs

The are many additional APIs like:
* Departures and Arrivals at a specific station
* "Zug Radar" - Live Positions of Trains

In case someones needs them, feel free to create a PR or an issue.

## Client Libraries

* NodeJS: https://github.com/juliuste/oebb (base for this documentation, thanks!)