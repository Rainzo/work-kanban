# Connect HubSpot to Keboola and sync properties

Created: January 11, 2022 8:19 AM
Last edited: June 17, 2022 11:34 AM
Owner: Tibor Kese, Matej Višňovský
Status: Done
Engineer: Slava Gatin, tomas.dedek@glami.cz
Priority: high

**1) Verify that connection works**

- Try to sync just one property and verify that there is no technical issue that would fuck this up
- **API token: 3653fa45-b821-4866-9bd9-b057b177d0f3**
- **Frequency of sync:** Hourly
- **Documentation:**
    - documentation for Writer is here: [https://bitbucket.org/kds_consulting_team/kds-team.wr-hubspot/src/master/README.md](https://bitbucket.org/kds_consulting_team/kds-team.wr-hubspot/src/master/README.md)
    - documentation for Extractor is here: [https://components.keboola.com/components/kds-team.ex-hubspot-crm](https://components.keboola.com/components/kds-team.ex-hubspot-crm)

**2) Sync these properties to Keboola**

- List of properties to sync: (be careful about field names - maybe in API doc somewhere?)
    - Contact properties:
        - Email
        - Associated Company - can have more than one value
        - IsContact - values yes/no
        - IsMerchant - values yes/no
        - IsBilling - values yes/no
        - First Name
        - Last Name
        - Phone Number
    - Company properties
        - Name
        - Associated Contact - can have more than one value
        - Company Domain Name