# Row_Count_Tracing

This tool is provide to tracing the source and target by specific data range.

## Prerequisite
	Please check the below software,SDK,python package in your deveoplment environment
1. 	install Oracle-client from sam
2. install MTDSM and use it to setting Oracle ODBC driver in your development environment
3. install Anaconda3 from sam or install python version 3.8.8 
4. install python-jupyter notebook
```
pip install jupyter --proxy http://proxy-web.micron.com --trusted-host pypi.python.org --trusted-host files.pythonhosted.org --trusted-host pypi.org	
```
5. install python-pandas 
```
pip install pandas --trusted-host pypi.org --trusted-host files.pythonhosted.org --proxy http://proxy-web.micron.com:80
```		
```
pip install pandas-gbq --trusted-host pypi.org --trusted-host files.pythonhosted.org --proxy http://proxy-web.micron.com:80
```
```
pip install pyarrow --trusted-host pypi.org --trusted-host files.pythonhosted.org --proxy http://proxy-web.micron.com:80
```
6.Install python-pandas install GCP-SDK [Link](https://confluence.micron.com/confluence/display/GCPHELP/Install+Cloud+SDK+on+Windows)
```
"gcloud info" - a Google Cloud SDK properties
```
```
"gcloud projects list" -a list of Google Cloud projects
```
```
pip install --upgrade google-api-python-client
```

## How to use 
	1. Download code from git 
	2. Start jupyter notebook
	3. Revise "Query Criteria Settings" markdown area in jupyter 
	4. Run every block in jupyter.

## JSON fromat description
:::info
- **gcp_project**: please input the project name that you can access in gcp
* **sql_pattern**: Provide SQL pattern that you want to query in database, you can use {{XXX}} as dynamic field to set real value in [compare_setting.xxxxx_sql_critera]
* **add_column**: Those columns will be calucate in Pandas's dataframe after retrive data from database.
* **add_column.col_name_99**: output new columns name in Pandas's dataframe
* **add_column.col_A_99**: get the columns name from output of data columns
* **add_column.col_B_99**: get the columns name from output of data columns
* **add_column.col_oper_99**: currently, support "minus", if you need more operator, you can revise code.
* **merge_key**: Use Pandas by those key to combine every dataframe data, every dataframe have those columns.
* **cols_sort**: The finally Pandas's data sort by those key.
* **compare_setting**: 
    Support one source and multiple target query result. currently, only support source databse ia Oracle and target databse is Oracle or GCP-BigQuery.
    **- source01_platform**:"ORACLE"
    **- source01_connection**:"Data base name"
    **- source01_sql_pattern**: Which sql patten want to use.
    **- source01_df_columns**: output dataframe columns name.
    **- source01_sql_critera**: you can set multiple coulmns name which are set jinja2's template in sql pattern 
    **- target01_platform**:"ORACLE"
    **- target01_connection**:"Data base name"
    **- target01_sql_pattern**: Which sql patten want to use.
    **- target01_df_columns**: output dataframe columns name.
    **- target01_sql_critera**: you can set multiple coulmns name which are set jinja2's template in sql pattern 
    **- target02_platform**:"GCP"
    **- target02_connection**:"Data base name"
    **- target02_sql_pattern**: Which sql patten want to use.
    **- target02_df_columns**: output dataframe columns name.
    **- target02_sql_critera**: you can set multiple coulmns name which are set jinja2's template in sql pattern 	

:::	
	

###### tags: `Templates` `Meeting`

:::info
- **Location:** Room A
- **Date:** Nov 1, 2030 2:30 PM (CET)
- **Agenda**
1. Walk through signup flow `45min`
	> [name=Yukai]
2. Sprint planning `45min`
3. Revisit onboarding v1 `20min`
- **Participants:**
    - Max (MX)
    - Yukai (YK)
    - Yuhsuan (YH)
    - Arwen (YC)
- **Contact:** Max <max@example.com>
- **Host:** YK
- **Reference:** - [Last week meeting minute](/s/template-meeting-note)

:::

## Walk through signup flow 

- [Slide to explain the flow](/p/slide-example)

:dart: Sprint Goal
---
- Identify tasks that can help us raise conversion rate

:books: Sprint Backlog
---
- Email invite feature
- Interview users

:mag: Sprint Retro
---
### What we can start Doing
- New initiatives and experiments we want to start improving

:closed_book: Tasks
--
==Importance== (1 - 5) / Name / **Estimate** (1, 2, 3, 5, 8, 13)
### Development Team:
- [ ] ==5== Email invite
  - [x] ==4== Email registration page **5**
  - [ ] ==5== Email invitees **3**
- [ ] ==4== Setup e2e test in production **2**

### Design Team:
- [ ] ==4== Interview users **8**
- [ ] ==5== Build roll-up display content **5**
- [ ] ==5== Help user discover new features **5**

## Notes 
<!-- Other important details discussed during the meeting can be entered here. -->
