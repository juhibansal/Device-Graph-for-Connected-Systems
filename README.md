Device-Graph-for-Connected-Systems

Goal of the project is to create a deterministic device graph pipeline ie to identify and connect digital devices based on their usage. The key application of this pipeline would be for efficient digital advertisement targeting. Motivation for the project came from getting unrelated advertisement myself as well as from reading a paper on ‘Internet Device Graphs’published Aug 2017.

Table of Content
1. Background
2. Data Pipeline
3. Challenges
4. Pipeline flow

Background 

Every year more than $80 Billion is spent on digital marketing and advertisement which includes Mobile devices, electronic Billboards etc.

Google, Facebook, Microsoft, Oat, Amazon and Twitter are some of the largest players in advertisement targeting with 60-70% market coverage. The device graph is likely developed using fixed user profile (email addresses, login, location, etc) and digital behavior (browsing, interaction with various applications, comments, likes, etc).

There are others in industry that provide advertisement targeting solutions based on probabilisitic methods to determine what their audiences are. Some examples are location data providers Foursquare, music publisher like Pandora, etc. Usually companies develop in-house or collaborate with outside party (examples neustar, etc) to provide identity graph based on IP addresses, Device Id, Location, User agents etc information available from serving an advertisement.

Data Pipeline

In either case there is a need to connect disparate sources and create a holistic device graph pipeline that is promptly available to target, is reliable and provides accurate targeting of growing digital advertisement industry.
Data is understood to be coming from varied sources having their unique schema and delivery timelines. 

Static data sources used here are:
IP and Location data is from: https://lite.ip2location.com/ 
Device ID data with user agent (Device Type, Website, Cookie vs Other Mobile device) information as a function of time is anonymously generated. This data gets collected typically per propriety technology or can be purchased from bid stream of advertisement serving (also can be referred to as impression data).

Since in real scenario, there will be incoming data every second. In this pipeline, created stream of data as real time for processing (via an API or a script).
The extraction, transform and load of static data is joined, cleaned, aggregated and processed for device graph and saved in S3 which is then connected to a database and an API for querying.

In the Transform phase, data is connected as a graph with Device Ids as nodes connected to IPs as edges with a weight. The weight is calculated based on number of times IP, Device Id combination appears and month relative to present it appeared in. Automatically older IP-Devices are weighted less and finally disappears from the list. This also takes care of one of chance appearance of IP-Device combinations. 

This connected graph give companies a platform to target audiences by their usage, user type. This graph can further be used a lift in business due to an advertisement serve. 

Pipeline Flow

<p align="center">
  <img src="Screen%20Shot%202018-07-27%20at%209.27.49%20AM.png" width="1000" title="Pipeline">
</p>
