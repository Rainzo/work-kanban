# Categories, providers, # of products and exits

Created: July 17, 2021 10:07 AM
Last edited: August 26, 2021 6:51 AM
Owner: Zuzana Drápalová
Status: Done
Software: Tableau, keboola
Engineer: Slava Gatin
Estimation: up to 4 hours
Priority: low

**What the tableau report could look like:**

It should be built based on our tags (not sure if we can have all tags, but at lease categories would be great) and give us option to filter providers based on how many of their products have the given tag. In a filter I could select for example 10 tags and a trashold of at least for example 20 products of provider with the given tags - table would return list of providers. We also should include amount of provider exits in the category and provider ID.

- using exits would be an option as well, but is not only relevant aspect - it might happen provider with big catalog is on free and hence some product are not active/have few exits. Those are exactly the ones we would need to target with upsell more. Not sure how big problem the size of the database is, but I would prefer to have both metrics present in the report.
- if we would be looking at the data by amount of products in the tag, I think average per L60 days would do, we can keep the range even shorter, if that will help anything..