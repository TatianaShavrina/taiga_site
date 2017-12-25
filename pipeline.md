# Corpus construction pipeline

## Data crawling
 - For [each](https://github.com/TatianaShavrina/crawlers) segment we crawl metainformation and texts parsed with Beautifulsoup

## Deduplication and boilerplate removal
 - by URL and full duplicates are removed

## Tokenization
 - we use [nltk.word_tokenize](http://www.nltk.org/api/nltk.tokenize.html)
 - symbol [unification](https://github.com/TatianaShavrina/taiga/blob/master/tagging_pipeline/unify.py)

## Morphology and syntax
 - [UDpipe parser](http://ufal.mff.cuni.cz/udpipe) 
 The pipeline is documented [here](https://github.com/TatianaShavrina/taiga/tree/master/tagging_pipeline)
 
 On our github repository for pipeline and database construction you can find more detailed information
 https://github.com/TatianaShavrina/taiga/
