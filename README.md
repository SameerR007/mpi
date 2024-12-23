# Max Planck Institute - Patent retrieval

The project primarily involves working with patents, embeddings, databases, and tools like LogicMill and Sentence Transformers to process, analyze, and enhance patent data.

## Project Overview

This project aims to explore patents using machine learning and database queries, enabling better retrieval, embedding, and analysis of patent-related data. The repository includes scripts, and methodologies used to generate insights and analyze patent similarities.

## Contents

The work is divided into 14 modules, each focusing on a specific aspect of the project:

### 1. **sentence-transformers**
- Experimenting with sentence transformers.
- Calculating similarities between query embeddings and their corresponding positive and negative documents using a dataset with queries.

### 2. **patstat_pat_no (introduction)**
- The `2patstat_pat_no.csv` file contains family IDs of representative patents.
- A SQL query was used to fetch similar patents from the `patstat_s24.tls201_appln` database.

### 3. **keys_for_logicmill**
- For each representative patent in `2patstat_pat_no.csv`, retrieved `publn_auth`, `publn_nr`, and `publn_kind` to create keys for LogicMill.

### 4. **similar_patents_byLogicMill**
- Retrieved similar patents for the representative patents and stored the family IDs of these similar patents.

### 5. **logicmill_introduction (part 1)**
- Initial exploration and understanding of LogicMill.

### 6. **logicmill_introduction (part 2)**
- Continuation of the exploration and understanding of LogicMill.

### 7. **similar_patents_less_than_date**
- Refined the dataset from `similar_patents_byLogicMill` to include only patents with publication dates earlier than the given dates.
- patents which were not found in logic mill server were stored in three datasets - `patents_not_found.csv`, `patents_without_embeddings.csv`, `patents_without_publicationdate.csv`.

### 8. **similar_patents_with_techclasses**
- Added a technology class column to the refined dataset from `similar_patents_less_than_date`.

### 9. **similar_patents_less_than1000**
- Investigated patents to ensure that no constraints were imposed by technology classes when using Octamine. 
- Attempted to retrieve more similar patents with larger values of `k` for patents with fewer than 1,000 unique similar patents. The remaining patents (fewer than 1,000 unique matches) were flagged for manual embedding.

### 10. **merged_data**
- Modified the dataset from `similar_patents_with_techclasses` to ensure all patents have more than 1,000 unique family IDs.
- Stored patents with fewer than 1,000 unique family IDs for manual embedding.

### 11. **data_with_citations**
- Retrieved cited patents for patents in `10merged_data.csv` from the SQL database. These cited patents serve as ground truth labels for close relationships.
- Added a column containing all cited patents for each representative patent.
- Stored patents without citations in `data_no_citations.csv`.

### 12. **english_abstract_title**
- For patents that LogicMill couldn't generate embeddings (`stored in patents_not_found.csv` and `patents_without_embeddings.csv`) for, extracted their abstract and title from the SQL database for manual embedding.
- Stored patents with non-English abstracts and titles separately.

### 13. **handling_non_english**
- For patents with non-English abstracts and titles, replaced them with another patent from the same family that had English abstracts and titles.

### 14. **embedding**
- Computed manual embeddings for patents with English abstracts and titles using Sentence Transformers.
