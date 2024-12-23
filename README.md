# mpi

1. 1sentence-transformers : Playing around with sentence transformers. Taking a dataset with query and its corresponding positive and negative documents. Calculating 
the similarity between the embeddings of query and positive documents and query and negative documents.

2. 2patstat_pat_no(introduction) : 2patstat_pat_no.csv contains the family ids of representative patents. Fetch similar patents with the given family ids from patstat_s24.tls201_appln database using sql query.

3. 3keys_for_logicmill : for each of the representative patent in patstat_pat_no.csv fetch publn_auth, publn_nr and publn_kind to form key that can be passed into logic mill.

4. 4similar_patents_byLogicMill : Storing similar patents with respect to the representative patents and storing the family ids of these similar patents.

5. 5logicmill_introduction(part1) : Getting to know about logicmill

6. 6logicmill_introduction(part2) : extension of 5

7. 7similar_patents_less_than_date : corrected data produced in 4similar_patents_byLogicMill by taking only for dates less than publication dates.

8. 8similar_patents_with_techclasses : adding tech class column to the data produced in 7similar_patents_less_than_date.

9. 9similar_patents_less_than1000 : first checked if octamine has contrained patents wrt tech class or not. After confirming that there isnt any constrain in tech class for patents, retired to get similar patents with larger k for patents which we had unique similar patents less than 1000. At the end we have the patents for which no amount of k could get us more than 1000 unique patents.

10. 10merged_data : modifying 8similar_patents_with_techclasses dataset such that number of unique family ids is greater than 1000 for all the patents. Patents for which number of unique family ids greater than 1000 was not achieved has been stored in a separate dataset for manual embedding. 

11. 11data_with_citations - for the patents in 10merged_data.csv get the cited patents from sql database as these cited patents are the ground truth labels which should be closely related. Add one more column containg all the cited patent for a given representative patent. Also the patents for which the citations were not found are stored in data_no_citations.csv

12. 12english_abstract_title - for the patents for which logic mill was not able to generate embedding we extract their abstract and title from sql database for manual embedding. We store the patents with their abstract and title. Also we store the patents which were not found in sql database or for which either abstract or title was not in english.

13. 13handling_non_english - for the patents with non english abstracts and title we take another patent with english abstract and title from the same family.

14. 14embedding - computing manual embeddings for patents with english abstract and title using sentence transformer.