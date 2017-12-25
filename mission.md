## Why are we doing Taiga corpus?
A wisely constructed web corpus has a lot more potential applications than is classically accounted to have. 
The “web as corpus” paradigm recently has had its natural continuation as a formulation “web as train set” [Kilgarriff 2001]. Open-source websites provide ample opportunities for NLP-developers and computational linguists, who nevertheless have to gather all the corresponding data by themselves, repeating the same actions for cleaning and de-duplicating the material, as traditional web corpora provide only search interface and do not give any access to the whole data. 

The "Taiga" corpus project unites the needs of developers, machine learners and computational linguists, as a web corpus for big linguistic data analysis and actual NLP and NLU systems modeling. Its main aim is to influence the culture of corpus research for Russian language and reflect the paradigm shift in linguistic methodology. 

Below the  framework of the project, corpus construction principles and obtained results are described. 

In the last decade corpus projects, whose volume exceeds a billion words, are rapidly developing. For the Russian language there are, for example, ruWAC [Baroni et al 2009], RuTenTen [Jakubicek et al. 2013], General Internet-Corpus of Russian [Belikov et al. 2013], Aranea Russicum [Benko 2014], Google Ngrams. Their volume is their undeniable dignity, but all these projects are united by one more feature - they provide access to the search, but you can not get their materials for development or autonomous statistical analysis. Corpus linguistics is positioned as a more accurate and computational approach to language, but in fact, a researcher studying a specific linguistic phenomenon, wanting to understand what the absolute frequency or IPM of a phenomenon obtained on corpus does mean, either relies on comparing the search results on different resources or on comparing the relative frequencies of various phenomena (which is laborious in both cases), or, more often and worse, just relies on his own intuition.
Interpretation of the corpus search result is a non-trivial task when the distribution of frequencies of words, parts of speech, text sources and other parameters is hidden from the user [Lagutin et al.2016].

If one wants to escape this statistical black box challenge, only fully open data can be used. From 2017, there is also a good open-source resource for many languages - conll shared task-2017 training set (raw data) [Ginter et al. 2017], which comes with morphological annotation and has a great amount of common crawl web-pages.  With respect to the project, we nevertheless claim that in this formation, conll shared data is very good for training morphological and syntactic parsers, but not at all convenient for carrying out any linguistic analysis, as we do not have sufficient information about text sources, their genres, authors, etc. 
Coming up with the problem of representativity on web corpora and big linguistic data, we can reformulate it, basing on the statistical idea of “language is a large set of rare events” and sufficient data amount on every non-hapax linguistic event. Coverage of language variation (firstly introduced by [Belikov et al, 2013]) then is a new main big corpus characteristics.

## Web as train set
In our methodological preparation for creating a new resource [Shavrina, Shapovalova 2017], we have postulated 5 main principles, which allow a modern web-corpus to be relevant from the point of view of the engineering approach to language:
1) open source 
A corpus should be available to use the material at one’s discretion, to modify it, to add new data to it, and publish it. Developing a good vector model on the data, composing new genre-specific frequency dictionaries, etc. then becomes a faster side products by a community of corpus users.
Texts of the corpus can be collected from open sources only, which, nevertheless, can be quite sufficient, since now there are a lot of such resources, and compiling their complete list for each language is a separate, voluminous task.
2) big data
A corpus should provide sufficient volume of the data (more than 10 million words) - thus it is possible to collect implicit information, for example about rare words and their compatibility, syntactic behavior  of individual words and different meanings of homonyms. This principle is also very important for users, as for many applications doubling the training data improves the quality more than developing a more complicated algorithm [Banko , Brill 2001].
3) clear data
There should be minimum share of errors embedded in the data itself - this includes both the sufficient quality of linguistic markup, and the completeness of meta-text information, the ability to uniquely separate one segment or genre from another, to find out their balance for each research. 
4) coverage of linguistic variation
Corpus data should represent all possible variability in unbiased proportions for each separate resource. 
5) solvability in a given metric 
Adequacy of data composition and its’ features to the applications is one of the most important principles - otherwise it is useless. Meta-information, such as author’s gender, age, text theme, etc (depending on the task) should be sufficient for the research, and on the part of the authors, it is necessary to provide maximum opportunities for users.

With these principles, we believe that a corpus product that meets modern requirements of corpus linguistics can be created - it will not be a black box, it will be reflecting modern language and its features, not biased and capable of encouraging more cooperation between developers and linguists. Refusal of the search interface, in our opinion, can be justified in this case, since obtaining examples for the concrete hypothesis, obtaining an IPM for a specific comparison on an unknown volume of data with an unknown distribution is a long-standing problem, which we wish to escape. As an alternative, a python-compatible API can be provided for community, which will include functions for statistic analysis.

