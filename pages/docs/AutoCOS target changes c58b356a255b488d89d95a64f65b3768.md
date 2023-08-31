# AutoCOS target changes

Created: August 10, 2021 11:07 AM
Last edited: September 13, 2021 9:13 AM
Owner: Tibor Kese
Status: Done
Engineer: tomas.dedek@glami.cz, Slava Gatin
Priority: mid

- add new tab "**AutoCOS target changes**" to this workbook: [https://tableau.glami.info/#/workbooks/210/views](https://tableau.glami.info/#/workbooks/210/views)

**Rows:** Every change in AutoCOS targets across GEOs

**Columns:**

- Provider Name
- Date of change
- COS target Old
- COS target New
- Who changed

**Filters:** 

- GEO
- COS target NEW - select lower and upper value, for example I want to see only changes with new COS target set between 0% and 19%
- Date of change - select two dates between which I want to see changes, for example between 1.8. and 9.8.

**We save all of these information, because we have them per provider in History values table, for example here: [https://www.glami.cz/klarka/provider/setcos/21/](https://www.glami.cz/klarka/provider/setcos/21/)**

![AutoCOS%20target%20changes%20c58b356a255b488d89d95a64f65b3768/Untitled.png](AutoCOS%20target%20changes%20c58b356a255b488d89d95a64f65b3768/Untitled.png)

Note: please let me know if this would be too doffocult, we can

**Reasoning:** 

- Helps with key MD priority to increase COS targets
- Další nápad na report k naší prioritě COS targetů u AutoCOSu. Připadá mi, že abychom naučili tým, jak s tím AutoCOSem pracovat, **měli bychom mít možnost vidět všechny ty změny COS targetů**. Abyste vy měli přehled, jak se ve Vaší GEO COS targety mění, a pokud by se třeba nějakej změnil dolů z 20% na 15%, abyste mohli ten konkrétní case vidět.

**Potenciální use cases:**

- Pokud by se COS target u nějakýho shopu změnil dolů z 20% na 15%, hned to CM uvidí, a můžete si s BD manažerem ověřit, že to mělo pádnej důvod, a jestli jsme fakt neměli jiný kroky, který by se dali udělat
- přehled jak efektivně pracuje BD manažer na změnách tragetů
- přehled u kterých providerů se povedl úspěch