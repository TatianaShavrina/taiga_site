
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
---

## Text storage
Each of the segments you can download in 2 formats:
1. As an archive with plain texts, tagged texts and tables with metadata 
2. As a sqlite3 database with tables for metadata, tagged texts and plain texts

 On our github repository for pipeline and database construction you can find more detailed information
 https://github.com/TatianaShavrina/taiga/
 
 ---
 
# Corpus construction pipeline

## Data crawling
 - For [each](https://github.com/TatianaShavrina/crawlers) segment we crawl metainformation and texts parsed with Beautifulsoup
 ---

## Deduplication and boilerplate removal
 - by URL and full duplicates are removed
 ---

## Tokenization
 - we use [nltk.word_tokenize](http://www.nltk.org/api/nltk.tokenize.html)
 - symbol [unification](https://github.com/TatianaShavrina/taiga/blob/master/tagging_pipeline/unify.py)
 ---

## Morphology and syntax
 - [UDpipe parser](http://ufal.mff.cuni.cz/udpipe) 
 The pipeline is documented [here](https://github.com/TatianaShavrina/taiga/tree/master/tagging_pipeline)
 
 ---
# Morphology
Tagset is rather typical, notwithstanding that proper nouns are different part of speech, 'быть' is considered an auxiliary verb and X stands for trash and forign words.
Here are the tags with typical examples: 

    ADJ – другой, новый, самый, первый, сам, должен, российский, нужный, последний

    ADP – в, на, с, по, к, из, о, для, от, за

    ADV – так, уже, еще, можно, более, как, очень, однако, где, сейчас

    AUX – быть

    CCONJ – и, а, но, или, ни, да, а_также, либо, причем, так_и

    DET – этот, свой, весь, тот, такой, наш, какой, некоторый, мой, никакой

    INTJ – ах, о, ох, а, эх, та-да-дам, ой, ай, алло, ба

    NOUN – год, человек, время, страна, работа, система, жизнь, власть, раз

    NUM – один, два, несколько, три, 1, 10, 20, 2, много, пять

    PART – не, и, же, только, бы, даже, вот, ли, лишь, именно

    PRON – он, это, они, который, то, я, она, мы, что, все

    PROPN – россия, москва, ссср, владимир, европа, сергей, земля, александр

    PUNCT – ,, ., ", -, :, ), (, ?, !, …

    SCONJ – что, как, если, чтобы, когда, то, чем, хотя, поскольку, пока

    SYM – %, $, №, °, €, =, плюс, №№, C, +

    VERB – мочь, быть, становиться, говорить, получать, иметь, считать, давать

    X – of, and, the, in, for, de, mignews.com, capture, di, money
    
---
    
### Every POS-tag has its own features (see below):

#### Animacy, value="Anim"\"Inan"

What POS: ADJ,NOUN,NUM,PRON,PROPN,VERB

Examples: человек, люди, людей, человека, все, ученые, президента, В. Путин, президент


#### Aspect, value="Imp"\"Perf"

What POS: AUX,VERB

Examples Imp: было, был, есть, может, будет, были, быть, была, нет, могут

Examples Perf: стал, сказал, стало, стали, сделать, сказать, заявил, получить


#### Case, value="Nom" \"Acc" \"Dat"\"Gen" \"Ins" \"Loc"\"Par"\"Voc"

What POS: ADJ,DET,NOUN,NUM,PRON,PROPN,VERB

Examples "Par": разу, виду, народу, толку, чаю, ходу, голоду, сахару, дому, глазу


#### Degree, value="Pos" "Cmp"\

What POS: "Cmp" – ADJ,ADV, "Pos" – ADJ,ADV,DET,NOUN,PROPN, "Sup" – ADJ

Examples: более, больше, менее, лучше, раньше, выше, дальше, чаще, позже, хуже


#### Foreign, value="Yes"

What POS: ADJ,NOUN,PROPN,X

Examples: MBA, FIA, the, of, ButtKicker, and, PM, RoboCup, FOXP2, Weta


#### Gender, value="Fem"\"Masc"\"Neut"

What POS: ADJ,AUX,DET,NOUN,NUM,PRON,PROPN,VERB

Examples: ее, России, она, была, этой, жизни, власти, страны, своей, эта


#### Mood, value="Imp"\"Cnd"\"Ind"

What POS: PART,SCONJ

Examples: бы, чтобы, чтоб, б, см., давайте, будь


#### Number, value="Sing"\"Plur"

What POS: ADJ,AUX,DET,NOUN,PRON,PROPN,VERB

Examples: их, мы, они, все, были, лет, них, нас, эти, всех


#### Person, value="1"\"2" \"3"

What POS: AUX,PRON,VERB

Examples: я, мы, нас, мне, меня, нам, скажем, думаю, знаю, будем


#### Рolarity, value="Neg"

What POS: ADV,PART

Examples: несмотря, не, ни, невзирая, нет, нет-нет


#### Tense, value="Fut"\"Past"\"Pres"

What POS: VERB

Examples: скажем, станет, придется, сможет, смогут, удастся, окажется, пойдет


#### Variant, value="Short"

What POS: ADJ,PROPN,VERB

Examples: нужно, должны, должен, должна, известно, необходимо, невозможно, должно, важно, трудно


#### VerbForm, value="Conv"\"Fin" \"Inf"\"Part"

What POS: AUX,VERB

Examples: говоря, начиная, учитывая, будучи, судя, исходя, имея, используя, глядя, выступая, была, нет, могут, будут, сделать, сказать, делать, получить, говорить, работать, стать, иметь, понять, связано, связаны, сделано, окружающей, принято, связанных, связана, связан, сказано, называемые


#### Voice, value="Act"\"Mid" \"Pass"

What POS: AUX,VERB

Examples: было, был, есть, может, будет, были, быть, была, нет, могут

---

# Syntax

acl: clausal modifier of noun (adjectival clause)
```
1    Доставшийся    доставаться    VERB    _    Aspect=Perf|Case=Nom|Gender=Masc|Number=Sing|Tense=Past|VerbForm=Part|Voice=Mid    11    acl    11:acl    _
2    в    в    ADP    _    _    3    case    3:case    _
3    наследство    наследство    NOUN    _    Animacy=Inan|Case=Acc|Gender=Neut|Number=Sing    1    obl    1:obl    _
...
11   потенциал    потенциал    NOUN    _    Animacy=Inan|Case=Nom|Gender=Masc|Number=Sing    12    nsubj    12:nsubj    _
```
advcl: adverbial clause modifier
```
26    ударил    ударять    VERB    _    Aspect=Perf|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act    5    conj    5:conj    _
...
30    ,    ,    PUNCT    _    _    29    punct    29:punct    _
31    как    как    SCONJ    _    _    33    mark    33:mark    _
32    чугунная    чугунный    ADJ    _    Case=Nom|Degree=Pos|Gender=Fem|Number=Sing    33    amod    33:amod    _
33    пушка    пушка    NOUN    _    Animacy=Inan|Case=Nom|Gender=Fem|Number=Sing    26    advcl    26:advcl    SpaceAfter=No

6    вырос    вырастать    VERB    _    Aspect=Perf|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act    0    root    0:root    _
7    на    на    ADP    _    _    9    case    9:case    _
8    9,6    9,6    NUM    _    _    9    nummod    9:nummod    SpaceAfter=No
9    %    %    SYM    _    _    6    obl    6:obl    SpaceAfter=No
10    ,    ,    PUNCT    _    _    9    punct    9:punct    _
11   составив    составлять    VERB    _    Aspect=Perf|Tense=Past|VerbForm=Conv|Voice=Act    6    advcl    6:advcl    _
```
advmod: adverbial modifier

```20    так    так    ADV    _    Degree=Pos    21    advmod    21:advmod    _
21    смертельно    смертельно    ADV    _    Degree=Pos    22    advmod    22:advmod    _
22    устал    уставать    VERB    _    Aspect=Perf|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act    11    conj    11:conj    SpaceAfter=No

10    вежливо    вежливо    ADV    _    Degree=Pos    11    advmod    11:advmod    _
11    сказал    сказать    VERB    _    Aspect=Perf|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act    7    parataxis    7:parataxis    _
12    Илья    илья    PROPN    _    Animacy=Anim|Case=Nom|Gender=Masc|Number=Sing    11    nsubj    11:nsubj    _
13    Ильич    ильич    PROPN    _    Animacy=Anim|Case=Nom|Gender=Masc|Number=Sing    12    flat:name    12:flat    SpaceAfter=No
```
amod: adjectival modifier

```19    на    на    ADP    _    _    21    case    21:case    _
20    постсоветском    постсоветский    ADJ    _    Case=Loc|Degree=Pos|Gender=Neut|Number=Sing    21    amod    21:amod    _
21    пространстве    пространство    NOUN    _    Animacy=Inan|Case=Loc|Gender=Neut|Number=Sing    17    nmod    17:nmod    SpaceAfter=No
```
appos: appositional modifier
```
the noun following immediately after the noun, specifying or modifying its meaning:
```
aux: auxiliary (+ aux:pass)

```25    не    не    PART    _    _    26    advmod    26:advmod    _
26    стал    стать    VERB    _    Aspect=Perf|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act    5    conj    5:conj    _
27    бы    бы    PART    _    Mood=Cnd    26    aux    26:aux    SpaceAfter=No

1    Стены    стена    NOUN    _    Animacy=Inan|Case=Nom|Gender=Fem|Number=Plur    3    nsubj    3:nsubj    _
2    были    быть    AUX    _    Aspect=Imp|Mood=Ind|Number=Plur|Tense=Past|VerbForm=Fin|Voice=Act    3    aux:pass    3:aux:pass    _
3    увешаны    увешивать    VERB    _    Aspect=Perf|Number=Plur|Tense=Past|Variant=Short|VerbForm=Part|Voice=Pass    0    root    0:root    _
```

case: case marking

```
1    В    в    ADP    _    _    3    case    3:case    _
2    советский    советский    ADJ    _    Animacy=Inan|Case=Acc|Degree=Pos|Gender=Masc|Number=Sing    3    amod    3:amod    _
3    период    период    NOUN    _    Animacy=Inan|Case=Acc|Gender=Masc|Number=Sing    11    obl    11:obl    _
```

cc: coordinating conjunction
```
3    вазы    ваза    NOUN    _    Animacy=Inan|Case=Nom|Gender=Fem|Number=Plur    2    nsubj    2:nsubj    _
4    под    под    ADP    _    _    5    case    5:case    _
5    цветы    цветы    NOUN    _    Animacy=Inan|Case=Acc|Gender=Masc|Number=Plur    3    nmod    3:nmod    _
6    и    и    CCONJ    _    _    7    cc    7:cc    _
7    сифоны    сифон    NOUN    _    Animacy=Inan|Case=Nom|Gender=Masc|Number=Plur    3    conj    3:conj    _
```
ccomp: clausal complement
```
2    скажи    сказать    VERB    _    Aspect=Perf|Mood=Imp|Number=Sing|Person=2|VerbForm=Fin|Voice=Act    0    root    0:root    _
3    на    на    ADP    _    _    4    case    4:case    _
4    милость    милость    NOUN    _    Animacy=Inan|Case=Acc|Gender=Fem|Number=Sing    2    obl    2:obl    SpaceAfter=No
5    ,    ,    PUNCT    _    _    4    punct    4:punct    _
6    сколько    сколько    ADV    _    Degree=Pos    8    advmod    8:advmod    _
7    ты    ты    PRON    _    Case=Nom|Number=Sing|Person=2    8    nsubj    8:nsubj    _
8    получаешь    получать    VERB    _    Aspect=Imp|Mood=Ind|Number=Sing|Person=2|Tense=Pres|VerbForm=Fin|Voice=Act    2    ccomp    2:ccomp    _
```
compound: compound

```
25    российско    российский    ADJ    _    Degree=Pos    27    compound    27:compound    SpaceAfter=No
26    -    -    PUNCT    _    _    25    punct    25:punct    SpaceAfter=No
27    американской    американский    ADJ    _    Case=Gen|Degree=Pos|Gender=Fem|Number=Sing    28    amod    28:amod    _
28    программы    программа    NOUN    _    Animacy=Inan|Case=Gen|Gender=Fem|Number=Sing    24    nmod    24:nmod    _
```
conj: conjunct

```
19    первый    первый    ADJ    _    Animacy=Inan|Case=Acc|Degree=Pos|Gender=Masc|Number=Sing    24    amod    24:amod    SpaceAfter=No
20    ,    ,    PUNCT    _    _    19    punct    19:punct    _
21    второй    второй    ADJ    _    Animacy=Inan|Case=Acc|Degree=Pos|Gender=Masc|Number=Sing    19    conj    19:conj    _
22    и    и    CCONJ    _    _    23    cc    23:cc    _
23    третий    третий    ADJ    _    Animacy=Inan|Case=Acc|Degree=Pos|Gender=Masc|Number=Sing    19    conj    19:conj    _
```
cop: copula
```
13    будет    быть    AUX    _    Aspect=Imp|Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act    17    cop    17:cop    _
14    для    для    ADP    _    _    15    case    15:case    _
15    него    он    PRON    _    Case=Gen|Gender=Masc|Number=Sing|Person=3    17    nmod    17:nmod    _
16    наилучшим    наилучший    ADJ    _    Case=Ins|Degree=Pos|Gender=Neut|Number=Sing    17    amod    17:amod    _
17    решением    решение    NOUN    _    Animacy=Inan|Case=Ins|Gender=Neut|Number=Sing    1    obl    1:obl    SpaceAfter=No
```
csubj: clausal subject
```
4    приобрести    приобретать    VERB    _    Aspect=Perf|VerbForm=Inf|Voice=Act    7    csubj    7:csubj    _
5    однокомнатную    однокомнатный    ADJ    _    Case=Acc|Degree=Pos|Gender=Fem|Number=Sing    6    amod    6:amod    _
6    квартиру    квартира    NOUN    _    Animacy=Inan|Case=Acc|Gender=Fem|Number=Sing    4    obj    4:obj    _
7    можно    можно    ADV    _    Degree=Pos    2    parataxis    2:parataxis    _
```
dep: unspecified dependency
```
если по каким-то причинам система не смогла определить тип отношения, ему присваивается метка dep:
```
det: determiner
```
отношение между именной вершиной и её детерминативом:

2    по    по    ADP    _    _    4    case    4:case    _
3    ту    тот    DET    _    Case=Acc|Gender=Fem|Number=Sing    4    det    4:det    _
4    сторону    сторона    NOUN    _    Animacy=Inan|Case=Acc|Gender=Fem|Number=Sing    6    obl    6:obl    _
```
discourse: discourse element
```
7    предстоял    предстоять    VERB    _    Aspect=Imp|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act    5    parataxis
8    ведь    ведь    PART    _    _    7    discourse    7:discourse    _
9    его    он    PRON    _    Case=Gen|Gender=Masc|Number=Sing|Person=3    10    nmod    10:nmod    _
10   выход    выход    NOUN    _    Animacy=Inan|Case=Nom|Gender=Masc|Number=Sing    7    nsubj    7:nsubj    SpaceAfter=No
```
expl: expletive
```
13    это    это    PART    _    _    14    expl    14:expl    _
14    отличался    отличаться    VERB    _    Aspect=Imp|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Mid    6    parataxis    6:parataxis    _
15    его    он    PRON    _    Case=Gen|Gender=Masc|Number=Sing|Person=3    16    nmod    16:nmod    _
16    друг    друг    NOUN    _    Animacy=Anim|Case=Nom|Gender=Masc|Number=Sing    14    nsubj    14:nsubj    _
17    Платонов    платонов    PROPN    _    Animacy=Anim|Case=Nom|Gender=Masc|Number=Sing    16    appos    16:appos    SpaceAfter=No
```
fixed: fixed multiword expression
```
31    в    в    ADP    _    _    34    advmod    34:advmod    _
32    конце    конец    NOUN    _    Animacy=Inan|Case=Loc|Gender=Masc|Number=Sing    31    fixed    31:fixed    _
33    концов    конец    NOUN    _    Animacy=Inan|Case=Gen|Gender=Masc|Number=Plur    31    fixed    31:fixed    _
34    возмутительно    возмутительный    ADJ    _    Degree=Pos|Gender=Neut|Number=Sing|Variant=Short    5    conj    5:conj    _
```
flat: flat multiword expression
```
5    канал    канал    NOUN    _    Animacy=Inan|Case=Nom|Gender=Masc|Number=Sing    4    nsubj    4:nsubj    _
6    "    "    PUNCT    _    _    7    punct    7:punct    SpaceAfter=No
7    National    national    PROPN    _    Foreign=Yes    5    flat:foreign    5:flat:foreign    _
8    TV    tv    PROPN    _    Foreign=Yes    7    flat:foreign    7:flat:foreign    _
9    and    and    X    _    Foreign=Yes    8    flat:foreign    8:flat:foreign    _
10   Radio    radio    PROPN    _    Foreign=Yes    9    flat:foreign    9:flat:foreign    _
11   of    of    X    _    Foreign=Yes    10    flat:foreign    10:flat:foreign    _
12   Armenia    armenia    PROPN    _    Foreign=Yes    11    flat:foreign    11:flat:foreign    SpaceAfter=No
```
goeswith: goes with
```
the relation between parts of a word in a poorly edited text (ie when the division of a word into such parts violates the orthographic rules of the language)
```
iobj: indirect object
```
см. obj
20    выйти    выходить    VERB    _    Aspect=Perf|VerbForm=Inf|Voice=Act    18    xcomp    18:xcomp    _
21    на    на    ADP    _    _    22    case    22:case    _
22    сцену    сцена    NOUN    _    Animacy=Inan|Case=Acc|Gender=Fem|Number=Sing    20    obl    20:obl    _
23    и    и    CCONJ    _    _    24    cc    24:cc    _
24    раздать    раздавать    VERB    _    Aspect=Perf|VerbForm=Inf|Voice=Act    20    conj    20:conj    _
25    балеринам    балерина    NOUN    _    Animacy=Anim|Case=Dat|Gender=Fem|Number=Plur    24    iobj    24:iobj    _
26    кубки    кубок    NOUN    _    Animacy=Inan|Case=Acc|Gender=Masc|Number=Plur    24    obj    24:obj    _
```
list: list
```
the relationship between the elements of any sequence in the absence of a clear syntactic structure (the root is the first element):
```
mark: marker
```
3    я    я    PRON    _    Case=Nom|Number=Sing|Person=1    4    nsubj    4:nsubj    _
4    говорил    говорить    VERB    _    Aspect=Imp|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act    0    root    0:root    SpaceAfter=No
5    ,    ,    PUNCT    _    _    4    punct    4:punct    _
6    чтобы    чтобы    SCONJ    _    Mood=Cnd    7    mark    7:mark    _
7    запирали    запирать    VERB    _    Aspect=Imp|Mood=Ind|Number=Plur|Tense=Past|VerbForm=Fin|Voice=Act    4    ccomp    4:ccomp    _
8    дверь    дверь    NOUN    _    Animacy=Inan|Case=Acc|Gender=Fem|Number=Sing    7    obj    7:obj    SpaceAfter=No
```
nmod: nominal modifier
```
1    Такой    такой    DET    _    Case=Nom|Gender=Masc|Number=Sing    2    det    2:det    _
2    тип    тип    NOUN    _    Animacy=Inan|Case=Nom|Gender=Masc|Number=Sing    5    nsubj    5:nsubj    _
3    людей    человек    NOUN    _    Animacy=Anim|Case=Gen|Gender=Masc|Number=Plur    2    nmod    2:nmod    _
```
nsubj: nominal subject
```
1    Помощь    помощь    PROPN    _    Animacy=Inan|Case=Nom|Gender=Fem|Number=Sing    5    nsubj    5:nsubj    _2    этой    этот    DET    _    Case=Dat|Gender=Fem|Number=Sing    3    det    3:det    _
3    стране    страна    NOUN    _    Animacy=Inan|Case=Dat|Gender=Fem|Number=Sing    1    nmod    1:nmod    _
4    обычно    обычно    ADV    _    Degree=Pos    5    advmod    5:advmod    _
5    поступает    поступать    VERB    _    Aspect=Imp|Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin|Voice=Act    0    root    0:root    _
6    извне    извне    ADV    _    Degree=Pos    5    advmod    5:advmod    SpaceAfter=No
7    .    .    PUNCT    _    _    6    punct    6:punct    _
```
nsubj:pass – субъект при пассивном глаголе:
```
18    объявлялся    объявлять    VERB    _    Aspect=Imp|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Pass    0    root    0:root    _
19    строгий    строгий    ADJ    _    Case=Nom|Degree=Pos|Gender=Masc|Number=Sing    20    amod    20:amod    _
20    выговор    выговор    NOUN    _    Animacy=Inan|Case=Nom|Gender=Masc|Number=Sing    18    nsubj:pass    18:nsubj:pass    SpaceAfter=No
```
nummod: numeric modifier
```
1    В    в    ADP    _    _    3    case    3:case    _
2    2003    2003    NUM    _    _    3    nummod    3:nummod    _
3    году    год    NOUN    _    Animacy=Inan|Case=Loc|Gender=Masc|Number=Sing    7    obl    7:obl    _
```
obj: object
```
19    связь    связь    NOUN    _    Animacy=Inan|Case=Nom|Gender=Fem|Number=Sing    20    nsubj    20:nsubj    _
20    охватит    охватывать    VERB    _    Aspect=Perf|Mood=Ind|Number=Sing|Person=3|Tense=Fut|VerbForm=Fin|Voice=Act    11    acl    11:acl    _
21    всю    весь    DET    _    Case=Acc|Gender=Fem|Number=Sing    22    det    22:det    _
22    территорию    территория    NOUN    _    Animacy=Inan|Case=Acc|Gender=Fem|Number=Sing    20    obj    20:obj    _
```
obl: oblique nominal
```
1    Доставшийся    доставаться    VERB    _    Aspect=Perf|Case=Nom|Gender=Masc|Number=Sing|Tense=Past|VerbForm=Part|Voice=Mid    11    acl    11:acl    _
2    в    в    ADP    _    _    3    case    3:case    _
3    наследство    наследство    NOUN    _    Animacy=Inan|Case=Acc|Gender=Neut|Number=Sing    1    obl    1:obl    _
```
orphan: orphan
```
2    Как    как    ADV    _    Degree=Pos    3    orphan    3.1:advmod    _
3    тебе    ты    PRON    _    Case=Dat|Number=Sing|Person=2    0    root    0:root    _
4    известность    известность    NOUN    _    Animacy=Inan|Case=Nom|Gender=Fem|Number=Sing    2    nsubj    2:nsubj    SpaceAfter=No
5    ?    ?    PUNCT    _    _    4    punct    4:punct    _
```
parataxis: parataxis
```
6    ученые    ученый    NOUN    _    Animacy=Anim|Case=Nom|Gender=Masc|Number=Plur    2    nsubj    2:nsubj    _
7    древности    древность    NOUN    _    Animacy=Inan|Case=Gen|Gender=Fem|Number=Sing    6    nmod    6:nmod    _
8    -    -    PUNCT    _    _    7    punct    7:punct    _
9    астрономы    астроном    NOUN    _    Animacy=Anim|Case=Nom|Gender=Masc|Number=Plur    6    parataxis    6:parataxis    SpaceAfter=No
```
punct: punctuation
```
A punctuation mark separating the elements, connected by a writing link, joins the element following it;

tokens with the label punct have no dependent and always join the significant words (the cases of ellipsis are the exception):
```
reparandum: overridden disfluency
```
reparandum – speech failure, subject to correction by the speaker; the relationship between such a failure (dependent) and self-correction (root)
```
root: root
the root of the sentence, usually a finite verb or other predicate
```
1    Поэт    поэт    NOUN    _    Animacy=Anim|Case=Nom|Gender=Masc|Number=Sing    0    root    0:root    SpaceAfter=No
2    ,    ,    PUNCT    _    _    1    punct    1:punct    _
3    можно    можно    ADV    _    Degree=Pos    1    parataxis    1:parataxis    _
4    сказать    сказать    VERB    _    Aspect=Perf|VerbForm=Inf|Voice=Act    3    csubj    3:csubj    SpaceAfter=No
5    .    .    PUNCT    _    _    4    punct    4:punct    _
```
one tree – one root! if there is no predicate in the sentence due to the ellipse, one of the dependent words rises to the status of the root, and the others join it
```
1    И    и    CCONJ    _    _    4    cc    4:cc    _
2    это    это    PRON    _    Animacy=Inan|Case=Nom|Gender=Neut|Number=Sing    4    nsubj    4:nsubj    _
3    не    не    PART    _    _    4    advmod    4:advmod    _
4    хуже    плохой    ADJ    _    Degree=Cmp    0    root    0:root    SpaceAfter=No
5    :    :    PUNCT    _    _    4    punct    4:punct    _
```
vocative: vocative
```
22    Ты    ты    PRON    _    Case=Nom|Number=Sing|Person=2    23    nsubj    23:nsubj    _
23    знаешь    знать    VERB    _    Aspect=Imp|Mood=Ind|Number=Sing|Person=2|Tense=Pres|VerbForm=Fin|Voice=Act    28    parataxis    28:parataxis    SpaceAfter=No
24    ,    ,    PUNCT    _    _    23    punct    23:punct    _
25    Володь    володя    PROPN    _    Animacy=Anim|Case=Voc|Gender=Masc|Number=Sing    23    vocative    23:vocative    SpaceAfter=No
```
xcomp: open clausal complement
```
11    в    в    ADP    _    _    13    case    13:case    _
12    1956    1956    NUM    _    _    13    nummod    13:nummod    _
13    году    год    NOUN    _    Animacy=Inan|Case=Loc|Gender=Masc|Number=Sing    14    obl    14:obl    _
14    начал    начинать    VERB    _    Aspect=Perf|Gender=Masc|Mood=Ind|Number=Sing|Tense=Past|VerbForm=Fin|Voice=Act    6    conj    6:conj    _
15    работать    работать    VERB    _    Aspect=Imp|VerbForm=Inf|Voice=Act    14    xcomp    14:xcomp    _
```
