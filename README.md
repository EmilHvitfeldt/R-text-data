
<!-- README.md is generated from README.Rmd. Please edit that file -->

# R-text-data

The goal of this repository is to act as a collection of textual data
set to be used for training and practice in text mining/NLP in R. This
repository will not be a guide on how to do text analysis/mining but
rather how to get a data set to get started with minimal hassle.

# Table of Contents

  - [Main page](#R-text-data)
  - [CRAN packages](#cran-packages)
      - [janeaustenr](#janeaustenr)
      - [proustr](#proustr)
      - [gutenbergr](#gutenbergr)
      - [text2vec](#text2vec)
      - [epubr](#epubr)
  - [Github packages](#github-packages)
      - [sacred](#sacred)
      - [hcandersenr](#hcandersenr)
      - [harrypotter](#harrypotter)
      - [koanr](#koanr)
      - [rperseus](#rperseus)
      - [subtools](#subtools)
  - [Wild data](#wild-data)
      - Cornell data
          - [polarity dataset v2.0](#polarity-dataset-v20)
          - [sentence polarity dataset
            v1.0](#sentence-polarity-dataset-v10)
          - [scale dataset v1.0](#scale-dataset-v10)
          - [subjectivity dataset v1.0](#subjectivity-dataset-v10)
      - [SouthParkData](#southparkdata)

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

  - <https://juliasilge.com/blog/if-i-loved-nlp-less/>

### proustr

This **proustr** packages gives you access to tools designed to do
Natural Language Processing in French.

``` r
#install.packages("proustr")
library(proustr)
```

Furthermore it includes the following 7 books

  - Du côté de chez Swann (1913): `ducotedechezswann`.
  - À l’ombre des jeunes filles en fleurs (1919):
    `alombredesjeunesfillesenfleurs`.
  - Le Côté de Guermantes (1921): `lecotedeguermantes`.
  - Sodome et Gomorrhe (1922) : `sodomeetgomorrhe`.
  - La Prisonnière (1923) :`laprisonniere`.
  - Albertine disparue (1925, also know as : La Fugitive) :
    `albertinedisparue`.
  - Le Temps retrouvé (1927) : `letempretrouve`.

Which are all found in the `proust_books()` function.

``` r
dplyr::glimpse(proust_books())
#> Observations: 4,690
#> Variables: 4
#> $ text   <chr> "Longtemps, je me suis couché de bonne heure. Parfois, ...
#> $ book   <chr> "Du côté de chez Swann", "Du côté de chez Swann", "Du c...
#> $ volume <chr> "Première partie : Combray", "Première partie : Combray...
#> $ year   <dbl> 1913, 1913, 1913, 1913, 1913, 1913, 1913, 1913, 1913, 1...
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
#> # ... with 2 more variables: rights <chr>, has_text <lgl>
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
#>  7          768 1801.--I have just returned from a visit to my landlord--…
#>  8          768 neighbour that I shall be troubled with.  This is certain…
#>  9          768 country!  In all England, I do not believe that I could h…
#> 10          768 situation so completely removed from the stir of society.…
#> # ... with 12,075 more rows
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
#> $ id        <chr> "5814_8", "2381_9", "7759_3", "3630_4", "9495_8", "8...
#> $ sentiment <int> 1, 1, 0, 0, 1, 1, 0, 0, 0, 1, 0, 1, 1, 0, 0, 0, 0, 0...
#> $ review    <chr> "With all this stuff going down at the moment with M...
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
#> $ book.num <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,...
#> $ book     <chr> "es1", "es1", "es1", "es1", "es1", "es1", "es1", "es1...
#> $ psalm    <chr> "11", "11", "11", "11", "11", "11", "11", "11", "11",...
#> $ verse    <chr> "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "1...
#> $ text     <chr> "And Josias held the feast of the passover in Jerusal...
```

Examples:

Still pending.

### hcandersenr

The **hcandersenr** package includes many of H.C. Andersen’s fairy tales
in 5 difference languages.

``` r
#devtools::install_github("EmilHvitfeldt/hcandersenr")
library(hcandersenr)
```

The fairy tales are found in the following data frames `hcandersen_en`,
`hcandersen_da`, `hcandersen_de`, `hcandersen_es` and `hcandersen_fr`
for the English, Danish, German, Spanish and French versions
respectively. Please be advised that all fairy tales aren’t available in
all languages in this package.

``` r
dplyr::glimpse(hcandersen_en)
#> Observations: 27,859
#> Variables: 2
#> $ text <chr> "A soldier came marching along the high road: \"Left, rig...
#> $ book <chr> "The tinder-box", "The tinder-box", "The tinder-box", "Th...
```

All the fairy tales are collected in the following data.frame:

``` r
dplyr::glimpse(hca_fairytales)
#> Observations: 115,247
#> Variables: 3
#> $ text     <chr> "Der kom en soldat marcherende hen ad landevejen: én,...
#> $ book     <chr> "The tinder-box", "The tinder-box", "The tinder-box",...
#> $ language <chr> "Danish", "Danish", "Danish", "Danish", "Danish", "Da...
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

  - [Harry Plotter: Celebrating the 20 year anniversary with tidytext
    and the tidyverse in
    R](https://paulvanderlaken.com/2017/08/03/harry-plotter-celebrating-the-20-year-anniversary-with-tidytext-the-tidyverse-and-r/)
  - [Harry Plotter: Part 2 – Hogwarts Houses and their
    Stereotypes](https://paulvanderlaken.com/2017/08/22/harry-plotter-part-2-hogwarts-houses-and-their-stereotypes/)

## koanr

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
#> Observations: 192
#> Variables: 4
#> $ collection <chr> "The Gateless Gate", "The Gateless Gate", "The Gate...
#> $ case       <int> 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 5, ...
#> $ type       <chr> "title", "main_case", "commentary", "capping_verse"...
#> $ text       <chr> "Joshu's Dog", "A monk asked Joshu, \"Has the dog t...
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
#> # A tibble: 6 x 7
#>   text        urn       group_name label description      language section
#>   <chr>       <chr>     <chr>      <chr> <chr>            <chr>      <int>
#> 1 Arma virum… urn:cts:… Virgil     Aene… "Perseus:bib:oc… lat            1
#> 2 Conticuere… urn:cts:… Virgil     Aene… "Perseus:bib:oc… lat            2
#> 3 Postquam r… urn:cts:… Virgil     Aene… "Perseus:bib:oc… lat            3
#> 4 At regina … urn:cts:… Virgil     Aene… "Perseus:bib:oc… lat            4
#> 5 Interea me… urn:cts:… Virgil     Aene… "Perseus:bib:oc… lat            5
#> 6 Sic fatur … urn:cts:… Virgil     Aene… "Perseus:bib:oc… lat            6
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

  - [Movies and series subtitles in R with
    subtools](http://www.pieceofk.fr/?p=437)
  - [A tidy text analysis of Rick and
    Morty](http://tamaszilagyi.com/blog/a-tidy-text-analysis-of-rick-and-morty/)
  - [You beautiful, naïve, sophisticated newborn
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
#> Observations: 64,720
#> Variables: 4
#> $ text     <chr> "plot : two teen couples go to a church party , drink...
#> $ polarity <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALS...
#> $ cv_tag   <chr> "000", "000", "000", "000", "000", "000", "000", "000...
#> $ html_tag <chr> "29416", "29416", "29416", "29416", "29416", "29416",...
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
#> Observations: 10,662
#> Variables: 2
#> $ text     <chr> "simplistic , silly and tedious . ", "it's so laddish...
#> $ polarity <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALS...
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
#> Observations: 5,006
#> Variables: 4
#> $ text   <chr> "in my opinion , a movie reviewer's most important task...
#> $ id     <chr> "29420", "17219", "18406", "18648", "20021", "20454", "...
#> $ rating <chr> "0.1", "0.2", "0.2", "0.2", "0.2", "0.2", "0.2", "0.2",...
#> $ name   <chr> "Dennis Schwartz", "Dennis Schwartz", "Dennis Schwartz"...
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
#> Observations: 10,000
#> Variables: 2
#> $ text  <chr> "smart and alert , thirteen conversations about one thin...
#> $ label <chr> "subjective", "subjective", "subjective", "subjective", ...
```

### SouthParkData

the following github repository
[BobAdamsEE/SouthParkData](https://github.com/BobAdamsEE/SouthParkData)
includes the script of the first 19 seasons of South Park. The following
code snippet lets you download them all at
once.

``` r
url_base <- "https://raw.githubusercontent.com/BobAdamsEE/SouthParkData/master/by-season"
urls <- paste0(url_base, "/Season-", 1:19, ".csv")

data <- map_df(urls, ~ read_csv(.x))
```

Examples:

  - <https://www.kaylinpavlik.com/text-mining-south-park/>
