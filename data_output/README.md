# Data Folder

This folder contains various datasets generated and used throughout the project. Below is an overview of each file and its structure:

---

### **1sentence_transformers.csv**
**Columns:**
- **Query**: Focal datapoint.
- **Pos**: Set of positive datapoints.
- **Neg**: Set of negative datapoints.
- **Avg_sim_pos**: Average of similarities between the query and all its positive documents.
- **Avg_sim_neg**: Average of similarities between the query and all its negative documents.
- **Result**: True if for a query `Avg_sim_pos > Avg_sim_neg`.

---

### **3keys_for_logicmill.csv**
**Columns:**
- **docdb_family_id**
- **pat_publn_id**
- **earliest_filing_date**
- **appln_auth**
- **granted**
- **publn_auth**
- **publn_nr**
- **publn_kind**
- **key**: The key to be passed into LogicMill.

---

### **4similar_patents_byLogicMill.csv**
**Columns:**
- **docdb_family_id**
- **key**
- **similar_patents**
- **similar_patents_family**: Family IDs of similar patents.
- **num_unique_elements**: Number of unique family IDs. If this is less than 1,000 for any representative patent, we need to retry with more similar patents.

---

### **7similar_patents_less_than_date.csv**
**Columns:**
- Same as `4similar_patents_byLogicMill.csv` but includes only patents with publication dates earlier than the given dates.

### **patents_not_found.csv**
**Description**: Contains keys of patents not found by the LogicMill server.

### **patents_without_embeddings.csv**
**Description**: Contains keys of patents for which embeddings were not found.

### **patents_without_publicationdate.csv**
**Description**: Contains keys of patents for which publication dates were not found.

---

### **8similar_patents_with_techclasses.csv**
**Columns:**
- Same as `7similar_patents_less_than_date.csv`, with an added column:
  - **mainarea34**: Denotes the technology class.

---

### **9similar_patents_less_than1000.csv**
**Description**: A subset of `8similar_patents_with_techclasses.csv` with all patents for which the number of unique family IDs is less than 1,000.

### **dataconcat1.csv** and **dataconcat2.csv**
**Description**: Contain data for patents for which attempts with a larger `k` successfully retrieved more than 1,000 unique similar family IDs. These need to be merged with `8similar_patents_with_techclasses.csv`.

---

### **10merged_data.csv**
**Description**: Merged data from `8similar_patents_with_techclasses.csv`, `dataconcat1.csv`, and `dataconcat2.csv`.

---

### **data204.csv**
**Description**: Same as `9similar_patents_less_than1000.csv` but corrected with a reset index.

---

### **11data_with_citations.csv**
**Description**: Contains data from `10merged_data.csv` with an additional column for cited patents.

### **data_no_citations.csv**
**Description**: subset of `10merged_data.csv` for which citations were not found in the SQL database.

---

### **12english_abstract_title.csv**
**Columns:**
- **key**
- **appln_id**
- **appln_title**
- **appln_abstract**

### **applnids_notin_tls203_appln_abstr.csv**
**Columns:**
- **key**
- **appln_id**

### **patents_not_en_abstract.csv**
**Columns:**
- **key**
- **appln_id**

---

### **13handling_non_english.csv**
**Description**: A subset of `applnids_notin_tls203_appln_abstr.csv` and `patents_not_en_abstract.csv` for which another patent from the same family with an English abstract and title was found.

### **patents_not_en.csv**
**Description**: A subset of `applnids_notin_tls203_appln_abstr.csv` and `patents_not_en_abstract.csv` for which no patent from the same family with an English abstract and title was found.

---

### **14embeddings.pkl** and **14embeddings.csv**
**Description**: Contain embeddings of patents with English abstracts and titles.

---

### **21similar_patents_updated.pkl**

**Columns:**
- **docdb_family_id**
- **similar_patents**: Family IDs of similar patents.

### **21error_ids.pkl**
**Description**: List of family ids of representative patents for which logic mill gave error when fetching.

---

### **22patents_atleast1000.pkl**
**Description**: Subset of `21similar_patents_updated.pkl` with only the patents for which unique similar patents were atleast 1000.

### **22patents_NotFound.pkl**
**Description**: `21error_ids.pkl` in dataframe format

### **22patents_lessthan1000.pkl**
**Description**: Subset of `21similar_patents_updated.pkl` with only the patents for which unique similar patents were less than 1000.

---

### **23patents_lessthan1000.pkl**
**Description**: Subset of `22patents_lessthan1000.pkl` for which unique similar patents were less than 1000 irrespective of how high the k was.

---

### **24all_patents_atleat1000.pkl**
**Description**: All the patents combined for which unique similar patents are atleast 1000

**Columns:**
- **docdb_family_id**
- **similar_patents**: Family IDs of similar patents.

---

### **25patents_with_citations.pkl**
**Description**: Contains data from `24all_patents_atleat1000.pkl` with an additional column for cited patents.

### **25patents_no_citations.pkl**
**Description**: Subest of `24all_patents_atleat1000.pkl` for which no citations were found in sql datadase.

---

### 26. **26noisy_patents.pkl**
**Description**: ids for which there were noisy (random strings) in similar patents. 

### 26. **26evaluated_data_logicmill.pkl**
**Description**: Evaluation on `25patents_with_citations.pkl`

**Columns:**
- **docdb_family_id**
- **similar_patents**: Family IDs of similar patents.
- **cited_docdb_family_id**: list of citations
- **MRR@10**: Mean reciprocal rank value
- **MAP@1000**: Mean Absolute precision value
- **RFR@1000**: Rank first relavent value