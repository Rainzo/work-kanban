# Write the data into the output table in User segmentation transformation

Created: February 23, 2023 8:55 PM
Last edited: February 23, 2023 9:44 PM
Owner: Kate Usova
Status: To-do

Tranformation: [https://connection.keboola.com/admin/projects/1828/transformations-v2/keboola.python-transformation-v2/952985244](https://connection.keboola.com/admin/projects/1828/transformations-v2/keboola.python-transformation-v2/952985244)

**Problem:** transformation fails to write the output file into the output table raising “File 'emails_user_segments.csv' not found” error.

1. pd.to_csv works only in the sandbox but fails in the transformation itself
2. CSV dialect (as suggested in Keboola documentation: [https://help.keboola.com/transformations/python/](https://help.keboola.com/transformations/python/)) also works only in the sandbox generating the file, but fails in the transformation
    
    Code used is commented in the code block itself as per below:
    
    ```python
    csvlt = '\n'
    csvdel = ','
    csvquo = '"'
    with open('out/tables/emails_user_segments.csv', mode='wt', encoding='utf-8') as out_file:
        writer = csv.writer(out_file)
        writer = csv.DictWriter(out_file, dialect='kbc', fieldnames=['db', 'user_id', 'user_segment'])
        writer.writeheader()
    
        for index, row in fin_data.iterrows(): 
        	writer.writerow({"db": row['db'], "user_id": row['user_id'], "user_segment": row['user_segment'] })
    ```
    

![Screenshot 2023-02-23 at 21.59.28.png](Write%20the%20data%20into%20the%20output%20table%20in%20User%20segme%20fdaa717c6bf94ee1aa5dc9f669f89f12/Screenshot_2023-02-23_at_21.59.28.png)

Failed job details: [https://connection.keboola.com/admin/projects/1828/jobs/953450101](https://connection.keboola.com/admin/projects/1828/jobs/953450101)

1. Tried the solution from Keboola community Q&A: [https://community.keboola.com/post/python-transformations---saving-data-to-out-tables-problem-62f66af87e37264d28351295](https://community.keboola.com/post/python-transformations---saving-data-to-out-tables-problem-62f66af87e37264d28351295)

ommitting the output table and writing the file directly to the destination (slightly modified as per [documentation](https://docs.python.org/3/library/io.html) using `writelines` instead of `write` as I need the list of lines to be inserted)

```python
from keboola.component import CommonInterface

# init the interface
ci = CommonInterface()

# create container for the result
result_table = ci.create_out_table_definition('emails_user_segments.csv', destination="out.c-tbl_prep.emails_user_segment")

# write some content
with open(result_table.full_path, 'w') as result:
  for index, row in fin_data.iterrows(): 
    	result.writelines([row['db'], row['user_id'], row['user_segment']])
```

Job details: [https://connection.keboola.com/admin/projects/1828/jobs/953455323](https://connection.keboola.com/admin/projects/1828/jobs/953455323)

From the log it is visible that the file was actually uploaded, however, the job keeps running for ages stuck at the stage “Waiting for 1 Storage jobs to finish” where I have to manually terminate it

![Screenshot 2023-02-23 at 22.05.23.png](Write%20the%20data%20into%20the%20output%20table%20in%20User%20segme%20fdaa717c6bf94ee1aa5dc9f669f89f12/Screenshot_2023-02-23_at_22.05.23.png)