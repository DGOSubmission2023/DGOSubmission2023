### DGO Submission 2023 for Track 1: Data-driven Governance through Information Retrieval and Decision Support Systems

The application R2D was mainly created through the four python scripts: `scrapeTelegramChannelMessages.py`, `runBERTopic.py`, `transformResults.py`, `appSwitzerland.py`

Below each of the four files is explained briefly and sample usage is shown. More information can be gathered from the comments within the code.


`transformResults.py` takes the results of the BERTopic model and gives each cluster a name. This is done via qualitativ analysis of each cluster. Thus if the code is rerun, this qualitativ analysis has to be done by the user. Within the python script one can then modify the dictionary `class_name_dict` to give each cluster a distinctive name. The file takes as input the results of the BERTopic model and outputs the modified dataframe used within the Streamlit app

`python transformResults.py -i df.csv -o data/df_prep.csv `
