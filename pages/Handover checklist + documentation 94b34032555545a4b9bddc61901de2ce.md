# Handover checklist + documentation

Created: December 16, 2021 3:40 PM
Last edited: October 11, 2022 10:54 AM
Status: Done
Engineer: tomas.dedek@glami.cz, Slava Gatin
Priority: high

- [x]  Tableau user switch + licences setup - Tomas
- [ ]  Server optimisation follow up - no reply from the guys yet (October 11, 2022)(@Slava Gatin)
- [x]  Tableau customer portal - Tomas
- Drop Tomas in Tbl users - January
    - [x]  Done

---

- Tableau extracts
    - extracts:backgrounder and **jobs** on tableau (only 2 simultaneous jobs)
    - schedules 1,2,3,5 - 6 exracts in total - FB_ga, fb_insights_ga,
    - how to create: connect to snowflake dataset and
    - Classic extractor: not using custom SQL but using **tableau Join (simple SQL join in front end) -** exit_log_join w/o items - 7 months only. Drag and drop tables without aggregation (no queries). Possibility of publishing as live and change on Server to extract. Old way: in Notion
    - **SQL custom query:** querying snowflake storage to create extracts and Query - anything
    - Snowflake did not finish before extract refresh! Monitor these in Schedule tbl + Writers in kbc
    - Exit_log_join
    - [https://www.tableau.com/about/blog/2013/9/easy-empty-local-extracts-25152?signin=ae4e8eebbacb15523d6fb5b8d8ba404b](https://www.tableau.com/about/blog/2013/9/easy-empty-local-extracts-25152?signin=ae4e8eebbacb15523d6fb5b8d8ba404b)
- [x]  Done
- Tableau VM server
    
    How to clean and restart the server
    
    1. Microsoft remote (Name is IP, then login + pass from 1password)
    2. If server is degraded → clean and restart in command prompt:
    - tsm stop
    - tsm maintenance cleanup
    - tsm start
- [x]  Done
- KBC - all extractors switch
    - fb pages + ad accounts (fb + adwords + instagram) (both)
        
        FB Pages Extractor: 
        - add a person to the admin for all FB pages (ask someone from Social Media to do that) 
        - add a person as an admin to the Glami app in Meta Developers ([https://developers.facebook.com/apps/736431110212318/roles/roles/](https://developers.facebook.com/apps/736431110212318/roles/roles/))
        - reset old authorisation. New person should reauthorise using instant approach (first option).
        
    - [x]  Done
    - google sheets + google drive
    - [x]  Done
    - GA + ad_words
        
        GA extractor: custom oath method to be used to have dedicated api requests limit. To be found under keboola - business connection here: [https://console.cloud.google.com/apis/credentials/oauthclient/249010692593-0ac0bj611a5kptvfilmu9015852ifa2t.apps.googleusercontent.com?project=glami-ga](https://console.cloud.google.com/apis/credentials/oauthclient/249010692593-0ac0bj611a5kptvfilmu9015852ifa2t.apps.googleusercontent.com?project=glami-ga)
        
    - [x]  Done
    - instagram - need FB accesses
    - [x]  Done
    - Mailchimp
- [x]  Done
- KBC - transformations overview 1 by 1
    
    Upload tutorials here.
    
- [x]  Done
- KBC - consumptions overview
    - 1600 credits a month, 53 credits / day
    - Transformation: 6 credits per hour.
    - Writers: DATA based, 1 cr / ~0.01 GB => ~5% per day
    - KBC gives us credits back after they switched from S to L snowflake but transformations are still slow. KBC can come to us and say that we spend too much
    - Optimize keboola SOON.
- [x]  Done
- Tableau - hard dashboard overview 1 by 1
    - Discounted x not discounted products:  (discount flag contains “trac_flag” : 102)
    - Discover: Tag_id count as items, by geos, back in stock products, cohorts
    - Checkout: checkout orders and checkout order items
    - Glamidays: separate x-td transformation, only using exits and orders of glami days items for specific dates. Separate writer as well. Once per year
    - Glami scout - track flag based. Column order - poradi.
    - Items-full for fresh data, item main proc time stamp (main_proc = main + conversions rate and brand)
    - Mobile: out.mobile
    - MySize: my size transformation. Size exits from tag report
    - Product CoS: products with high COS
    - Registered users: is-account-user: 0 (I.e 1 - end customer)
    1. Users likes in Tbl
    
    Visual serach report - potentially to bin (check extracts) based on type of exits by origin
    
    Brand:
    
    Email newsletter - email newsletter report
    
    Brand ads report (ask if they need)
    FB pages official (ask if they need)
    Sustainable fashion stats - main proc in the end
    
    Content:
    Content KPIs: exit_log_ based (referrer)
    Exits by LP: referrer based
    Item likes (again!)
    tag report - tag report dataset!
    
    CM:
    Multiple dimensions - same logic as metadata report
    pricing and channels & cats - ask which one is needed
    reviews - ask if needed
    
    Unused:
    Exit log meta data: weighted stuff (autocos_providers channels)
    Bizdev:
    Pixel data quality - Pixel data report (glam pixel stats)
    Provider tiering
    
- [x]  Done

---

- [x]  Inspigroup - podklady - January (with Tereza)
- [x]  Inspigroup - affiláci - January (with Tereza)
- [x]  Inspigroup - vyhodnocení + navázané reporty - January (with Tereza)
- [x]  Affiliates credentials to 1pass
- [x]  Monthly billing and unused credits - dev to change the email address
- [x]  Tableau licences activation