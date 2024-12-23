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
