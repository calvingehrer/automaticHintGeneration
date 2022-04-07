# automaticHintGeneration #

This porgramm will **automatically generate hints** based on an **input question** and the **corresponding answer**. The system reads an .xlsx-file containing the **question**, **answer** and the **category**. Then it is retrieving data from Wikidata and Wikipedia. The answer of the question needs to be a Wikipedia entity and can either be a **person**, **year** or a **location**.
This code and data are based on the paper: 
*Calvin Gehrer and Adam Jatowt: Automatically Generating Hints using Wikipedia to Support Answering Factoid Questions, arxiv preprint*

## Hints for When-type Questions ##
**Wikipedia** is used to get data about the answer to generate hints using the Wikipedia-API. Every past year has an individual Wikipedia page which are all structured same: first you will see the *Events*-Section. In this section are events which occured in corresponding year listed. After that are the sections *Birth* and *Deaths* where famous people are listed which where either born or died in this year. All outlinks, which are the links of the Wikipedia page of the answer which lead to another Wikipedia page, are saved in a list and an *utility score* is calculated. The *utility score* is calculated with the **number of backlinks**, which are links which lead to targed Wikipedia pages, the **average number of pageviews** and the **similarity to the input question**. The entities with the highest scores are then searched in the Wikipedia page of the answer and the corresponding line will be outputted as hints.

## Hints for Who- and Where-type Questions ##
To generate hints if the answer is a person or a location, data will be gained from Wikidata using SPARQL. Two queries have been created with appropriate properties to get all kind of information about the answer. For some properties, if multiple results are returned, the *utility score* is calculated and the result(s) with the highest score is/are picked. The final hints will then be generated using templates for each property.


## How to use ##

An template input file is provided. Fill in the question, answer and category ("Person", "Year" or "Location") and upload it to the notebook. To be able to generate hints you need to run all cells. Then move to section *Call Functions* and exectute the corresponding cell to generate hints where the answer is a person, year or location.
