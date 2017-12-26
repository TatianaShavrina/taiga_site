
# Data format

We are providing tagged texts in conllu format:

```
# newdoc
# newpar
# sent_id = 1
# 2003Armeniya.xml 1
# text = В советский период времени число ИТ- специалистов в Армении составляло около десяти тысяч.
# sent_id = 1
1	В	в	ADP	_	_	3	case	3:case	_
2	советский	советский	ADJ	_	Animacy=Inan|Case=Acc|Degree=Pos|Gender=Masc|Number=Sing	3	amod	3:amod	_
3	период	период	NOUN	_	Animacy=Inan|Case=Acc|Gender=Masc|Number=Sing	11	obl	11:obl	_
4	времени	время	NOUN	_	Animacy=Inan|Case=Gen|Gender=Neut|Number=Sing	3	nmod	3:nmod	_
5	число	число	NOUN	_	Animacy=Inan|Case=Acc|Gender=Neut|Number=Sing	11	obj	11:obj	_
6	ИТ	ит	PROPN	_	Animacy=Inan|Case=Nom|Gender=Neut|Number=Sing	8	compound	8:compound	SpaceAfter=No
7	-	-	PUNCT	_	_	6	punct	6:punct	_
8	специалистов	специалист	NOUN	_	Animacy=Anim|Case=Gen|Gender=Masc|Number=Plur	5	nmod	5:nmod	_
9	в	в	ADP	_	_	10	case	10:case	_
10	Армении	армения	PROPN	_	Animacy=Inan|Case=Loc|Gender=Fem|Number=Sing	5	nmod	5:nmod	_
11	составляло	составлять	VERB	_	Aspect=Imp|Gender=Neut|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act	0	root	0:root	_
12	около	около	ADP	_	_	14	case	14:case	_
13	десяти	десять	NUM	_	Case=Gen	14	nummod	14:nummod	_
14	тысяч	тысяча	NOUN	_	Animacy=Inan|Case=Gen|Gender=Fem|Number=Plur	11	nsubj	11:nsubj	SpaceAfter=No
15	.	.	PUNCT	_	_	14	punct	14:punct	_

```

## Text storage
Each of the segments you can download in 2 formats:
1. As an archive with plain texts, tagged texts and tables with metadata 
2. As a sqlite3 database with tables for metadata, tagged texts and plain texts

 On our github repository for pipeline and database construction you can find more detailed information
 https://github.com/TatianaShavrina/taiga/
 
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
