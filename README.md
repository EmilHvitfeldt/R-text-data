
<!-- README.md is generated from README.Rmd. Please edit that file -->

# R Text Data Compilation

The goal of this repository is to act as a collection of textual data
set to be used for training and practice in text mining/NLP in R. This
repository will not be a guide on how to do text analysis/mining but
rather how to get a data set to get started with minimal hassle.

# Table of Contents

-   [Main page](#R-text-data)
-   [CRAN packages](#cran-packages)
    -   [janeaustenr](#janeaustenr)
    -   [quRan](#quran)
    -   [scriptuRs](#scripturs)
    -   [hcandersenr](#hcandersenr)
    -   [proustr](#proustr)
    -   [gutenbergr](#gutenbergr)
    -   [text2vec](#text2vec)
    -   [epubr](#epubr)
-   [Github packages](#github-packages)
    -   [sacred](#sacred)
    -   [harrypotter](#harrypotter)
    -   [hgwellsr](#hgwellsr)
    -   [jeeves](#jeeves)
    -   [koanr](#koanr)
    -   [rperseus](#rperseus)
    -   [subtools](#subtools)
-   [Wild data](#wild-data)
    -   Cornell data
        -   [polarity dataset v2.0](#polarity-dataset-v20)
        -   [sentence polarity dataset
            v1.0](#sentence-polarity-dataset-v10)
        -   [scale dataset v1.0](#scale-dataset-v10)
        -   [subjectivity dataset v1.0](#subjectivity-dataset-v10)
    -   [SouthParkData](#southparkdata)
    -   [Saudi Newspapers Corpus](#saudi-newspapers-corpus)

## CRAN packages

### janeaustenr

First we have the **janeaustenr** package popularized by Julia Silge in
[tidytextmining](https://www.tidytextmining.com/).

``` r
#install.packages("janeaustenr")
library(janeaustenr)
```

`janeaustenr` includes 6 books; `emma`, `mansfieldpark`,
`northangerabbey`, `persuasion`, `prideprejudice` and `sensesensibility`
all formatted as a character vector with elements of about 70
characters.

``` r
head(emma, n = 15)
#>  [1] "EMMA"                                                               
#>  [2] ""                                                                   
#>  [3] "By Jane Austen"                                                     
#>  [4] ""                                                                   
#>  [5] ""                                                                   
#>  [6] ""                                                                   
#>  [7] ""                                                                   
#>  [8] "VOLUME I"                                                           
#>  [9] ""                                                                   
#> [10] ""                                                                   
#> [11] ""                                                                   
#> [12] "CHAPTER I"                                                          
#> [13] ""                                                                   
#> [14] ""                                                                   
#> [15] "Emma Woodhouse, handsome, clever, and rich, with a comfortable home"
```

All the books can also be found combined into one data.frame in the
function `austen_books()`

``` r
dplyr::glimpse(austen_books())
#> Observations: 73,422
#> Variables: 2
#> $ text <chr> "SENSE AND SENSIBILITY", "", "by Jane Austen", "", "(1811...
#> $ book <fct> Sense & Sensibility, Sense & Sensibility, Sense & Sensibi...
```

Examples:

-   <https://juliasilge.com/blog/if-i-loved-nlp-less/>

## quRan

The **quRan** package contains the complete text of the Qur’an in Arabic
(with and without vowels) and in English (the Yusuf Ali and Saheeh
International translations).

``` r
#install.packages("quRan")
library(quRan)
```

``` r
dplyr::glimpse(quran_ar)
#> Observations: 6,236
#> Variables: 18
#> $ surah_id             <int> 1, 1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2, 2, 2…
#> $ ayah_id              <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, …
#> $ surah_title_ar       <fct> الفاتحة, الفاتحة, الفاتحة, الفاتحة, الفاتحة…
#> $ surah_title_en       <fct> Al-Faatiha, Al-Faatiha, Al-Faatiha, Al-Faat…
#> $ surah_title_en_trans <fct> The Opening, The Opening, The Opening, The …
#> $ revelation_type      <chr> "Meccan", "Meccan", "Meccan", "Meccan", "Me…
#> $ text                 <chr> "﻿بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ", …
#> $ surah                <int> 1, 1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2, 2, 2…
#> $ ayah                 <int> 1, 2, 3, 4, 5, 6, 7, 1, 2, 3, 4, 5, 6, 7, 8…
#> $ ayah_title           <chr> "1:1", "1:2", "1:3", "1:4", "1:5", "1:6", "…
#> $ juz                  <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
#> $ manzil               <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
#> $ page                 <int> 1, 1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 3, 3, 3…
#> $ hizb_quarter         <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
#> $ sajda                <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, F…
#> $ sajda_id             <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
#> $ sajda_recommended    <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
#> $ sajda_obligatory     <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
```

Examples:

[Twitter
thread](https://twitter.com/andrewheiss/status/1078428352577327104)

## scriptuRs

The **scriptuRs** package full text of the Standard Works for The Church
of Jesus Christ of Latter-day Saints: the Old and New Testaments, the
Book of Mormon, the Doctrine and Covenants, and the Pearl of Great
Price. Each volume is in a data frame with a row for each verse, along
with 19 columns of detailed metadata.

``` r
#install.packages("scriptuRs")
library(scriptuRs)
```

``` r
dplyr::glimpse(scriptuRs::book_of_mormon)
#> Observations: 6,604
#> Variables: 19
#> $ volume_id          <dbl> 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, …
#> $ book_id            <dbl> 67, 67, 67, 67, 67, 67, 67, 67, 67, 67, 67, 6…
#> $ chapter_id         <dbl> 1190, 1190, 1190, 1190, 1190, 1190, 1190, 119…
#> $ verse_id           <dbl> 31103, 31104, 31105, 31106, 31107, 31108, 311…
#> $ volume_title       <chr> "Book of Mormon", "Book of Mormon", "Book of …
#> $ book_title         <chr> "1 Nephi", "1 Nephi", "1 Nephi", "1 Nephi", "…
#> $ volume_long_title  <chr> "The Book of Mormon", "The Book of Mormon", "…
#> $ book_long_title    <chr> "The First Book of Nephi", "The First Book of…
#> $ volume_subtitle    <chr> "Another Testament of Jesus Christ", "Another…
#> $ book_subtitle      <chr> "His Reign and Ministry", "His Reign and Mini…
#> $ volume_short_title <chr> "BoM", "BoM", "BoM", "BoM", "BoM", "BoM", "Bo…
#> $ book_short_title   <chr> "1 Ne.", "1 Ne.", "1 Ne.", "1 Ne.", "1 Ne.", …
#> $ volume_lds_url     <chr> "bm", "bm", "bm", "bm", "bm", "bm", "bm", "bm…
#> $ book_lds_url       <chr> "1-ne", "1-ne", "1-ne", "1-ne", "1-ne", "1-ne…
#> $ chapter_number     <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
#> $ verse_number       <dbl> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14…
#> $ text               <chr> "I, Nephi, having been born of goodly parents…
#> $ verse_title        <chr> "1 Nephi 1:1", "1 Nephi 1:2", "1 Nephi 1:3", …
#> $ verse_short_title  <chr> "1 Ne. 1:1", "1 Ne. 1:2", "1 Ne. 1:3", "1 Ne.…
```

Examples:

-   [Tidy text, parts of speech, and unique words in the
    Bible](https://www.andrewheiss.com/blog/2018/12/26/tidytext-pos-john/)

### hcandersenr

The **hcandersenr** package includes many of H.C. Andersen’s fairy tales
in 5 difference languages.

``` r
#install.packages("hcandersenr")
library(hcandersenr)
```

The fairy tales are found in the following data frames `hcandersen_en`,
`hcandersen_da`, `hcandersen_de`, `hcandersen_es` and `hcandersen_fr`
for the English, Danish, German, Spanish and French versions
respectively. Please be advised that all fairy tales aren’t available in
all languages in this package.

``` r
dplyr::glimpse(hcandersen_en)
#> Observations: 31,380
#> Variables: 2
#> $ text <chr> "A soldier came marching along the high road: \"Left, right…
#> $ book <chr> "The tinder-box", "The tinder-box", "The tinder-box", "The …
```

All the fairy tales are collected in the following data.frame:

``` r
dplyr::glimpse(hca_fairytales())
#> Observations: 126,102
#> Variables: 3
#> $ text     <chr> "Der kom en soldat marcherende hen ad landevejen: én, t…
#> $ book     <chr> "The tinder-box", "The tinder-box", "The tinder-box", "…
#> $ language <chr> "Danish", "Danish", "Danish", "Danish", "Danish", "Dani…
```

Examples:

Still pending.

### proustr

This **proustr** packages gives you access to tools designed to do
Natural Language Processing in French.

``` r
#install.packages("proustr")
library(proustr)
```

Furthermore it includes the following 7 books

-   Du côté de chez Swann (1913): `ducotedechezswann`.
-   À l’ombre des jeunes filles en fleurs (1919):
    `alombredesjeunesfillesenfleurs`.
-   Le Côté de Guermantes (1921): `lecotedeguermantes`.
-   Sodome et Gomorrhe (1922) : `sodomeetgomorrhe`.
-   La Prisonnière (1923) :`laprisonniere`.
-   Albertine disparue (1925, also know as : La Fugitive) :
    `albertinedisparue`.
-   Le Temps retrouvé (1927) : `letempretrouve`.

Which are all found in the `proust_books()` function.

``` r
dplyr::glimpse(proust_books())
#> Observations: 4,690
#> Variables: 4
#> $ text   <chr> "Longtemps, je me suis couché de bonne heure. Parfois, à …
#> $ book   <chr> "Du côté de chez Swann", "Du côté de chez Swann", "Du côt…
#> $ volume <chr> "Première partie : Combray", "Première partie : Combray",…
#> $ year   <dbl> 1913, 1913, 1913, 1913, 1913, 1913, 1913, 1913, 1913, 191…
```

### gutenbergr

The **gutenbergr** package allows for search and download of public
domain texts from [Project Gutenberg](https://www.gutenberg.org/).
Currently includes more then 57,000 free eBooks.

``` r
#install.packages("gutenbergr")
library(gutenbergr)
```

To use **gutenbergr** you must know the Gutenberg id of the work you
wish to analyze. A text search of the works can be done using the
`gutenberg_works` function.

``` r
gutenberg_works(title == "Wuthering Heights")
#> # A tibble: 1 x 8
#>   gutenberg_id title author gutenberg_autho… language gutenberg_books…
#>          <int> <chr> <chr>             <int> <chr>    <chr>           
#> 1          768 Wuth… Bront…              405 en       Gothic Fiction/…
#> # … with 2 more variables: rights <chr>, has_text <lgl>
```

With that id you can use the `gutenberg_download()` function to

``` r
gutenberg_download(768)
#> Determining mirror for Project Gutenberg from http://www.gutenberg.org/robot/harvest
#> Using mirror http://aleph.gutenberg.org
#> # A tibble: 12,085 x 2
#>    gutenberg_id text                                                       
#>           <int> <chr>                                                      
#>  1          768 WUTHERING HEIGHTS                                          
#>  2          768 ""                                                         
#>  3          768 ""                                                         
#>  4          768 CHAPTER I                                                  
#>  5          768 ""                                                         
#>  6          768 ""                                                         
#>  7          768 1801.--I have just returned from a visit to my landlord--t…
#>  8          768 neighbour that I shall be troubled with.  This is certainl…
#>  9          768 country!  In all England, I do not believe that I could ha…
#> 10          768 situation so completely removed from the stir of society. …
#> # … with 12,075 more rows
```

Examples:

Still pending.

### text2vec

While the **text2vec** package is data package by itself, it does
include a textual data set inside.

``` r
#install.packages("text2vec")
library(text2vec)
```

The data frame `movie_review` contains 5000 IMDB movie reviews selected
for sentiment analysis. It has been preprocessed to include sentiment
that means that an IMDB rating \< 5 results in a sentiment score of 0,
and a rating \>=7 has a sentiment score of 1.

``` r
dplyr::glimpse(movie_review)
#> Observations: 5,000
#> Variables: 3
#> $ id        <chr> "5814_8", "2381_9", "7759_3", "3630_4", "9495_8", "819…
#> $ sentiment <int> 1, 1, 0, 0, 1, 1, 0, 0, 0, 1, 0, 1, 1, 0, 0, 0, 0, 0, …
#> $ review    <chr> "With all this stuff going down at the moment with MJ …
```

### epubr

The **epubr** package allows for extraction of metadata and textual
content of epub files.

``` r
install.packages("epubr")
library(epubr)
```

Further information and examples can be found
[here](https://github.com/ropensci/epubr).

## Github packages

### sacred

The **sacred** package includes 9 tidy data sets: `apocrypha`,
`book_of_mormon`, `doctrine_and_covenants`, `greek_new_testament`,
`king_james_version`, `pearl_of_great_price`, `tanach`, `vulgate` and
`septuagint` with column describing the position within each work.

``` r
#devtools::install_github("JohnCoene/sacred")
library(sacred)
```

``` r
dplyr::glimpse(apocrypha)
#> Observations: 5,725
#> Variables: 5
#> $ book.num <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
#> $ book     <chr> "es1", "es1", "es1", "es1", "es1", "es1", "es1", "es1",…
#> $ psalm    <chr> "11", "11", "11", "11", "11", "11", "11", "11", "11", "…
#> $ verse    <chr> "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11"…
#> $ text     <chr> "And Josias held the feast of the passover in Jerusalem…
```

Examples:

Still pending.

### harrypotter

The **harrypotter** package includes the text from all 7 main series
books.

``` r
#devtools::install_github("bradleyboehmke/harrypotter")
library(harrypotter)
```

the 7 books; `philosophers_stone`, `chamber_of_secrets`,
`prisoner_of_azkaban`, `goblet_of_fire`, `order_of_the_phoenix`,
`half_blood_prince` and `deathly_hallows` are formatted as character
vectors with a chapter for each string.

``` r
dplyr::glimpse(harrypotter::chamber_of_secrets)
#>  chr [1:19] "THE WORST BIRTHDAY　　Not for the first time, an argument had broken out over breakfast at number four, Privet "| __truncated__ ...
```

Examples:

-   [Harry Plotter: Celebrating the 20 year anniversary with tidytext
    and the tidyverse in
    R](https://paulvanderlaken.com/2017/08/03/harry-plotter-celebrating-the-20-year-anniversary-with-tidytext-the-tidyverse-and-r/)
-   [Harry Plotter: Part 2 – Hogwarts Houses and their
    Stereotypes](https://paulvanderlaken.com/2017/08/22/harry-plotter-part-2-hogwarts-houses-and-their-stereotypes/)

### hgwellsr

The **hgwellsr** package provides access to the full texts of six novels
by H. G. Wells.

``` r
#devtools::install_github("erikhoward/hgwellsr")
library(hgwellsr)
```

-   Ann Veronica (1909): `annveronica`.
-   The History of Mr Polly (1910): `mrpolly`.
-   The Invisible Man (1897): `invisibleman`.
-   The Island of Doctor Moreau (1896): `doctormoreau`.
-   The Time Machine (1895):`timemachine`.
-   The War of the Worlds (1898): `waroftheworlds`.

``` r
head(annveronica, 10)
#>  [1] "CHAPTER THE FIRST"                                                     
#>  [2] ""                                                                      
#>  [3] "ANN VERONICA TALKS TO HER FATHER"                                      
#>  [4] ""                                                                      
#>  [5] ""                                                                      
#>  [6] "Part 1"                                                                
#>  [7] ""                                                                      
#>  [8] ""                                                                      
#>  [9] "One Wednesday afternoon in late September, Ann Veronica Stanley came"  
#> [10] "down from London in a state of solemn excitement and quite resolved to"
```

### jeeves

The **jeeves** package provides access to the full texts of 38 works by
P.G. Wodehouse.

``` r
#devtools::install_github("aniruhil/jeeves")
library(jeeves)
```

``` r
glimpse(adamselindistress)
#> Rows: 10,291
#> Columns: 3
#> $ gutenberg_id <int> 2233, 2233, 2233, 2233, 2233, 2233, 2233, 2233, 2233, 223…
#> $ text         <chr> "[Transcriber's Note for edition 11: in para. 4 of Chapte…
#> $ title        <chr> "A Damsel in Distress", "A Damsel in Distress", "A Damsel…
```

### koanr

The **koanr** package includes text from several of the more important
Zen koan texts.

``` r
#devtools::install_github("malcolmbarrett/koanr")
library(koanr)
```

The texts in this package include The Gateless Gate (`gateless_gate`),
The Blue Cliff Record (`blue_cliff_record`), The Record of the
Transmission of the Light(`record_of_light`), and The Book of
Equanimity(`book_of_equanimity`).

``` r
dplyr::glimpse(gateless_gate)
#> Rows: 192
#> Columns: 4
#> $ collection <chr> "The Gateless Gate", "The Gateless Gate", "The Gateless Gat…
#> $ case       <int> 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 5, 5, 5, 5,…
#> $ type       <chr> "title", "main_case", "commentary", "capping_verse", "title…
#> $ text       <chr> "Joshu's Dog", "A monk asked Joshu, \"Has the dog the Buddh…
```

### rperseus

The goal of rperseus is to furnish classicists, textual critics, and R
enthusiasts with texts from the Classical World. While the English
translations of most texts are available through `gutenbergr`, rperseus
returns these works in their original language–Greek, Latin, and Hebrew.

``` r
#devtools::install_github("ropensci/rperseus")
library(rperseus)
aeneid_latin <- perseus_catalog %>% 
  filter(group_name == "Virgil",
         label == "Aeneid",
         language == "lat") %>% 
  pull(urn) %>% 
  get_perseus_text()
head(aeneid_latin)
#> # A tibble: 6 × 7
#>   text           urn        group_name label description        language section
#>   <chr>          <chr>      <chr>      <chr> <chr>              <chr>      <int>
#> 1 Arma virumque… urn:cts:l… Virgil     Aene… "Perseus:bib:oclc… lat            1
#> 2 Conticuere om… urn:cts:l… Virgil     Aene… "Perseus:bib:oclc… lat            2
#> 3 Postquam res … urn:cts:l… Virgil     Aene… "Perseus:bib:oclc… lat            3
#> 4 At regina gra… urn:cts:l… Virgil     Aene… "Perseus:bib:oclc… lat            4
#> 5 Interea mediu… urn:cts:l… Virgil     Aene… "Perseus:bib:oclc… lat            5
#> 6 Sic fatur lac… urn:cts:l… Virgil     Aene… "Perseus:bib:oclc… lat            6
```

See [the vignette for more
examples.](https://ropensci.github.io/rperseus/articles/rperseus-vignette.html)

### subtools

The **subtools** package doesn’t include any textual data, but allows
you to read subtitle files.

``` r
#devtools::install_github("fkeck/subtools")
library(subtools)
```

the use of this function can be found in the examples.

Examples:

-   [Movies and series subtitles in R with
    subtools](http://www.pieceofk.fr/?p=437)
-   [A tidy text analysis of Rick and
    Morty](http://tamaszilagyi.com/blog/a-tidy-text-analysis-of-rick-and-morty/)
-   [You beautiful, naïve, sophisticated newborn
    series](https://masalmon.eu/2017/11/05/newborn-serie/)

## Wild data

This sections includes public data sets and how to import them into R
ready for analysis. It is generally advised to save the resulting data
such that you don’t re-download the data excessively.

[Movie Review
Data](http://www.cs.cornell.edu/people/pabo/movie-review-data/)

This website include a handful of different movie review data sets.
Below is the code chuck necessary to load in the data sets.

### polarity dataset v2.0

``` r
library(tidyverse)
library(fs)

filepath <- file_temp() %>%
  path_ext_set("tar.gz")

download.file("http://www.cs.cornell.edu/people/pabo/movie-review-data/review_polarity.tar.gz", filepath)

file_names <- untar(filepath, list = TRUE)
file_names <- file_names[!str_detect(file_names, "README")]

untar(filepath, files = file_names)

data <- map_df(file_names, 
               ~ tibble(text = read_lines(.x),
                        polarity = str_detect(.x, "pos"),
                        cv_tag = str_extract(.x, "(?<=cv)\\d{3}"),
                        html_tag = str_extract(.x, "(?<=cv\\d{3}_)\\d*")))

glimpse(data)
#> Rows: 64,720
#> Columns: 4
#> $ text     <chr> "plot : two teen couples go to a church party , drink and the…
#> $ polarity <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE…
#> $ cv_tag   <chr> "000", "000", "000", "000", "000", "000", "000", "000", "000"…
#> $ html_tag <chr> "29416", "29416", "29416", "29416", "29416", "29416", "29416"…
```

### sentence polarity dataset v1.0

``` r
library(tidyverse)
library(fs)

filepath <- file_temp() %>%
  path_ext_set("tar.gz")

download.file("http://www.cs.cornell.edu/people/pabo/movie-review-data/rt-polaritydata.tar.gz", filepath)

file_names <- untar(filepath, list = TRUE)
file_names <- file_names[!str_detect(file_names, "README")]

untar(filepath, files = file_names)

data <- map_df(file_names, 
               ~ tibble(text = read_lines(.x),
                        polarity = str_detect(.x, "pos")))

glimpse(data)
#> Rows: 10,662
#> Columns: 2
#> $ text     <chr> "simplistic , silly and tedious . ", "it's so laddish and juv…
#> $ polarity <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE…
```

### scale dataset v1.0

``` r
library(tidyverse)
library(fs)

filepath <- file_temp() %>%
  path_ext_set("tar.gz")

download.file("http://www.cs.cornell.edu/people/pabo/movie-review-data/scale_data.tar.gz", filepath)

file_names <- untar(filepath, list = TRUE)
file_names <- file_names[!str_detect(file_names, "README")]

untar(filepath, files = file_names)

subjs <- str_subset(file_names, "subj")
ids <- str_subset(file_names, "id")
ratings <- str_subset(file_names, "rating")
names <- str_extract(ratings, "(?<=rating.).*") %>%
  str_replace("\\+", " ")

data <- map_df(seq_len(length(names)), 
               ~ tibble(text = read_lines(subjs[.x]),
                        id = read_lines(ids[.x]),
                        rating = read_lines(ratings[.x]),
                        name = names[.x]))

glimpse(data)
#> Rows: 5,006
#> Columns: 4
#> $ text   <chr> "in my opinion , a movie reviewer's most important task is to o…
#> $ id     <chr> "29420", "17219", "18406", "18648", "20021", "20454", "20473", …
#> $ rating <chr> "0.1", "0.2", "0.2", "0.2", "0.2", "0.2", "0.2", "0.2", "0.2", …
#> $ name   <chr> "Dennis Schwartz", "Dennis Schwartz", "Dennis Schwartz", "Denni…
```

### subjectivity dataset v1.0

``` r
library(tidyverse)
library(fs)

filepath <- file_temp() %>%
  path_ext_set("tar.gz")

download.file("http://www.cs.cornell.edu/people/pabo/movie-review-data/rotten_imdb.tar.gz", filepath)

file_names <- untar(filepath, list = TRUE)
file_names <- file_names[!str_detect(file_names, "README")]

untar(filepath, files = file_names)

data <- map_df(file_names, 
               ~ tibble(text = read_lines(.x),
                        label = if_else(str_detect(.x, "quote"), 
                                        "subjective", 
                                        "objective")))

glimpse(data)
#> Rows: 10,000
#> Columns: 2
#> $ text  <chr> "smart and alert , thirteen conversations about one thing is a s…
#> $ label <chr> "subjective", "subjective", "subjective", "subjective", "subject…
```

### SouthParkData

the following github repository
[BobAdamsEE/SouthParkData](https://github.com/BobAdamsEE/SouthParkData)
includes the script of the first 19 seasons of South Park. The following
code snippet lets you download them all at once.

``` r
url_base <- "https://raw.githubusercontent.com/BobAdamsEE/SouthParkData/master/by-season"
urls <- paste0(url_base, "/Season-", 1:19, ".csv")

data <- map_df(urls, ~ read_csv(.x))

glimpse(data)
#> Rows: 73,139
#> Columns: 4
#> $ Season    <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
#> $ Episode   <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
#> $ Character <chr> "Boys", "Kyle", "Ike", "Kyle", "Cartman", "Kyle", "Stan", "K…
#> $ Line      <chr> "School day, school day, teacher's golden ru...\n", "Ah, dam…
```

Examples:

-   <https://www.kaylinpavlik.com/text-mining-south-park/>

### Saudi Newspapers Corpus

The following Github repository
[inparallel/SaudiNewsNet](https://github.com/inparallel/SaudiNewsNet)
includes data and text from 31030 Arabic newspaper articles along with
metadata, extracted from various online Saudi newspapers.

``` r
library(rio)
library(glue)
library(fs)
library(purrr)

dates <- c("2015-07-21", "2015-07-22", "2015-07-23", "2015-07-24", "2015-07-25",
           "2015-07-26", "2015-07-27", "2015-07-31", "2015-08-01", "2015-08-02",
           "2015-08-03", "2015-08-04", "2015-08-06", "2015-08-07", "2015-08-08",
           "2015-08-09", "2015-08-10", "2015-08-11")

tmp_path <- path_temp()

urls <- glue("https://raw.githubusercontent.com/inparallel/SaudiNewsNet/master/dataset/{dates}.zip")
paths <- path(tmp_path, dates, ext = "zip")

data <- map2_dfr(urls, paths, ~ {
  download.file(.x, .y)
  import_list(.y)[[1]]
})

glimpse(data)
#> Rows: 31,030
#> Columns: 6
#> $ source         <chr> "aawsat", "aawsat", "aawsat", "aawsat", "aawsat", "aaws…
#> $ url            <chr> "http://aawsat.com/home/article/410826/بريطانيا-أربعة-م…
#> $ date_extracted <chr> "2015-07-21 02:51:32", "2015-07-21 02:51:33", "2015-07-…
#> $ title          <chr> "بريطانيا: أربعة محاور لاستراتيجية جديدة تتصدى للتطرف ع…
#> $ author         <chr> "لندن: رنيم حنوش", "لندن: «الشرق الأوسط أونلاين»", "لند…
#> $ content        <chr> "حدد رئيس الوزراء البريطاني ديفيد كاميرون، اليوم (الاثن…
```
