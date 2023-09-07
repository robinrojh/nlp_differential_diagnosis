# NLP Differential Diagnosis

The aim of this personal project is to create an AI program to assist in the disease diagnosis process. 
Mainly, it aims to help with finding a differential diagnosis for an input diagnosis.

### Data Source
* Unified Medical Language System® (UMLS®) Metathesaurus

Input: Suspected disease name or CUI from UMLS (Diagnosis)

Output: Top-k diseases that are relevant to the input

### Process
1. Extract data from UMLS Metathesaurus (not included in this repository)
2. Process the data from 1 to obtain only the diseases and their definitions
3. Using the paraphrase mining technique from [Sentence-Transformers]([url](https://www.sbert.net/examples/applications/paraphrase-mining/README.html)https://www.sbert.net/examples/applications/paraphrase-mining/README.html) package, compute the cosine similarity of all pairs of disease definitions
4. Save the output in output/similarity.csv, and finally call ```get_similar_diseases``` or ```get_similar_diseases_by_cui``` function to retrieve the differential diagnosis to the given disease.

### Example

| CUI_1 |	STR_1	| CUI_2 |	STR_2 |	SCORE |
| ----- | ----- | ----- | ----- | ----- | 
|	C0000744 |	ABETALIPOPROTEINEMIA	| C0020479	| HYPERLIPOPROTEINEMIA TYPE III |	0.734213 |
| C0000744 |	ABETALIPOPROTEINEMIA	| C0023817	| HYPERLIPOPROTEINEMIA TYPE I |	0.732668 |
| C0000744 |	ABETALIPOPROTEINEMIA	| C0020480	| HYPERLIPOPROTEINEMIA TYPE IV |	0.729844 |
|	C0000744 |	ABETALIPOPROTEINEMIA	| C0028064	| NIEMANN-PICK DISEASE |	0.670821 |
|	C0000744 |	ABETALIPOPROTEINEMIA	| C0020445	| HYPERLIPOPROTEINEMIA TYPE II |	0.650171 |
|	C0000744 |	ABETALIPOPROTEINEMIA	| C0034960	| REFSUM DISEASE |	0.640331 |
|	C0000744 |	ABETALIPOPROTEINEMIA	| C0023195	| LECITHIN CHOLESTEROL ACYLTRANSFERASE DEFICIENCY |	0.638767 |
