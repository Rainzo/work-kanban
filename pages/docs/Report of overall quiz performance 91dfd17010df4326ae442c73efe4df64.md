# Report of overall quiz performance

Created: June 7, 2022 4:01 PM
Last edited: October 17, 2022 12:24 PM
Owner: Jakub Eliáš
Status: Done
Timeline: June 8, 2022 → July 31, 2022
Engineer: Kate Usova
Priority: mid

We want to create a report with overall numbers of quiz performance.

[Simple example table with data sources here](https://docs.google.com/spreadsheets/d/1RBOIdDtIQfjD4aKWOQdQ1Nyt8wWeHwHzwEGZWGY5-QE/edit#gid=1075167682)

**Report should allow us to:**

- Filter based on date (we can use already in use date picker in Tableau)
- Filter based on device (ideally distinguish desktop web and mobile web, if not possible, only web)
- Filter based on GEOs

**Report should include:**

- Total of all genders selected
    - Female gender count
    - Male gender count
- Total brand like from quiz
    - Avg number per user from quiz
- Total sizes selected from quiz
    - Avg number per user from quiz
- Total product likes from quiz
    - Avg number per user from quiz
- Total finished quiz
- Total registered users that finished the quiz

Sources task from dev: 

ALTER TABLE

```
GuestTagLike
```

ADD COLUMN

```
source
```

tinyint UNSIGNED DEFAULT NULL;

ALTER TABLE

```
UserTagLike
```

ADD COLUMN

```
source
```

tinyint UNSIGNED DEFAULT NULL;

### Comments:

case "idProfile"
when '76214327' then 'CZ'
when '184822567' then 'BG'
when '171616401' then 'TR'
when '171624390' then 'GR'
when '184882373' then 'HR'
when '159249074' then 'HU'
when '149473193' then 'RO'
when '171618759' then 'RU'
when '129619770' then 'SK'
when '184969812' then 'SI'
when '95479154' then 'ES'
when '198598681' then 'ECO'
when '216462358' then 'LV'
when '216492951' then 'LT'
when '216433021' then 'EE'
when '81960282' then 'DE'
when '99404979' then 'FR'
when '198605994' then 'BR'
when '94338637' then 'IT'
end as "country",