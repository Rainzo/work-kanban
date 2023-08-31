# Create HubSpot reports

Created: January 11, 2022 8:14 AM
Last edited: October 24, 2022 9:21 AM
Owner: Tibor Kese, Matej Višňovský
Status: Done
Engineer: Slava Gatin
Estimation: up to 4 hours
Priority: high

**Report 1: Contact-Company Inconsistencies**

- [https://docs.google.com/spreadsheets/d/1J5s9Lb20og1F-Gi_TcdI2FCVc7hEpEDYVZjEhes2W3Y/edit#gid=0](https://docs.google.com/spreadsheets/d/1J5s9Lb20og1F-Gi_TcdI2FCVc7hEpEDYVZjEhes2W3Y/edit#gid=0)
- **Data Sources:** HubSpot and Klarka
- **Lines:** Email addresses
- **Columns:** see in sheet above
- **Filters:** see in sheet above
- **Open question:** Tableau report or Google Sheet?
- **Rules for Associated Companies check:**
    - The check should ideally look like this:
        - Check GEO and provider ID (ex. cz-123, found in property Provider Id) from HS, compare to GEO and provider ID from Klarka:
        
        If there is no match, surface the name (ID optional). If possible we would like to see also IDs of the companies with issues
- Feedback exchange:
    
    Hey Slava, I went over a part of the report and I have some points, I downloaded the report and worked with it in [sheets](https://docs.google.com/spreadsheets/d/1YrHLfgc2VIFUZORekSv2xNF3soGjV9foGqfTnQF-JvY/edit#gid=0) in order to be able to leave some comments. Together with Tibor we compiled these additional points:
    
    1. Inconsistency type - is there anything you need from our side? I am happy to help you with the context of this, just let me know if anything is unclear
    2. Is it possible to have one email per row in this report? It would be great to see all `email_types_klarka` in one cell per email address, this would help us identify, what the inconsistency is.
    3. We would also like to see provider status in Klarka, possibly with ability to show the filter in the report. By default, we would like to have excluded banned, blocked and deleted statuses from the report (also visible in the filter).
    4. In row 28 of the sheet, we can see an email that has email type in both Klarka and HS as billing - for this one, we do not want to check any inconsistencies regarding first, last name or phone (this is actually correct, because billing and merchant emails do not have phone numbers nor names in Klarka)
    5. Is it possible to group email addresses together by provider_id? I found some cases where merchant and contact emails were in the report together, but the billing contact was far from them (around 20k lines away  )
    6. I added comments in the sheet, feel free to go over them and see my notes.
    
    Please let me know should you have any questions, I will be more than happy to explain in depth if needed
    
    1. If comparison between columns after the data is cleared
    2. email per row
    3. status as a filter
    4. take name and phone from the contact email_type
    5. done in tbl
    6. if merchant and contact => display “billing is missing” and other variations

---

**Report 2: Company Domain Name**

- [https://docs.google.com/spreadsheets/d/1J5s9Lb20og1F-Gi_TcdI2FCVc7hEpEDYVZjEhes2W3Y/edit#gid=200265599](https://docs.google.com/spreadsheets/d/1J5s9Lb20og1F-Gi_TcdI2FCVc7hEpEDYVZjEhes2W3Y/edit#gid=2002655996)
- **Data sources:** only HubSpot
- **Lines:** Combination of Company and Associated Contact (only problematic ones, see rules)
- **Columns:** see in sheet above
- **Filters:** see in sheet above
- **Rules when to show a problematic record:**
    - 1) None of Ass Emails matches current Company Domain Name
    - 2) None of Associated Companies to this email have current Company Domain Name

**Report 3: Records from Klarka in HubSpot**

- [https://docs.google.com/spreadsheets/d/1J5s9Lb20og1F-Gi_TcdI2FCVc7hEpEDYVZjEhes2W3Y/edit#gid=364841325](https://docs.google.com/spreadsheets/d/1J5s9Lb20og1F-Gi_TcdI2FCVc7hEpEDYVZjEhes2W3Y/edit#gid=364841325)
- **Data Sources:** HubSpot and Klarka
    - For Companies: Only Klarka
    - For contacts: Compare Klarka and HubSpot based on emails
- **Lines:** GEOs
- **Columns:** see in sheet above
- **Filters:** see in sheet above