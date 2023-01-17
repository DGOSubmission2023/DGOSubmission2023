### DGO Submission 2023 for Track 1: Data-driven Governance through Information Retrieval and Decision Support Systems

The application R2D was mainly created through the four python scripts: `scrapeTelegramChannelMessages.py`, `runBERTopic.py`, `transformResults.py`, `appSwitzerland.py`

Below each of the four files is explained briefly and sample usage is shown. More information can be gathered from the comments within the code.

1. `scrapeTelegramChannelMessages.py` takes the a list of open telegram channels as input, compare `data/switzerland_groups.txt` and scrapes the message text and the date the message was written on. It then save the results as a `.csv` file, the sample use is shown below:

`python scrapeTelegramChannelMessages.py -i data/switzerland_groups.txt -o data/df_telegram.csv`

2. `runBERTopic.py` runs the BERTopic algorithm on a given dataset e.g. `data/telegram_df.csv` obtained from the prior step. Further, we can specify where the outputs, meaning the model and some visualisation for analysis can be saved. Moreover, we can specify the number of clusters the algorithm should create. Last, we can specify if the trained model should do inference as well, meaning if it should predict the which topic a message belongs to for the input dataset. The results of the model are saved under `myBERTopicModel/df_model.csv` Below the example usage is show for the dataset `data/df_telegram.csv` we save our output to a folder, which the script creates named `myBERTopicModel`, we define the algorithm should create `25` cluster and also do infernece `--di`.

`python runBERTopic.py -i data/df_telegram.csv -o myBERTopicModel -k 25 --di`

3. `transformResults.py` takes the results of the BERTopic model and gives each cluster a name. This is done via qualitativ analysis of each cluster. Thus if the code is rerun, this qualitativ analysis has to be done by the user. Within the python script one can then modify the dictionary `class_name_dict` to give each cluster a distinctive name. The file takes as input the results of the BERTopic model and outputs the modified dataframe used within the Streamlit app. Example usage is shown below:

`python transformResults.py -i myBERTopicModel/df_model.csv -o data/df_prep.csv`

4. `appSwitzerland.py` contains the Streamlit application for displays the results of the BERTopic analysis. The app can be locally hosted using the command below. For the hosting we provided on the Streamlit Cloud we utilized another private Github repo.

`streamlit run appSwitzerland.py`
