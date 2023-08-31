# Guys don’t have yesterday Revenue/Cost data in the morning

Created: February 17, 2022 3:41 AM
Last edited: August 23, 2022 12:34 AM
Owner: Anastasiya Ivanova, Barbora Vrbíková, Anna Kapitanová, Zuzana Drápalová
Status: Done
Software: keboola
Engineer: Slava Gatin
Estimation: up to 8 hours
Priority: highest

### Keboola mysql extractors:

It seems that the table in.c-main.items2tag (and possibly others) is under pressure, between midnight and 5 am last night there were at least 20 import jobs and they cannot run in parallel. Their execution has to be serialized and the jobs are picked up from the queue in a random order, that's why the times vary.

To make it more stable and predictable I would suggest decreasing number of imports into this table in the time frame.

###