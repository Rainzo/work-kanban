# Create report “Source coeff changes model”

Created: February 20, 2022 5:50 PM
Last edited: November 10, 2022 11:33 AM
Owner: Tibor Kese, Matej Višňovský
Status: Done
Engineer: Slava Gatin
Priority: high

**Sheet with explanation:** [https://docs.google.com/spreadsheets/d/18BBbvgzXvTSggqHNSJ4ZqGZ55V2-skyDlclvKgnUxlo/edit?usp=sharing](https://docs.google.com/spreadsheets/d/18BBbvgzXvTSggqHNSJ4ZqGZ55V2-skyDlclvKgnUxlo/edit?usp=sharing) 

**Principle:**

- You input new values of source coefficients per channel
- And the report shows you new values of COS and CPC (how it would change per channel with new source coeffs) on past data
- It assumes that no other parameter would change (traffic, GMV, CRs, etc.) - all stays the same expect source coeffs

**Lines:**

- Sources (channels)

**Columns**

- see sheet above

**Filters:**

- see sheet above

**Logic behind calculations:**

- it is visible in second sheet - but lets talk this through on a call

### Note for self:

- we need to add source coefficient from the table [https://connection.keboola.com/admin/projects/1828/storage/in.c-main/source_cpc_coefficient#data-sample](https://connection.keboola.com/admin/projects/1828/storage/in.c-main/source_cpc_coefficient#data-sample) to two outputs: 
1. out.source_coefficient_7 (line 951)
2. out.source_coefficient_14 (line 962)
inside Channels [transformation](https://connection.keboola.com/admin/projects/1828/transformations/bucket/218763689/transformation/673447800)
- joins should be done on Source and date level
- Source is defined in the table tmp.source_coefficient (line 722) and tmp.providers_autocos_sources (line 797) - they should be redefined based on the source_cpc_coefficient sources
- aggregation on provider level is not necessary for the task