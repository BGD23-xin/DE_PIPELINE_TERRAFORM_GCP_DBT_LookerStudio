## Configuration of DBT

## 1.configuration of DBT

This part is very simple. we could use the DBT cloud IDE to trait the data in the bigquery.

Firstly, we need create an account on the [site](https://www.getdbt.com/lp/free-account?utm_medium=paid-search&utm_source=google&utm_campaign=q1-2026_emea-fran-brand_cv&utm_content=_dbt-ex___&utm_term=all_emea__&utm_term=dbt&utm_campaign=q2-2024_us-brand_cv&utm_source=adwords&utm_medium=ppc&hsa_acc=8253637521&hsa_cam=22162285891&hsa_grp=174909487178&hsa_ad=730395869753&hsa_src=g&hsa_tgt=kwd-95889999&hsa_kw=dbt&hsa_mt=e&hsa_net=adwords&hsa_ver=3&gad_source=1&gclid=CjwKCAiArKW-BhAzEiwAZhWsIHZSY4VHs_pztRQJIC22ISDNCH4uSPSG_mtnNF4H9bVsNdV6QZdlNxoCarsQAvD_BwE#signup):

Secondly, we need to need generate a security keys of our service account on the bigquery.
![photo](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/blob/operations/photos/create_keys.png)

Then download it and upload into DBT, which is for DBT connecting to the bigquery.

If you want to configure for connecting github, you need to copy the URL of directory of your project , then DBT will generate a ssh key, you must use it to create a public ssh key on github.

## 2.Creation of sql models

After creating a project on the DBT, we could initialize the project to generate files automatically.(we could also run dbt init in our terminal to create) 

For the treatment, it is very simple. We just need to create follow files:
- 1.Schema.yml
- 2.Sql_files
Those files must be stored under the directory of models. The file Schema.yml is use to store the information of sources of data.(this project i use the dataset of bigquery.)

The files of sql are just the sql code of treatment. We could then run the follow code to execute project

```bash
dbt build --select sql_file --vars '{'is_test_run':false}'
```

`--vars '{'is_test_run':false}'` this code is one command in the bottom of sql file. Its default value is True. That means it will run just 100 rows (which depends on our definition). this is for the test.

Ps. if we want to upload a csv file which is not big. we could create store this file under the directory seeds. Then building it, it will create automatically on bigqeury.

Finally, we could see in linage, the relationship of all the sql files,which could help us easily repair and check. 
![photo](https://github.com/BGD23-xin/DE_PIPELINE_TERRAFORM_GCP_DBT_LookerStudio/blob/operations/photos/dbt_final_schema.png)