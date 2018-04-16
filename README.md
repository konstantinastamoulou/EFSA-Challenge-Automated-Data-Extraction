# EFSA-Challenge-Automated-Data-Extraction

#Detailed Description & Requirements
##BACKGROUND

Data extraction from texts and images is a fundamental human action. Anytime we read a book or newspaper we’re extracting data whether we know it or not. This extraction may be non-targeted, such as when reading an article on a new topic and placing various key points into memory, or targeted, such as when searching for the score of a particular sporting event. Beyond everyday reading, data extraction is a key part of gathering information for almost any endeavor and spans all fields of work. Investors scan news items for companies of interest and stock prices, scientists read publications to extract data relevant to their own studies, auto mechanics look for torque specification for tightening bolts, etc.. These are targeted data extractions wherein the person is looking for and extracting specific information from the content and the data elements to be extracted can be defined beforehand. Automation of this type of targeted data extraction would save a tremendous amount of human resources for organizations that depend on extracting data from published material, particularly considering the ever-increasing mass of specialized documentation available.

Automated data extraction would be particularly useful for the Seeker in the preparation of literature reviews or systematic reviews. A systematic review is a structured process that includes the selection, appraisal and synthesis of all the relevant evidence found in relation to a specific research question. This process is increasingly used by the scientific community and considered a cornerstone of evidence-based research.  At the same time it poses challenges due to the exponential growth in evidence production and the consequent high demand in terms of time and resources. Therefore, the automation of some of the tasks to be performed in a literature review or a systematic review is highly desirable since it will assist in making these processes more feasible particularly when performed on a routine basis. The data extraction step of a systematic review aims to extract relevant information (information that is important to answer the research question/s, quantitative and/or qualitative data) to aid with the synthesis of crucial evidence gathered during the systematic review. This step in general requires human expertise and it is expensive in terms of time and resources.

At the present time some methodologies falling under the broad category of machine learning techniques, text mining and natural language processing have started to be used for the information extraction task and their performance tested, but because of the large variation of extracted data elements and the absence of a common dataset for evaluation, it is impossible to compare and assess the performance of algorithms and methods for data extraction. In addition, despite efforts, it seems that no unified framework for automatic information/data extraction has yet been developed.

 

##DATA

The data for this Challenge is found in the attachment Dataset.zip and covers four topic areas that are the subject of four literature reviews (LR) performed in EFSA. For each topic area the following files are provided:

Document with details about the LR (title, link to published version, and description of the LR), number of training and validation references, and a table of data elements to extract with description and data type. (Word format).
List of training set references with DOI links. (CSV format, UTF-8 encoded)
List of validation set references with DOI links. (CSV format, UTF-8 encoded)
Additionally, two other files with information covering all topic areas are provided. Data elements extracted from training set references by experts are in Extracted data element training set.csv  (CSV format, UTF-8 encoded) and a table of all the data elements to extract is in Table of data elements.xlsx (Excel format.)

The four topic areas for this Challenge are:

Xyllella fastidiosa (ALPHA Xylella)
Vector-borne diseases (AHAW VBD)
Amphibian  and  reptile  ecotoxicology (PRAS AmphibRept)
Toxoplasma gondii (BIOHAZ Toxoplasma)
 

##THE CHALLENGE

The Seeker desires a general algorithm for data element extraction from electronic documents including graphs and images. The proposed solution must meet the following Technical Requirements:

Able to extract data from text, graphs, and images from electronic documents in PDF format.
Generate data extraction using no human intervention other than input of a table of the data elements to be extracted, a list of bibliographic references to be used for the training dataset (called training set in this Challenge), a list of bibliographic references from which data elements need to be extracted (called validation set in this Challenge), and a training dataset of data elements extracted by experts from the papers in the training set, as illustrated in Fig 1.
Input of data elements to be extracted should be read from a user-created file that contains the identifier of the data element, a description of the data element, data type of the element, and any controlled terminology used for the data element. Submissions must include a thorough description of how to create this input file for a new topic area.
Articles for training set will be stored locally in PDF form in a directory from which the executable is run adopting the following filename convention: “topic name”+”_”+”RefID”+”.pdf” (for example ALPHA Xylella_1.pdf).
Articles for validation set will be stored locally in PDF form in a directory from which the executable is run adopting the following filename convention: “topic name”+”_”+”RefID”+”.pdf” (for example ALPHA Xylella_5.pdf).
Training dataset: input of data elements extracted by experts from training set should be read from a CSV file that contains in the first column the topic name, the second column the reference identifier (RefID), the third column the Bibliographic entry, and in the following columns the extracted data elements with data element names in the first row of the file.


