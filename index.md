

## We have gathered the resources with respect to popular NLP-problems:

- thematic modelling - news with theme tags, all the sites which provide rubrication (news, poems, prose)
- readability of texts - a popular science magazine NPlus1 has a readability metric for each text, provided by editor.
- NER and fact extraction - news with references to mentioned person’s page or wiki-information, news with personalia tags
- key-words extraction - news with key-word tags, hashtags on social media
- authorship attribution - all the texts with author information - magazines, news, and more important - social media - with gender, age, city, time and education mark-up.
- chat-bot training - open-source film subtitles
- text generation - any resource depending on genre
- rare words studying, frequency dictionaries - literary magazines, social media
- morphological and syntactic parsers - any resource with respect to the genre

By now, 350 millions of words are 50% literary texts (33 literary magazines), 25% of news (Interfax, Fontanka, Lenta ru, Komsomolskaya Pravda, ) and 25% of other (popular science - NPlus1, culture - Arzamas, social networks - VKontakte, amateur poems - stihi.ru and prose - proza.ru), with documentation [available](https://tatianashavrina.github.io/taiga_site/segments).

In our methodological preparation for creating a new resource, we have postulated 5 main principles: 
1) open source 
2) big data 
3) clear data 
4) coverage of linguistic variation 
Corpus data should represent all possible variability in unbiased proportions for each separate resource. 
5) solvability in a given metric 
(аdequacy of data composition and its’ features to the applications)

With these principles, we believe that a corpus product that meets modern requirements of corpus linguistics can be created - it will not be a black box, it will be reflecting modern language and its features, not biased and capable of encouraging more cooperation between developers and linguists. 


## Some stats about Taiga corpus:

| Resource                      | texts              | tokens             | words           | median words per text   |
|-------------------------------|--------------------|--------------------|-----------------|------------------------:|
| stihi ru (poems)              | 4249               | 1040449            | 813413          | 96.0                    |
| proza ru (proze)              | 2505               | 8490399            | 6716361         | 1009.0                  |
| Lenta ru (news)               | 36446              | 8752681            | 7290281         | 179.0                   |
| Interfax (news)               | 46429              | 7301002            | 6128555         | 87.0                    |
| NPlus1  (popular science)     | 7696               | 2090506            | 1788361         | 213.0                   |
| Komsomol truth (news)         | 45503              | 5683046            | 4723543         | 102.0                   |
| magazine Hall (literature)    | 39890              | 239722547          | 189065703       | 2401.0                  |
| Fontanka ru (news)            | 342683             | 71046905           | 59844450        | 117.0                   |
| Arzamas (culture mag)         | 311                | 451720             | 371709          | 958.0                   |
| TV Subtitles in Russian       | 7899               | 38300057           | 28429392        | 3609.0                  |
| TV Subtitles in other langs   | 11112              | 63981638           | 49974754        | 4501.5                  |
| <b>Total </b>                 | <b>544723</b>      | <b>446860950</b>   | <b>355146522</b>| <b>1206.5</b>           |

## This project is a project in the [HSE Compling](https://www.hse.ru/en/ma/ling/) framework

## References:
Shavrina T., Shapovalova O. (2017) TO THE METHODOLOGY OF CORPUS CONSTRUCTION FOR MACHINE LEARNING: «TAIGA» SYNTAX TREE CORPUS AND PARSER. in proc. of "CORPORA2017", international conference , Saint-Petersbourg, 2017.

## Support or Contact

Check out our [documentation](https://github.com/TatianaShavrina/taiga_site/blob/master/segments.md) or [contact us](mailto:rybolos@gmail.com) and we’ll help you sort it out.

We welcome users to ask question on [Google Groups](https://groups.google.com/forum/#!forum/taigacorpus)!
