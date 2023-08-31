# AutoCOS regular check

Created: August 10, 2021 11:06 AM
Last edited: September 22, 2021 2:34 PM
Owner: Tibor Kese
Status: Done
Software: Tableau, keboola
Engineer: tomas.dedek@glami.cz
Estimation: up to 4 hours
Priority: mid

- Add new tab "AutoCOS regular check" to this workbook: [https://tableau.glami.info/#/workbooks/210/views](https://tableau.glami.info/#/workbooks/210/views)
- Will be similar structure to this tab, maybe you can copy it first and then modify: [https://tableau.glami.info/#/views/AutoCOSSmartCOSguarantee/AutoCOSprovidershighlight](https://tableau.glami.info/#/views/AutoCOSSmartCOSguarantee/AutoCOSprovidershighlight)  After a while we can probably archive the original table.

**Rows:** All providers on AutoCOS

**Columns:**

- **~~Status** - simply current status of provider~~
- **~~Paid vs free** - can be same column as in original table~~
- **~~AutoCOS target -** can be same column as "Auto cos" column in original table~~
- **~~Min COS target** - calculated as [Min COS target % (in Filter)] * [Base COS (30 days)]~~
- **~~Base COS (30 days)~~**
- **~~BM (30 days) -** can be same column as in original table~~
- **~~COS (30 days)-** can be same column as in original table~~
- **~~COS (30 days, difference vs target)** **-** can be same column as in original table~~
- **~~Rank -** can be same column as in original table~~
- **~~Orders (desktop+tablet, 60 days)~~**
- **~~Orders (mobile, 60 days)~~**
- **~~Exits (30 days)~~**
- **~~MMF** - same value as column "MMF" from this table. [https://www.glami.cz/klarka/provider/](https://www.glami.cz/klarka/provider/)~~
- **Tracking Type** - same value as in column "Tracking Type" from this table: [https://www.glami.cz/klarka/stats/providers/](https://www.glami.cz/klarka/stats/providers/)
    - The column "Active tracking" from original table is not enough, because it doesnt distinguish between PX1 and PX2
- **~~Pixel Purchase pairing** - same value as here: [https://tableau.glami.info/#/views/PixelDatareport/Pairing](https://tableau.glami.info/#/views/PixelDatareport/Pairing)~~
- **~~Pixel ViewContent pairing** - same value as here: [https://tableau.glami.info/#/views/PixelDatareport/Pairing](https://tableau.glami.info/#/views/PixelDatareport/Pairing)~~

**Filters:** 

- **These three:**

![AutoCOS%20regular%20check%205a1c8a14541e4081864ad32e344ea7e8/Untitled.png](AutoCOS%20regular%20check%205a1c8a14541e4081864ad32e344ea7e8/Untitled.png)

- **Min COS target %** - select % (min 1%, max 100%). By default set to 70%.

**Rationale**

- We change waysw e work with AutoCOS? and we create new guidelines for chekcing exieting shops on AutoCOS - [https://www.notion.so/glami/AutoCOS-Guidelines-existing-shops-5a0f860e0de342bdbbca37933560551c](https://www.notion.so/AutoCOS-Guide-Existing-shops-5a0f860e0de342bdbbca37933560551c?pvs=21) . We need this report to support the rules.