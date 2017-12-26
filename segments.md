
# Corpus segments

| Ресурс                        | количество текстов | количество токенов | количество слов | в среднем слов на текст |
|-------------------------------|--------------------|--------------------|-----------------|------------------------:|
| Стихи ру                      | 4249               | 1040449            | 813413          | 96.0                    |
| Проза ру                      | 2505               | 8490399            | 6716361         | 1009.0                  |
| Лента ру                      | 36446              | 8752681            | 7290281         | 179.0                   |
| Интерфакс                     | 46429              | 7301002            | 6128555         | 87.0                    |
| NPlus1                        | 7696               | 2090506            | 1788361         | 213.0                   |
| Комсомольская правда          | 45503              | 5683046            | 4723543         | 102.0                   |
| Журнальный зал                | 39890              | 239722547          | 189065703       | 2401.0                  |
| Фонтанка ру                   | 342683             | 71046905           | 59844450        | 117.0                   |
| Арзамас                       | 311                | 451720             | 371709          | 958.0                   |
| TV Subtitles на русском       | 7899               | 38300057           | 28429392        | 3609.0                  |
| TV Subtitles на других языках | 11112              | 63981638           | 49974754        | 4501.5                  |
| <b>Всего </b>                 | <b>544723</b>      | <b>446860950</b>   | <b>355146522</b>| <b>1206.5</b>           |

# Segment distribution

| Resource              | texts                | tokens               | words           | words, median per text    |
|-----------------------|----------------------|----------------------|-----------------|--------------------------:|
| news                  | 471061               | 92783634             | 81563551        | 121.25                    |
| literature            | 53398                | 239722547            | 189065703       | 2401                      |
| other                 | 33772                | 114354769            | 207782890       | 1177                      |

#### Token distribution per segment

![alt text]({{ site.baseurl }}/assets/images/pie-chart-taiga.png "corpus segments")

# Segment information

### Stihi ru

#### Text metaattributes:
 - 'textrubric' - poem genre
 - 'textid' - unique text id
 - 'textname' - title
 - 'author' - authors nickname
 - 'authortexts' - amount of authors texts
 - 'authorreaders' - amount of authors readers
 - 'date' - date text was written
 - 'time' - time text was written
 - 'source' -  URL (sometimes can be not available any more)

#### Textrubric distribution of poems:

![alt text]({{ site.baseurl }}/assets/images/stihi_ru_rubrics.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/stihi_ru.md)

### Proza ru

#### Text metaattributes:
 - 'textrubric' - text genre
 - 'textid' - unique text id
 - 'textname' - title
 - 'author' - authors nickname
 - 'authortexts' - amount of authors texts
 - 'authorreaders' - amount of authors readers
 - 'date' - date text was written
 - 'time' - time text was written
 - 'source' -  URL (sometimes can be not available any more)

#### Genre distribution of texts:

![alt text]({{ site.baseurl }}/assets/images/proza_ru_textrubric.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/proza_ru.md)

### Lenta ru

#### Text metaattributes:
 - 'textid' - unique text id
 - 'textname' - title
 - 'textrubric' - rubrics
 - 'date' - date text was written
 - 'time' - time text was written
 - 'tags' - tags
 - 'source' - URL (sometimes can be not available any more)

#### Rubric distribution of news:

![alt text]({{ site.baseurl }}/assets/images/lenta_rubrics.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/lenta_ru.md)

### Interfax

#### Text metaattributes:
 - 'textid' - unique text id
 - 'textname' - title
 - 'textrubric' - rubrics
 - 'date' - date text was written
 - 'time' - time text was written
 - 'tags' - tags
 - 'source' - URL (sometimes can be not available any more)

#### Rubric distribution of news:

![alt text]({{ site.baseurl }}/assets/images/interfax_tags.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/interfax.md)

### NPlus1

#### Text metaattributes:
 - 'textid' - unique text id
 - 'textname' - title
 - 'textdiff' - text readability
 - 'author' - authors name
 - 'textrubric' - rubric
 - 'date' - date text was written
 - 'time' - time text was written
 - 'tags' - tags
 - 'source' - URL (sometimes can be not available any more)

#### Readability distribution of texts (from 0 to 10):

![alt text]({{ site.baseurl }}/assets/images/nplus1_diff.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/nplus1.md)

### Komsomolskaya pravda

#### Text metaattributes:
 - 'textid' - unique text id
 - 'textname' - title
 - 'textregion' - region of the news 
 - 'textrubric' - rubrics
 - 'date' - date text was written
 - 'time' - time text was written
 - 'tags' - tags
 - 'source' - URL (sometimes can be not available any more)

#### Region distribution of news:

![alt text]({{ site.baseurl }}/assets/images/kp_regions.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/komsomol.md)

### Russian Magazines Hall

#### Text metaattributes:
 - 'textid' - unique text id
 - 'textname' - title
 - 'magazine' - source magazine
 - 'author' - author's name
 - 'date' - date text was written
 - 'time' - time text was written
 - 'tags' - tags
 - 'source' - URL (sometimes can be not available any more)

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/magazines.md)

### Fontanka ru

#### Text metaattributes:
 - 'textid' - unique text id
 - 'textname' - title
 - 'textregion' - region of the news 
 - 'textrubric' - rubrics
 - 'date' - date text was written
 - 'time' - time text was written
 - 'tags' - tags
 - 'source' - URL (sometimes can be not available any more)

#### Year distribution of news:

![alt text]({{ site.baseurl }}/assets/images/fontanka_years.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/fontanka.md)

### Arzamas

#### Text metaattributes:
 - 'textid' - unique text id
 - 'textname' - title
 - 'authors' - author's name
 - 'authorprofession' - author's profession
 - 'about_author' - about the author
 - 'textrubric' - rubrics
 - 'date' - date text was written
 - 'time' - time text was written
 - 'tags' - tags
 - 'source' - URL (sometimes can be not available any more)

#### Rubric distribution of texts:

![alt text]({{ site.baseurl }}/assets/images/arzamas_rubrics.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/arzamas.md)

### TV Subtitles

#### Text metaattributes:
 - 'textid' - unique text id
 - 'title' - film title
 - 'language' - language
 - 'filepath' - path to file in this language

#### Language distribution of texts:

![alt text]({{ site.baseurl }}/assets/images/tvsubtitles_langs.png "corpus segments")

For more statistics [see](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/tvsubtitles.md)
