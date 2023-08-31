# Data entry click analysis

Created: April 30, 2020 2:33 PM
Last edited: May 19, 2021 5:44 PM
Status: Abandoned
Software: keboola

### Sandbox Snowflake part

- [x]  parse 'data' column to sub-elements
- [x]  clean up empty values and define data types
- [x]  join with smaller table on exit_logs
- [x]  join with exit_logs (cpc, cpc_eur, device)
- [x]  join with orders (orders (to add), gmv, gmv_eur)
- [x]  join with categories → 
by creating one time transformation with the same input and output:
1) add country code to tag_id in [existing table](https://connection.keboola.com/admin/projects/1828/extractors/keboola.ex-db-mysql/215039844/query/23242)
2) add country code to item_id in the same place ?
3) update all the **item_category_id** extractors to include concatenated country code to their tag_id and (?) item_id
- [x]  Add providers data. Add provider_id from exit_log and provider_id + name from providers table
- [x]  create channel grouping
- testing small sample in TBL:
- no glid data → waiting for LR and JN to give us these data
- [x]  create an aggregated table on entry_click_id with exit_logs count
- [ ]  validate → see comments

### Keboola part

- [x]  Done
- create transformation
- schedule a proper orchestration for it
- connect the writer

### Tableau part

- build a report

Miscellaneous:

- ask JN regarding empty sources being 50% of data

- *Ahoj, to je divné, ale nevim. Některé exit kliky to tak mají. Důvod takto z hlavy nevím.*

- ask LR regarding google_cpc campaigns
- To be defined Monday 18.05
- can't aggregate exit clicks because of different providers ⇒ leave providers apart

case when b."data_provider_id" is null or "data_provider_id" = '' then '--empty--' else b."data_provider_id" end as "data_provider_id",

## Requests:

Comments from guys:

- sizes: group by number of sizes
- pull tag type from exit logs and map it
- sale = tag_type "Sale"
- price levels:
    
    [](https://tableau.glami.info/#/views/KPIsbypricelevel/KPIsbypricelevel?:iid=1)
    

Jan: 

- what was clicked out? hightlighted products or something else? from the same category or difffent one?
- traffic performance based by no of sizes of the H product (per category - to have only relevant cats.
- does the perf differ if we show product on sale/voucher or without
- frequency of tags and its perf. per tag_type
- performance of H products per price-level (distinct category)
- in general, which products shouldnt be in feed and which are sure bet

- new/Returning users - i would rather say users with saved cookie from previous visits or without
- data is ok for product view - so sizes, sales can still bring us 100%ly proper picture of entry clicks
- data about source, campaign or GCLID (data from cookie), are not correct and cannot be used
- after DEV will adjust it as we want, we can extract UMT and other parameters from URL, if will find a way how to identify that user is new or returning we can add this info as well (probally we can use what we have now, f.e. if cookie contains anything = YES, if is empty = NO) but we need to ask them to develop it as well

[4:06](https://glami.slack.com/archives/GK7LUKKGR/p1593093985040900)

- also GLAMI testing own web sending request for the web, For example every 10 minutes (or something like that) we send URL with highlight to be sure that everything on the web is working poperly - so this is also something what we should keep in the mind - probably we can have statuses like new/returning/test

![Data%20entry%20click%20analysis%2070962929c2f24ef8b1ea40127984bf27/Untitled.png](Data%20entry%20click%20analysis%2070962929c2f24ef8b1ea40127984bf27/Untitled.png)

Source split last 6 months: 

![Data%20entry%20click%20analysis%2070962929c2f24ef8b1ea40127984bf27/Untitled%201.png](Data%20entry%20click%20analysis%2070962929c2f24ef8b1ea40127984bf27/Untitled%201.png)

1. analyse useless products (no exits)
2. find products that are good in cr ctr 
3. confirm when it was fixed (empty sources)
4. 

### Source is still not right.

1. find cases where # of sizes is changing
2. price ranges