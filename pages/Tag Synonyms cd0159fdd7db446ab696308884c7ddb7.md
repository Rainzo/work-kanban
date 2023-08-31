# Tag Synonyms

Created: January 28, 2021 4:40 PM
Last edited: April 20, 2021 10:16 AM
Status: Done
Software: keboola
Engineer: Slava Gatin

### Extracting

TagSynonym
Tag2Synonym
Tag2GoogleAds
3 more columns in Tag: `singular`,`grammaticalGender`,`grammaticalCountability`
TagSynonymDeclension
TagDeclension
DeclensionSettings

- [x]  Done

Will need:

- TagConnection →

```sql
SELECT t.tagId, t.title, tc.tagIdMaster AS 'czTagId', tga.name 
FROM klarka_bg.Tag t 
JOIN klarka_bg.TagConnection tc ON tc.tagIdSlave = t.tagId AND tc.country = 'bg'
JOIN kg.Tag2GoogleAds tga ON tga.tagId = tc.tagIdMaster
```

- Category →

[Keboola Connection | Keboola Connection](https://connection.keboola.com/admin/projects/1828/storage-explorer/in.c-main_proc/category)