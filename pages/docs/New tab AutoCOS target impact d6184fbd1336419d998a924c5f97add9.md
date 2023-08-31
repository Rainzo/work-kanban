# New tab "AutoCOS target impact"

Created: August 3, 2021 9:26 AM
Last edited: August 18, 2021 1:22 PM
Owner: Tibor Kese
Status: Done
Engineer: tomas.dedek@glami.cz
Estimation: up to 4 hours
Priority: mid

- put to this workbook as a new second tab - [https://tableau.glami.info/#/workbooks/210/views](https://tableau.glami.info/#/workbooks/210/views)
- Example structure: [https://docs.google.com/spreadsheets/d/1-fcTjbCqTJf_XyKxRRVzl9bUiNXcRjbHOgHs-91KV0c/edit](https://docs.google.com/spreadsheets/d/1-fcTjbCqTJf_XyKxRRVzl9bUiNXcRjbHOgHs-91KV0c/edit)

**Lines:**

- AutoCOS providers

**Columns:**

- **Provider Name**
- **AutoCOS COS Target**
- **Difference to GEO COS target**  = AutoCOS COS target (from previous column) - GEO COS target (from filter)
    - Reasoning: takže si můžu seřadit shopy podle toho, jak vzdálený jsou od targetu na mojí GEO - celkovej AutoCOS target v prioritě máme 21%, ale navrhuju že si to člověk bude moct nastavit ve filtru
- **Exits**
- **Impact on GEO COS target** -
    - Reasoning - tohle je nejdůlěžitější sloupec. Násobí předchozí dva sloupce a tím kombinuje COS traget s objemem exitů. Když si to seřadím od nejnižšího jako ve screenshotu, tak mám nahoře právě ty shopy, který mi ten průměrnej target COS v mojí zemi tahají nejvíc dolů. Díky této metrice vidím, že na GR má například větší impact zvýšit o 1% COS target Factcoolu (z 20% na 21%), než zvýšit shopu [Sneaker10.gr](http://sneaker10.gr/) COS target ze 7% na 21%. Tohle může být kontraintuitivní - kdybych neměl tuhle metriku a řadil bych si to jen podle COS targetu, tak si budu myslet, že nejdůlěžitější je zvednout COS target shopům jako [Sneaker10.gr](http://sneaker10.gr/).
- **BM** - jen FYI pro kontext profitability
- **% of Purchase paired items** - same as we have in this report - [https://tableau.glami.info/#/views/PixelDatareport/Pairing](https://tableau.glami.info/#/views/PixelDatareport/Pairing).  This is nice-to-have, drop if complicated
- **% of Viewcontent paired items** - same as we have in this report - [https://tableau.glami.info/#/views/PixelDatareport/Pairing](https://tableau.glami.info/#/views/PixelDatareport/Pairing).  This is nice-to-have, drop if complicated

**Filers:**

- **GEO**
- **Time period** - start date and end date. COS target always reflects snapshot representing the last day of the period. If this is not possible, then it should reflect the current status (but in that case let me know plz)
- **GEO COS target** - you can select integers - from 19% up to 30%