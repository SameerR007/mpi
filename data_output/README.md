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
