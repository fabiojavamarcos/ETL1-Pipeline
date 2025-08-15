# ETL1-Pipeline

The ETL1 pipeline data will be used to populate the database(apriori) with information about APIs/libaries(from API_specific) from the source code updated by PRs, i.e. $${\color{orange}linking\ skills\ to\ authors\ based\ on\ the\ libaries\ used\ in\ files\ updated\ in\ PRs\ that\ they\ created.}$$

&nbsp;
## Program

ETL1 receives data, called master_all.csv, and parses it to create filesPR3BodyTitle2 which goes into [OSSPRMapper4](https://github.com/fabiojavamarcos/OSSPRMapper4). 

The output will only pass through pull requests. The output will contain: 
- issue number for the pull request
- files changed in the pull request
- title of the pull request
- body of the pull request
- author username for the author that created the pull request

&nbsp;

The dataframe is setup have a ';' in the cells between elements. Files are added in a cell together, in one string, and separated by ';'. For java, only files with extension ".java" are kept (file extension can be updated). 

The CSV separator is set to '\t' currently and the TXT(used in OSSPRMapper) is set to ' '. The separators can be confusing at first glance, but since we are using raw text, it is important to have a very unique separator. It is also important to be able to chunk all the files together and be able to split them easily too.

<details>
<summary>filesPR3BodyTitle2.csv Example:</summary>
    <img width="959" height="286" alt="CSV Example" src="https://github.com/user-attachments/assets/17599ab0-a284-471c-9686-5ed3f5d941f8" />
</details>

<details>
    <summary>filesPR3BodyTitle2.txt Example:</summary>
    <img width="943" height="419" alt="TXT Example" src="https://github.com/user-attachments/assets/6bf493f6-930f-4c4a-adce-f107571cccb7" />
</details>

As of now, the only file necesary for all projects should be updated_research2. The only thing that should be changed is column names or column setup if future input data is different.


&nbsp;
## Files Names
The file to be read whould be updated in the second cell as the example below:

    inputToRead = "./ETL1-Pipeline/data/inputs/new/master_all_projectName.csv"

The notebook writes three outputs:

    fileNameOutput = "./ETL1-Pipeline/data/outputs/new/rxjava/dataframe_file_names.csv"

    filesPR3_TXT_Output = "./ETL1-Pipeline/data/outputs/new/filesPR3BodyTitle2.txt"

    filesPR3_CSV_Output = "./ETL1-Pipeline/data/outputs/new/filesPR3BodyTitle2.csv"

The filesPR3BodyTitle2.txt is used in the next step: OSSPRMapper4.


&nbsp;
## Diagram
Below is a diagram of the entire pipeline, up to date with all the information I believe should be necesary to understand at a glance. Please look back at past data or program outputs for specific understanding of how the data is handled.

<details>
<summary> Pipeline Diagram </summary>
    <img width="3553" height="1753" alt="DataPipeline-v1 1 drawio" src="https://github.com/user-attachments/assets/638083bd-73ae-4389-905e-f62ac0efbca3" /> 
</details>
