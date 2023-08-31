# Checkout ROI per provider report

Created: October 13, 2022 12:10 PM
Last edited: November 14, 2022 9:00 AM
Owner: Pavel Hůza
Status: Done
Engineer: Kate Usova
Priority: mid

### What do you want to see and why?

We need this report to be able to evaluate the performance of GCO (Glami Checkout) campaigns for each provider.

### How it should look?

The report should look similarly as presented in this google sheet

[https://docs.google.com/spreadsheets/d/16whk9Or0VuYRTna6ESC4UIcLOoGfdW00EUoS1Z1im5U/edit?usp=sharing](https://docs.google.com/spreadsheets/d/16whk9Or0VuYRTna6ESC4UIcLOoGfdW00EUoS1Z1im5U/edit?usp=sharing)

Columns

- **Provider name & ID**

Rows

- **Campaign costs** - Data from Google Analytics (all campaigns where campaign name containing `GCO` & campaign `Google Ad Group` equals string “PROVIDER_ID - PROVIDER_NAME” ie. “4506 - Fashionsugar.cz”)
- **Clickout revenue** - Data from Google Analytics (all campaigns where campaign name containing `GCO`, conversion origin is equal `clickout` and campaign `Google Ad Group` equals string “PROVIDER_ID - PROVIDER_NAME” ie. “4506 - Fashionsugar.cz”)
- **Checkout revenue** - Data from Tableau - Report `Checkout P&L` - row `Glami revenue aka Glami Fee`
- **ROI** - `(Clickout revenue + Checkout revenue) / Campaign costs`

Option to view data for weeks / months / years

### How frequent you will use this?

It is regular report which will be checked once a month

### How much past data you will need?

Current year