## Possibilities of corpora for machine learning
By now, our corpus contains data from 11 sites, 44 sources and is of 480 million words, all documenting modern Russian language (we considered “modern Russian” as a language of speakers younger than 60 years old). For training, we have chosen 3 main segments, all differing stylistically and by word frequency: literary texts, news and “other” - various resources for specific needs of NLP. Literary texts come from literary magazines; news are taken a lot of open-source news aggregators; “other” is extracted from popular science and culture magazines, social networks and forums with amateur poetry and prose. 

### We have gathered the resources with respect to popular NLP-problems:

+ thematic modelling - news with theme tags, all the sites which provide rubrication (news, poems, prose)
+ readability of texts - a popular science magazine NPlus1 has a readability metric for each text, provided by editor.
+ NER and fact extraction - news with references to mentioned person’s page or wiki-information, news with personalia tags
+ key-words extraction - news with key-word tags, hashtags on social media
+ authorship attribution - all the texts with author information - magazines, news, and more important - social media - with gender, age, city, time and education mark-up.
+ chat-bot training - open-source film subtitles 
+ text generation - any resource depending on genre
+ rare words studying, frequency dictionaries - literary magazines, social media
+ morphological and syntactic parsers - any resource with respect to the genre


### References
+ Kilgarriff, A. (2001). The Web as corpus. Proceedings of Corpus Linguistics 2001
+ Baroni, M., Bernardini, S., Ferraresi, A., & Zanchetta, E. (2009). The WaCky wide Web: A collection of very large linguistically processed Web-crawled corpora. Language Resources and Evaluation, 43, 209–226.
+ Benko, Vladimir (2014) Aranea: Yet Another Family of (Comparable) Web Corpora. In Petr Sojka, Ales Horak, Ivan Kopecek and Karel Pala (Eds.): Text, Speech and Dialogue. 17th International Conference, TSD 2014, Brno, Czech Republic, September 8-12, 2014. Proceedings. LNCS 8655.Springer International Publishing Switzerland, 2014. pp. 257-264. ISBN: 978-3-319-10815-5 (Print), 978-3-319-10816-2 (Online).
+ Jakubicek, M., A. Kilgarriff, V. Kovar, P. Rychly, and V. Suchomel (2013) The TenTen corpus family. Lancaster: In Proc. Int. Conf. on Corpus Linguistics.
+ Ginter, Filip; Hajič, Jan; Luotolahti, Juhani; et al., 2017, CoNLL 2017 Shared Task - Automatically Annotated Raw Texts and Word Embeddings, LINDAT/CLARIN digital library at the Institute of Formal and Applied Linguistics, Charles University, http://hdl.handle.net/11234/1-1989. 
+ Belikov V., Kopylov N., Piperski A., Selegey V., Sharoff S., (2013) Big and diverse is beautiful: A large corpus of Russian to study linguistic variation. In Web as Corpus Workshop (WAC-8).
+ John Walker (2015) Big Data: A Revolution That Will Transform How We Live, Work, and Think. Evaluating Non-Expert Annotations for Natural Language Tasks http://www.tandfonline.com/doi/abs/10.2501/IJA-33-1-181-183?journalCode=rina20 
+ Michele Banko and Eric Brill (2001) Scaling to Very Very Large Corpora for Natural Language Disambiguation. Microsoft Research, In Proc. of ACL-2001. http://aclweb.org/anthology/P/P01/P01-1005.pdf 
+ Shavrina T., Shapovalova O. (2017) TO THE METHODOLOGY OF CORPUS CONSTRUCTION FOR MACHINE LEARNING: «TAIGA» SYNTAX TREE CORPUS AND PARSER. in proc. of "CORPORA2017", international conference , Saint-Petersbourg, 2017.
+ Snow, R., O’Connor, B., Jurafsky, D., & Ng, A. Y. (2008). Cheap and fast—but is it good? Evaluating non-expert annotations for natural language tasks. In M. Lapata & H. T. Ng (Eds.), Proceedings of the Conference on Empirical Methods in Natural Language Processing (pp. 254–263). New York: ACM www.aclweb.org/anthology/D08-1027
+ Belikov V., Kopylov N., Piperski A., Selegey V., Sharoff S., (2013) Big and diverse is beautiful: A large corpus of Russian to study linguistic variation. In Web as Corpus Workshop (WAC-8).
+ Lyashevskaya, O., Droganova K., Zeman, D., Alexeeva, M., Gavrilova, T., Mustafina, N., Shakurova, E. (2016). Universal Dependencies for Russian: a New Syntactic Dependencies Tagset. In Series: Linguistics, WP BRP 44/LNG/2016.
+ Lagutin M., Kuratov Y., Kopylov N. (2016) Statistical processing  of  Search results in differential corpora. Computational Linguistics and Intellectual Technologies: Proceedings of the International Conference “Dialogue 2016” Moscow, June 1–4, 2016

=======
---
permalink: /mission
---

