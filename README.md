# JapScanDownloader

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/acf59998d8a743188d5f7ef058010ffa)](https://www.codacy.com/manual/Harkame/JapScanDownloader?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=Harkame/JapScanDownloader&amp;utm_campaign=Badge_Grade)
[![Maintainability](https://api.codeclimate.com/v1/badges/eb654455df609c6fd1a2/maintainability)](https://codeclimate.com/github/Harkame/JapScanDownloader/maintainability)
[![Build Status](https://travis-ci.org/Harkame/JapScanDownloader.svg?branch=master)](https://travis-ci.org/Harkame/JapScanDownloader)
[![codecov](https://codecov.io/gh/Harkame/JapScanDownloader/branch/master/graph/badge.svg)](https://codecov.io/gh/Harkame/JapScanDownloader)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

## Installation - Please keep dependencies updated

``` bash

pip install -r requirements.txt -U

```

### Dependencies

  -   [Beautiful Soup 4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
  -   [PyYAML](https://github.com/yaml/pyyaml)
  -   [lxml](https://github.com/lxml/lxml.git)
  -   [tqdm](https://github.com/tqdm/tqdm)
  -   [Pillow](https://github.com/python-pillow/Pillow.git)
  -   [cloudscraper](https://github.com/VeNoMouS/cloudscraper)

## Usage

### Run

``` bash
python japscandownloader/main.py
```

### Options

``` bash
usage: main.py [-h] [-c CONFIG_FILE] [-d DESTINATION_PATH] [-f FORMAT] [-v]
               [-r] [-k] [-u]

optional arguments:
  -h, --help            show this help message and exit
  -c CONFIG_FILE, --config_file CONFIG_FILE
                        Set config file Example : python
                        japscandownloader/main.py -c /home/myconfigfile.yml
  -d DESTINATION_PATH, --destination_path DESTINATION_PATH
                        Set destination path of downloaded mangas Example :
                        python japscandownloader/main.py -d /home/mymangas/
  -f FORMAT, --format FORMAT
                        Set format of downloaded mangas Example : python
                        japscandownloader/main.py -f cbz|pdf|jpg|png
  -v, --verbose         Active verbose mode, support different level Example :
                        python japscandownloader/main.py -vv
  -r, --reverse         Reverse chapters download order (Default : Last to
                        first) Example : python japscandownloader/main.py -r
  -k, --keep            Keep downloaded images (when format is pdf/cbz)
                        (default : false) Example : python
                        japscandownloader/main.py -k
  -u, --unscramble      Force unscrambling Example : python
                        japscandownloader/main.py -u
```

### How it work

This program use an config file (default : ./config.yml)

This file contains list of mangas to download, destination path, etc.

#### Example of config file

``` yaml
mangas:
  - chapter :
      url:
        https://www.japscan.co/lecture-en-ligne/one-piece/965/

  - url :
      https://www.japscan.co/manga/oggy-et-les-cafards/

  - chapters:
      url:
        https://www.japscan.co/lecture-en-ligne/black-clover/
      chapter_min:
        158
      chapter_max:
        161

destination_path:
  ./mangas/

manga_format:
  jpg
```

### Download an manga

Add an entry to attribute mangas

``` yml
mangas:
  - url: #complete manga
      https://www.japscan.to/manga/uq-holder/

  - chapter: #specific chapter
      https://www.japscan.to/lecture-en-ligne/shingeki-no-kyojin/60/

  - chapters: #multiple chapters
      url:
        https://www.japscan.to/lecture-en-ligne/black-clover/
      chapter_min: #included
        158
      chapter_max: #included
        197
```

### Change downloads destination

Replace destination_path value by desired path

#### Linux

``` yml
   destination_path:
      /home/harkame/mangas
```

#### Windows

 ``` yml

   destination_path:
      F:\data\mangas
```

### Change Manga format

Replace manga_format value by desired format

Supported format

-   jpg/png (default) : Just download image file
-   pdf : Create PDF file
-   cbz : Create CBZ archive

``` yml

   mangaFormat:
      jpg
```

## TODO
-   More tests
-   Chapters folders name (not only number)
-   Don’t download already downloaded manga/chapter/page
-   Better scrambling detection
-   Fix : Download test not working on travis

## Tests

 ``` bash

     pip install tox

     tox
```
