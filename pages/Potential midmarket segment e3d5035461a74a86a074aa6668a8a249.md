# Potential midmarket segment

Created: March 1, 2023 1:08 PM
Last edited: April 11, 2023 4:14 PM
Owner: Matej Višňovský
Status: Done
Engineer: Michal Smrčina
Priority: mid

- [Tiering report](https://tableau.glami.info/#/views/Providertiering/Providertieringreportlast30days?%3Aiid=1) can be duplicated and used for this task
    - exclude columns: Provider tier, GLAMI revenue share + exits+ total items share along Table (Down)

**Filters**

- GEO

**Properties to be added**

- **Total items flag(over 10k items)**
    - Value 1 if Yes, 0 if No
    - Show filter
- **Good Exitrate flag (Exr > 0.8*AVG(Exr)per GEO)**
    - Value 1 if Yes, 0 if No
    - Show filter
- **Good CR flag (over 1%)**
    - Value 1 if Yes, 0 if No
    - Show filter
- **Good AOV flag (AOV > 0.8*AVG(AOV[GEO]))**
    - Value 1 if Yes, 0 if No
    - Show filter
- **Potential MidMarket priority**
    - If all of these are met (**Total items flag(over 10k items)=1, Good Exitrate flag (Exr > 0.8*AVG(Exr))=1, Good CR flag (over 1%)=1, Good AOV flag (AOV > 0.8 AVG(AOV[GEO])) =1**) ****  → Priority 1
    - If 3 out of 4 conditions are met → Priority 2
    - If 2 out of 4 conditions are met → Priority 3
    - If 1 condition is met → Priority 4
    - Show filter (by default show only providers with Priority 1)

## **Logic**

**Provider status = active**

**AND**

`Shop Type`

- Small