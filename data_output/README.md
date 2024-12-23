1sentence_transformers.csv
Columns: 
Query - focal datapoint
Pos - set of positive datapoints
neg - set of negative datapoints
avg_sim_pos - average of similarities between query and its all positive documents
avg_sim_neg - average of similarities between query and its all negative documents
Result - True if for a query avg_sim_pos > avg_sim_neg

3keys_for_logicmill.csv
Columns : docdb_family_id, pat_publn_id, earliest_filing_date, appln_auth, granted, publn_auth, publn_nr, publn_kind, key
Major column - key (that need to passed into logic mill)

4similar_patents_byLogicMill.csv
Columns : docdb_family_id, key, similar_patents, similar_patents_family, num_unique_elements
similar_patents_family - family ids of similar patents
num_unique_elements - represent how many unique family ids are there. If this is less than 1000 for any representative patent we need to rety with more similar patents

7similar_patents_less_than_date.csv
columns : same as 4similar_patents_byLogicMill.csv but with patents with less than publication dates

patents_ not_found.csv - keys of patents which were not found by logic mill server
patents_without_embeddings.csv - keys of patents for which embeddings were not found
patents_without_publicationdate.csv - keys of patents for which publication dates were not found

8similar_patents_with_techclasses.csv
columns : same as 7similar_patents_less_than_date.csv with an added column mainarea34 denoting the tech class

9similar_patents_less_than1000.csv
subset of 8similar_patents_with_techclasses.csv with all patents for which number of unique family ids is less than 1000

dataconcat1.csv and dataconcat2.csv - data for which trying with a larger k to get more than 1000 similar unique family ids patents was successful. And these have to be merged with 8similar_patents_with_techclasses.csv

10merged_data.csv - merged data 8similar_patents_with_techclasses.csv with dataconcat1.csv and dataconcat2.csv
data204.csv - same as 9similar_patents_less_than1000.csv (corrected by reset index)

11
data_with_citations.csv - 10merged_data.csv with an additional column with cited patents
data_no_citations.csv - patents in 10merged_data.csv for which citations were not found in sql database

12english_abstract_title.csv - columns : key, appln_id, appln_title, appln_abstract
applnids_notin_tls203_appln_abstr.csv - columns : key, appln_id
patents_not_en_abstract.csv - columns : key, appln_id

13handling_non_english.csv - subset of applnids_notin_tls203_appln_abstr.csv and patents_not_en_abstract.csv for which another patent of same family with english abstract and title was found.
patents_not_en.csv - subset of applnids_notin_tls203_appln_abstr.csv and patents_not_en_abstract.csv for which no patent of same family with english abstract and title was found.