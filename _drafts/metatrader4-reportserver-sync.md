---
layout: post
title: A faster way to resync an out of sycned mt4 report server
date: 2020-08-05T00:08:11.000Z
tags:
  - metatrader 4
  - mt4
  - report server
  - hack
---

Metaquote provides a tool for brokers to export their MT4 server data into MYSQL or Postgre server. However, due to its legacy-ness , its synchronisation could have issues from time to time.
The build-in functions does not include a "fix sync issues" function.
Normally people will just do a **resync**, which will resync the database from the beginning of time. This process usually take ages, depends on the number of trades and history, it may take up to several hours.

In many cases we know that up to a point in time the data integrity is intact. If we could just resync from that point, we could reduce the resync process. And I just got the exact method how you can do that.

## How it works
The MetaQuote mt4 report server works by reading data from an MT4 server and writing them into the database. It uses timestamps to keep tract of its synchronising process

## Requirements:
1. full access to the database that the report server is running on
2. have access to the "report server" synchronisation application so that you can stop and start the service.

## Steps:
1. Stop the synchronization application / Service
2. Updating the database.
    - There is a table named "mt4_config" under the database schema.
    - There are 5 rows of data:
        - the first row contains the timestamp of the trades
        - the second row contains the timestamp of the daily records
        - the rest, I have no idea
    - Now, if you have out-sync problem only in the mt4_trades table, then change the trade timestamp to the time that you want the synchronisation to continue from. The same for the mt4_daily table, change the daily time stamp.
3. Restart the service.
4. Check the log of the service to see it is reading the right timestamp. (Optional)

Now just wait until the synchronisation to complete.

## Causes
From my experience, there are some known issues that can cause the MT4 report server to out of sync
1. Network condition between MT4 dc and the Report Server
    - Ideally, The report server should be physically closer to the main server as possible
    - The connection quality between the database and report server is less important
1. Not enough computing resources: CPU/Memory/Network
