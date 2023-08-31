# Origin tracking / Offer comparison

Created: June 12, 2023 11:40 AM
Last edited: August 28, 2023 9:24 AM
Owner: Oskar Stierand, Ondřej Čajánek
Status: Validation
Engineer: Michal Smrčina
Priority: mid

**Oskar:**

Hi guys I would like to ask you for few adjustments of this report, which is crucial for us to know better, how offer comparison works.

[https://tableau.glami.info/#/views/AdhocreportsBD-Tibor/OriginTracking](https://tableau.glami.info/#/views/AdhocreportsBD-Tibor/OriginTracking)

I will write all changes like separate posts - can one of you add it to your todo list and let me know when it could be done please?

- ~~A~~
    - ~~1st - add row with sum for each column~~ ✅
- B
    - ~~B1 **General view on Item Grouping per GEO**~~
        - Kolik % produktů máme v itemgroupingu
        - Jak obecně fungují produkty, které mají itemgrouping versus nemají (GMV/s, Revenue, Exit rate, CR)Jak by se celkově snížil počet produktů, kdybychom zobrazovali v katalogu jen jeden produkt z itemgroupingu
        - [ENG]
            - What is percentage of items in grouping?
            - How do items perform grouped/ not grouped: @Ondřej Čajánek doplni
            
            ```sql
            ~~select
                gr.is_grouped,
                count(*)  # add other stats we use in Grouping Tableau
            from klarka_cz.ExitLogFinal e
            left join (
            	select 
            		itemId, 
            		1 as is_grouped 
            	from klarka_cz.Item2ItemGroup  # replace this by that complicated SQL 
            																 # for all items that are active, not ignored in grouping
            															   # if you're not sure, contact Ondra Cajanek.
            ) as gr on e.itemId=gr.itemId
            where e.date = '2023-06-07'  # different time frame?
            group by e.date, is_grouped~~
            
            ```
            
            Updated data pipeline from discussion with @Michal Smrčina 
            
            1. Get all logs for desired day
            2. from logs get all items
            3. classify if item is in grouping, or not → create flag is_grouped
            4. group by on origin, is_grouped flag
            
            ```sql
            select
                ef.origin,
            	gr.is_grouped,
                count(*)
            from klarka_lt.ExitLogFinal ef -- this will be replaced based on desired metric
            left join (
            	select
            		distinct itemId,
                    1 as is_grouped
            	from klarka_lt.Item2ItemGroup  -- this will be replaced by grouped items (filter ignored, single item groups)
            	) as gr on ef.itemId=gr.itemId
            where date='2023-06-13'
            group by ef.origin, gr.is_grouped
            ```
            
            - Result example on LT, exactly from the SQL above
                
                
                | origin | is_grouped | count(*) |
                | --- | --- | --- |
                | 3 | NULL | 12 |
                | 3 | 1 | 9 |
                | 13 | 1 | 3 |
                | 13 | NULL | 2 |
                | 21 | NULL | 4557 |
                | 21 | 1 | 1218 |
                | 22 | NULL | 428 |
                | 22 | 1 | 175 |
                | 23 | NULL | 329 |
                | 23 | 1 | 181 |
                | 25 | NULL | 13 |
                | 25 | 1 | 20 |
                | 26 | NULL | 1190 |
                | 26 | 1 | 324 |
                | 27 | NULL | 27 |
                | 27 | 1 | 3 |
                | 29 | NULL | 251 |
                | 29 | 1 | 147 |
                | 30 | NULL | 13 |
                | 32 | 1 | 5 |
                | 32 | NULL | 4 |
                | 33 | NULL | 14 |
                | 34 | 1 | 2 |
                | 34 | NULL | 1 |
                | 42 | NULL | 850 |
                | 42 | 1 | 323 |
                | 44 | NULL | 12 |
                | 44 | 1 | 14 |
                | 47 | 1 | 5 |
                | 47 | NULL | 8 |
                | 48 | NULL | 3 |
                | 48 | 1 | 2 |
                | 49 | 1 | 24 |
                | 49 | NULL | 40 |
                | 51 | 1 | 3 |
                | 51 | NULL | 2 |
                | 53 | NULL | 1 |
                | 53 | 1 | 4 |
                | 64 | NULL | 38 |
                | 64 | 1 | 11 |
                | 65 | NULL | 62 |
                | 65 | 1 | 17 |
                | 67 | NULL | 21 |
                | 67 | 1 | 4 |
                | 80 | 1 | 31 |
                | 80 | NULL | 87 |
                | 81 | 1 | 1 |
                | 82 | 1 | 1 |
                | 97 | NULL | 2 |
                | 99 | 1 | 2 |
                | 99 | NULL | 7 |
                | 112 | NULL | 5 |
                | 112 | 1 | 6 |
                | 113 | 1 | 1 |
                | 114 | NULL | 23 |
                | 114 | 1 | 3 |
                | 126 | 1 | 1 |
                | 149 | 1 | 1 |
                | 170 | NULL | 3 |
                | 170 | 1 | 3 |
                | 174 | NULL | 2 |
                | 174 | 1 | 1 |
                | 223 | 1 | 615 |
                | 223 | NULL | 996 |
                | 224 | NULL | 724 |
                | 224 | 1 | 267 |
                | 225 | NULL | 3006 |
                | 225 | 1 | 1230 |
                | 226 | 1 | 120 |
                | 226 | NULL | 3 |
                | 227 | 1 | 1 |
            - How would number of products changed if show only groups in catalog:
            
    - B2 **View on Item Grouping per category**
        - V podstatě to samé co v tom reportu výše, ale v pohledu na jednotlivé kategorie
        - Stačí top 2-3 level kategorie
    - B3 **View on performance of products in grouping**
        - ~~Jak fungují produkty podle velikosti itemgroupingu (tj. 2 produkty v groupingu, 3 produkty v groupingu ...)~~
        - ~~Stačí asi udělat nějaké intervaly (2, 3-5, 6-10, víc) nebo podobně~~
        - + rozdělení per device
    - C **Optimization of timely data delivery**
        - reorganizace flows a relevantních jobs pro zajištění včasnějšího doručení dat (
            - orders k dispozici logicky vždy až další den kolem poledne, tranformace běží v 6 ráno, TDE writer po 6 hodin do pozdního odpoledne ← odtud opoždění ← vyladit
    - D **Tableau report polishing (by @Ondřej Čajánek )**
        
        As a side note, I think we are getting a state, we we'd like to start comparing numbers. I'm still not sure about the optimal arrangement, but the current long table (video) does not seem handy to me. What would seem more natural to me, and those are just suggestions, you probably have seen much more reports and can come up with better arrangement.
        
        - select metric and then show just this one metric. we'd like to compare GMV/item for grouped and not grouped items and ideally in graph, we don't want to scroll table and look at numbers that are 5 blocks apart. This could be Similar to what I did here: [https://docs.google.com/spreadsheets/d/1duIBc6Vxf2ERxBU7qpHBYPlGa35gcEsu9GuDlfZAuOk/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1duIBc6Vxf2ERxBU7qpHBYPlGa35gcEsu9GuDlfZAuOk/edit?usp=sharing) and also screenshot.
        - add some color schemes so that we know if those numbers are high/low (this could be used for differences across categories), this is related to the **Alternative presentation** part above.
    - E **Category filter also to Origin**
        - pridat filtr dle kategorii i do tableau: [https://tableau.glami.info/#/views/AdhocreportsBD-Tibor/OriginTracking?:iid=3](https://tableau.glami.info/#/views/AdhocreportsBD-Tibor/OriginTracking?:iid=3)
        - tj. po validaci Grouping, lze přidat i do Origin datasetu
    -