Figure 1 Schema for algorithm general functioning

 

Implemented in a free license software.
Output must be in CSV format similar to the extracted data element file provided and utilize the papers in the validation set for data element extraction.
Columns should be topic name, RefID, and Bibliography entry from the list of references followed by the extracted data elements or sentence containing mentions to element to extract.
First row should contain the column heading for each column.
May utilize external information sources to improve extraction accuracy.
Able to address requests for data extraction for data elements not listed for this Challenge without alteration of the algorithm but only of the input list of data elements to be extracted, a training dataset of data elements extracted and corresponding list of bibliographic references used to extract data elements.
May be an extension of already developed algorithm or free license software/package but must provide a useful addition to the existing tool.
For data elements having controlled terminology type, the algorithm must provide either sentences containing the concept related to element to extract or exact term as in the controlled terminology (as in the training set). In case multiple studies are discussed in one article, the data elements are extracted separately, therefore a single article could be linked to more than one row in the data extraction table (as in the training set). For articles reporting more than one study, the algorithm must provide either for each element to extract the list of elements extracted from all the studies reported in the article or a table with as many rows as the number of the studies reported in the article and as many columns as the number of elements to extract, where a row contains all and only the element extracted relative to that specific study (as in the training set).

Evaluation

Evaluation of the solutions will be performed first by comparing algorithm output for the validation set with results produced by experts.
Further evaluation will be performed extracting data elements from additional topical articles and comparing algorithm output with results produced by experts.  
Final evaluation will be performed on a topic separate from topics presented for this Challenge and utilizing a new list of data elements to be extracted, a new training set of bibliographic references with the corresponding training dataset of extracted data elements and a validation set of bibliographic references to be used for data element extraction.
To be eligible for an award, algorithm performance must meet these minimum requirements at each corresponding evaluation stage listed above:

At least 3 elements extracted, with per individual element average F-score (average is calculated over the references of the validation set) greater than 50%.
At least 3 elements extracted, with per individual element average F-score (average is calculated over the references of the set of additional topical articles) greater than 50%.
None. This evaluation stage does not have a minimum requirement but will be used to differentiate submissions that have met 1 and 2 above.
F-score is defined as 2*(precision*recall)/(precision+recall) where precision and recall are based on the number of unique values for a particular data element. An explanation and example of the scoring system can be found in the file Example of Scoring System.pdf included in the Dataset.zip file attached to this Challenge.

##Project Criteria
The submitted proposal should include the following:

A detailed description of the proposed Solution addressing specific Technical Requirements presented in the Detailed Description of the Challenge. This should also include a thorough description of the algorithm used in the Solution accompanied by a well-articulated rationale for the method employed.
Input files for the four topic areas as described in (2) of the Technical Requirements.
Output from the proposed algorithm applied to the papers in the validation sets presented in the Challenge.
A free license software/algorithm/package including source code and executable with sufficient documentation to enable the Seeker to compile, execute the algorithm, and validate the method using additional test data sets.
The proposal should not include any personal identifying information (name, username, company, address, phone, email, personal website, resume, etc.) or any information the Solvers may consider as their Intellectual Property they do not want to share.

The Challenge award is contingent upon theoretical evaluation of the method/algorithm by the Seeker, and validation by the Seeker of the submitted reduction to practice Solution.  If multiple proposals meet all the Technical Requirements, the Seeker reserves the right to award only the solution which they believe the best in terms of:

Theoretical evaluation of the method/algorithm novelty of the method/algorithm.
Extraction coverage: number of data elements extracted (within each topic and overall).
Extraction performance: we evaluate F-score per individual element of extracted information against the gold extraction performed by expert, at topic level and overall.
Correct identification of studies within a reference: we evaluate F-score per study of extracted information against the gold standard extraction of study performed by expert, at topic level and overall.
The last three criteria will be evaluated and averaged over:

references of the provided validation set and
references of an external set of articles relevant for the selected topics and
references of a completely new set of articles from a topic different from the selected ones.
The higher the coverage and the F-scores, the higher score the solution gains. The more generalizable is the approach, the higher score the solution gains.

To receive an award, the Solvers will not have to transfer their exclusive IP rights to the Seeker. Instead, Solvers will grant to the Seeker a non-exclusive license to practice their solutions.  The award(s) will be paid by ADAS under the procurement contract referenced in the ABOUT THE SEEKER section.

Submissions to this Challenge must be received by 11:59 PM on 10 July 2018 US Eastern Time (05:59 AM on 11 July 2018 European Central Time.)
