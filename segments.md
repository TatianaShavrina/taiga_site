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
			
# Распределение сегментов

| Ресурс                | количество   текстов | количество   токенов | количество слов | в среднем слов   на текст |
|-----------------------|----------------------|----------------------|-----------------|--------------------------:|
| новости               | 471061               | 92783634             | 81563551        | 121.25                    |
| художественные тексты | 53398                | 239722547            | 189065703       | 2401                      |
| остальное             | 33772                | 114354769            | 207782890       | 1177                      |

#### Распределение токенов корпуса по сегментам

![alt text](https://github.com/TatianaShavrina/taiga_site/blob/master/stats/pie-chart-taiga.png "corpus segments"){:class="img-responsive"}

# Карточки сегментов

### Стихи ру

#### Метаатрибуты текстов:
 - 'textrubric' - жанр стиха
 - 'textid' - уникальный айди текста
 - 'textname' - заголовок
 - 'author' - ник автора
 - 'authortexts' - количество текстов автора
 - 'authorreaders' - количество читателей автора
 - 'date' - дата написания текста
 - 'time' - время написания текста
 - 'source' -  ссылка на первоисточник (иногда бывает удален)

#### Распределение стихов по textrubric:

![alt text](https://github.com/TatianaShavrina/taiga_site/blob/master/stats/stihi_ru_rubrics.png "corpus segments")

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/stihi_ru.md)

### Проза ру

#### Метаатрибуты текстов:
 - 'textrubric' - жанр текста
 - 'textid' - уникальный айди текста
 - 'textname' - заголовок
 - 'author' - ник автора
 - 'authortexts' - количество текстов автора
 - 'authorreaders' - количество читателей автора
 - 'date' - дата написания текста
 - 'time' - время написания текста
 - 'source' -  ссылка на первоисточник (иногда бывает удален)
 
#### Распределение текстов по жанрам:

![alt text](https://github.com/TatianaShavrina/taiga_site/blob/master/stats/proza_ru_textrubric.png "corpus segments")

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/proza_ru.md)

### Лента ру

#### Метаатрибуты текстов:
 - 'textid' - уникальный айди текста
 - 'textname' - заголовок
 - 'textrubric' - ребрика новости
 - 'date' - дата написания текста
 - 'time' - время написания текста
 - 'tags' - теги новости
 - 'source' -  ссылка на первоисточник (иногда бывает удален)
 
#### Распределение новостей по рубрикам:

![alt text](https://github.com/TatianaShavrina/taiga_site/blob/master/stats/lenta_rubrics.png "corpus segments")

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/lenta_ru.md)

### Интерфакс 

#### Метаатрибуты текстов:
 - 'textid' - уникальный айди текста
 - 'textname' - заголовок
 - 'textrubric' - рубрика новости
 - 'date' - дата написания текста
 - 'time' - время написания текста
 - 'tags' - теги новости
 - 'source' -  ссылка на первоисточник (иногда бывает удален)
 
#### Распределение новостей по тегам:

![alt text](https://github.com/TatianaShavrina/taiga_site/blob/master/stats/interfax_tags.png "corpus segments")

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/interfax.md)

### NPlus1 

#### Метаатрибуты текстов:
 - 'textid' - уникальный айди текста
 - 'textname' - заголовок
 - 'textdiff' - сложность текста
 - 'author' - имя автора
 - 'textrubric' - рубрика новости
 - 'date' - дата написания текста
 - 'time' - время написания текста
 - 'tags' - теги новости
 - 'source' -  ссылка на первоисточник (иногда бывает удален)
 
#### Распределение текстов по сложности:

![alt text](https://github.com/TatianaShavrina/taiga_site/blob/master/stats/nplus1_diff.png "corpus segments")

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/nplus1.md)

### Комсомольская правда

#### Метаатрибуты текстов:
 - 'textid' - уникальный айди текста
 - 'textname' - заголовок
 - 'textregion' - регион новости по поддомену
 - 'textrubric' - рубрика новости
 - 'date' - дата написания текста
 - 'time' - время написания текста
 - 'tags' - теги новости
 - 'source' -  ссылка на первоисточник (иногда бывает удален)
 
#### Распределение новостей по регионам:

![alt text](https://github.com/TatianaShavrina/taiga_site/blob/master/stats/kp_regions.png "corpus segments")

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/komsomol.md)

### Журнальный зал

#### Метаатрибуты текстов:
 - 
 
Распределение  по :

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/magazines.md)

### Фонтанка ру

#### Метаатрибуты текстов:
 - 
 
Распределение  по :

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/fontanka.md)

### Арзамас 

#### Метаатрибуты текстов:
 - 'textid' - уникальный айди текста
 - 'textname' - заголовок
 - 'authors' - имя автора
 - 'authorprofession' - профессия автора
 - 'about_author' - короткое описание со страницы автора
 - 'textrubric' - рубрика новости
 - 'date' - дата написания текста
 - 'time' - время написания текста
 - 'tags' - теги новости
 - 'source' -  ссылка на первоисточник (иногда бывает удален)
       
#### Распределение текстов по рубрикам:

![](https://github.com/TatianaShavrina/taiga_site/blob/master/stats/arzamas_rubrics.png "corpus segments")

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/arzamas.md)

### TV Subtitles на русском  

#### Метаатрибуты текстов:
 - 
 
Распределение  по :

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/tvsubtitles_ru.md)

### TV Subtitles на других языках 

#### Метаатрибуты текстов:
 - 
 
Распределение  по :

Больше статистики см [здесь](https://github.com/TatianaShavrina/taiga_site/blob/master/corpus/tvsubtitles_ino.md)
