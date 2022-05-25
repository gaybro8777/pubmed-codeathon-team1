# JUST RETRIEVAL
## pubmed-codeathon-team1

## DATA INFO

### [data/out/pmids.csv](data/out/pmids.csv)

This is a list of all the pmids for the terms we're interested in. Here's what the fields mean:

+ `pmid`
+ `query` - query string, read in from [./data/in/team1_search_strats_search_term+.csv](data/in/team1_search_strats_search_terms.csv) (from Travis' google doc)
+ `search_type` - relevant | pubdate_desc
+ `page` - 1 | 2

### [data/out/pmid_data.csv](data/out/pmid_data.csv)

Columns of data pulled directly from the PubMed API or [iCite](https://icite.od.nih.gov/):

**iCite columns**
+ `relative_citation_ratio`,   [RCR](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1002541) measure of influence
+ `human`,   Prediction from MeSH on human subject
+ `animal`,   Prediction from MeSH on animal subjects
+ `molecular_cellular`,   Prediction from MeSH on cellular subjects
+ `apt`,   Approx. potential to clinically translate
+ `is_clinical`,   Bool, clinical or guideline
+ `citation_count`,   Raw  of citations
+ `cited_by`,   PMIDs of citations
+ `references`,   PMIDs of references

**PubMed columns**
+    `title`
+    `abstract`
+    `journal`
+    `authors`
+    `affiliations`
+    `pubdate`
+    `mesh_terms`
+    `publication_types`
+    `chemical_list`
+    `keywords`
+    `languages`
+    `country`

### data/out/pmid_xmls

A set of raw xml files retrieved for each pmid in the pmids.csv file.

### data/out/pubs.json (coming soon!)

### Wiki link
<https://github.com/NCBI-Codeathons/pubmed-codeathon-team1/wiki/Data-Management-Team---Scratch>

## ABSTRACT
The goal of JUST RETRIEVAL is to describe any potential biases that exist in search results based on PubMed Best Search Algorithm in comparing the retrieved results between different pages as well as to search results from a different search algorithm (date sort algorithm) . The focus for this project is to answer the following research questions:

* RQ1: Is there a correlation between various author attributes and retrieved best match search results?
* RQ2: Is there a difference between search results between best search and date order search by author attributes?
* RQ3: Is there a correlation between various publication attributes and retrieved best match search results?
* RQ4: Is there a difference between search results between best search vs. date order search by Publication Attributes?

The author attributes that were considered are: gender, race, institutional affiliation, country of origin, and author authority (e.g., research impact based on number of hits). The publication attributes that were considered are: NIH funding, language of publication, reading level, diversity of references, associated data, and number of authors and affiliations.

We filtered out certain publication types such as books, errata, and commentary and have relied on both past user search behaviors as well as custome search keywords across these categories: Rare diseases, signaling pathways, social determinants of health and health equities, list of autoimmune diseases, list of cells, infectious bacteria, list of medical devices, and list of drugs.

## BASIC WORKFLOW

1. Connect to the PubMed API. 
2. Read the CSV files of search terms to use as search parameters for PubMed API.
3. Query and retrieve (both Best Match and Date Sort implementations) author and publication attributes for 1st 2 pages (1st 20 results).
4. Compare the author and publication attributes in retrieved results for the first page (1st 10 results) with second page (2nd 10 results) of PubMed Best Match algorithm results.
5. Compare the author and publication attributes in retrieved results (just 1st page) between the PubMed Best Search and PubMed Date Sort algorithms.
6. Display the results and write observations.

## TEAM MEMBERS

* Sruthi Chari (data lead)
* Travis Hoppe (project lead)
* Alex Sticco
* Alexa M. Salsbury
* Ben Rogers
* Brian Lee
* Brooks Leitner
* Caroline Trier
* Linda M. Hartman
* Preeti G. Kochar
* Sridhar Papagari Sangareddy