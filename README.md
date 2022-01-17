# Machine Translation Test Suite

For the longest time, the evaluation of Machine Translation (MT) has mostly concentrated on automatic metrics. However, with the rise of deep learning and Neural MT (NMT), translation outputs have become significantly better and more fluent, resulting in a need for more fine-grained evaluation techniques. Furthermore, detailed evaluation can also be used to improve MT systems by providing indications of where refinement is needed. 

One method that had already been used since the beginning of MT in the 1990's are test suites, also called challenge sets. A test suite is a hand-designed challenge set which can be used to test the performance of NLP tasks, e.g. MT outputs, with regard to specific aspects. Test suites can not only help to better understand the different kinds of errors the MT systems make, but can also provide clues for the improvement of the MT systems.

In this repository, we make public a large-scale, fine-grained test suite for German to English and English to German MT outputs, which is result of lengthy manual annotation effort over several years. We hope that  can be useful for further research by the community.


## Description of the test suite
The test suite comprises a large test set for evaluating both German to English and English to German MT outputs. It comprises around 5,000 test items per language direction. A test item always contains one sentence. The test items are categorized in 13, respectively 14 linguistic categories (depending on the language direction). The categories are in turn divided into more than 100 fine-grained phenomena. Each phenomenon is represented by at least 20 test items. For each test item, we have created a set of regular expressions to semi-automatically evaluate the correctness of MT outputs.  For the time being, we have decided to publish not the whole test set but 50\% of it (i.e., 50\% of test items of every phenomenon) in order to keep a number of test items a secret to be able to use them as a test set in case MT systems are trained on our test items. 

The classification of the test items into the categories and phenomena allows for a rather basic or more granular analysis, depending on the user's need. The classification is language-specific. For the language pair German-English, there is a large overlap in the classification between the two language directions, however, a number of categories/phenomena do only exist in either one of the language directions and few phenomena are classified in different categories. 

## Data structure
The test suite is served as one JSON file (`items.json`) per language direction, in the directory `testset`. The JSON file contains a list of test items which comprise the test suite. Every item contains the following keys:
 - `id`: unique numerical identifier of the item
 - `langpair`: the translation language direction that this item has been written for. It contains the 2-letter language codes of the source and target language concatenated without a hyphen (e.g. deen, ende)
 - `category`: the category that this item falls in
 - `phenomenon`: the phenomenon that this item falls in
 - `source_sentence`: the source (untranslated) sentece that is intended to challenge MT on one particular phenomenon 
 - `negative regex`: a regular expression intended to match wrong translations, with regards to the phenomenon being tested
 - `positive regex`: a regular expression intended to match correct translations, with regards to the phenomenon being tested
 - `negative tokens`: list of tokens (usually full sentences) that have been annotated as a wrong translation
 - `positive tokens`: list of tokens (usually full sentences) that have been annotated as a correct translation

## Related work
The directory `bibtex` contains a list of bibtex (`.bib`) files of prior work that has resulted in the creation of the test suite or applications of it. 

