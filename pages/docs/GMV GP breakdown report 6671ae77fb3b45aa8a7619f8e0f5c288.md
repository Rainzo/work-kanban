# "GMV/GP breakdown" report

Created: August 3, 2021 9:28 AM
Last edited: August 19, 2021 2:49 PM
Owner: Tibor Kese
Status: Done
Timeline: August 3, 2021 → August 13, 2021
Software: Tableau
Engineer: Slava Gatin
Estimation: up to 8 hours
Priority: mid

**The report should have two graphs, for GMV and for GP:**

![GMV%20GP%20breakdown%20report%206671ae77fb3b45aa8a7619f8e0f5c288/Untitled.png](GMV%20GP%20breakdown%20report%206671ae77fb3b45aa8a7619f8e0f5c288/Untitled.png)

![GMV%20GP%20breakdown%20report%206671ae77fb3b45aa8a7619f8e0f5c288/Untitled%201.png](GMV%20GP%20breakdown%20report%206671ae77fb3b45aa8a7619f8e0f5c288/Untitled%201.png)

**Filters:**

- Switcher that will influence what we will be comparing the numbers to (what percentage change will be shown):
    - Actual vs Forecast (default)
    - Actual vs YoY
    - Actual vs MoM
- GEO (by default we see All GEOs)

- Example in sheets - [https://docs.google.com/spreadsheets/d/1u3HfiCqyoeaOX7PaNsxgWiGq62PDol75EuMon-Cwjz0/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1u3HfiCqyoeaOX7PaNsxgWiGq62PDol75EuMon-Cwjz0/edit?usp=sharing)
- Should be added to "Glami general" section, either to workbook All GLAMI, or a separate workbook

**Reasoning:**

- This is for whole leaderhip group and company, requested by Tomas
- Příklad insightů za červen, které bychom na první pohled viděli v takovýmto breakdownu:
    - GMV
        - Drží se těsně nad forecastem jen díky tomu, že AOV je mnohem vyšší, než jsme forecastovali
        - Za to objemy táhnou GMV dolů - jsme pod forecastem na Sessions, Exit Rate i Conversion Rate, proto málo objednávek
    - GP
        - Negativně se podepsaly tři faktory (zhruba podobným dílem) - méně prodaných exitů, nižší CPC-out, vyšší CPC-in
        - Náklady bly ale celkově menší než forecastované, kvůli popadu sessions
- Mám pocit, že by to pomohlo například při
    - rychlýmu pohledu Tomas Hodbod / Jan Keselak na celý GLAMI, jaký metriky nám high-level vycházejí a jaký ne
    - rychlým pohledu Country managers na svoji zemi - jaký drivery ovlivňují nejvíc (ne)úspěch
    - měsíčním přehledu od CFO Terky