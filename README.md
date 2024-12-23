# mpi

1. 1sentence-transformers : Playing around with sentence transformers. Taking a dataset with query and its corresponding positive and negative documents. Calculating 
the similarity between the embeddings of query and positive documents and query and negative documents.

2. 2patstat_pat_no(introduction) : 2patstat_pat_no.csv contains the family ids of representative patents. Fetch similar patents with the given family ids from patstat_s24.tls201_appln database using sql query.

3. 3keys_for_logicmill : for each of the representative patent in patstat_pat_no.csv fetch publn_auth, publn_nr and publn_kind to form key that can be passed into logic mill.

4. 4similar_patents_byLogicMill : Storing similar patents with respect to the representative patents and storing the family ids of these similar patents.

5. 7similar_patents_less_than_date : corrected data produced in 4similar_patents_byLogicMill by taking only for dates less than publication dates.

6. 8similar_patents_with_techclasses : adding tech class column to the data produced in 7similar_patents_less_than_date.

7. 9similar_patents_less_than1000 : first checked if octamine has contrained patents wrt tech class or not. After confirming that there isnt any constrain in tech class for patents, retired to get similar patents with larger k for patents which we had unique similar patents less than 1000. At the end we have the patents for which no amount of k could get us more than 1000 unique patents.

