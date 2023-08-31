# Different autocos Variants

Created: January 25, 2022 1:10 AM
Last edited: February 16, 2022 2:03 AM
Owner: Denis Duránik
Status: Done
Software: keboola

- Hello guys, we have new toll available in klarka, A/B/C [variants](https://www.glami.sk/klarka/provider/setcos/26/) of Autocos (yes like viruses :D) and we need to start tracking it from database.
    - differentiate variants for A/B/C testing purposes, it means store information which shop in which date was switched to which variant
    - store snapshots of variants ?
    - to be bale filter and see differencies between variants. For example from 01.02. - 28.02. we should be bale track results (aCOS, tCOS, GMV, cr%, revenues, etc) for each variant and compare
    
    Specific reports will be defined, now we need get informations from database ?Thank you
    

**First thing should be duplicated** report: [https://tableau.glami.info/#/views/AutoCOSSmartCOSguarantee/AutoCOSprovidershighlight?:iid=2](https://tableau.glami.info/#/views/AutoCOSSmartCOSguarantee/AutoCOSprovidershighlight?:iid=2)

- with a possibility to filter only based on variant (I want to see only shops with a variant C)
- filter for a specific period 01.01.2022 - 31.01.20222 with a specific variant