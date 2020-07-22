# Google Keyword Planner

This repository contains materials reproduce the findings featured in our story, "[Google Ad Portal Equated 'Black Girls' With Porn](https://themarkup.org/google-the-giant/2020/07/23/google-advertising-keywords-black-girls)" from our series, [Google the Giant](https://themarkup.org/series/google-the-giant).

Screenshots and figures from our story can be found in the `data` folder.

Jupyter notebooks used for data preprocessing and analysis are avialble in the `notebooks` folder.

💡 Disclaimer: This repository contains code and data with explicit and graphically sexual language.

## Installation
`pip install -r requirements.txt`

## Data
Where the raw inputs and intermediaries are stored.

```
data/
├── input
│   ├── browser
│   ├── raw-exports
│   └── screenshots
├── intermediary
│   ├── all-keywords.csv
│   ├── keywords-labelled-as-adult.json
│   ├── preprocessed
│   ├── websites-from-search.csv
│   └── websites-we-found-to-be-pornographic.csv
└── output
    ├── volume-of-adult-rec-keywords.csv
    └── volume-of-adult-rec-keywords.png
```
We have raw exports from Google Keyword Planner in `data/input/raw-exports`.<br>
The same input is exported with and without the "exclude Adult ideas" filters.<br>
The only column we use is the recommended `Keyword`s column.<br>
Collected July 8-12, 2020. 

You can view screenshots from Keyword Planner in `data/input/screenshots.`<br>
We have two screenshots for a search for "Black girls" with- and without the adult filters.

We preprocess and merge these files in `data/intermediary/preprocessed`. <br> 
Here we add three boolean columns: <br>
`Google_Adult` - `True` if Google filtered out the keyword when you "exclude adult ideas".<br>
`SERP_Adult` - `True` if the recommended keyword's corresponding Google search is majority self-described pornographic sites.<br>
`All_Adult` - `True` if either of the two previously mentioned bolumns is `True`.

We have the source code (HTML) of Google search results page (SERP) for all the 1.9K recommended keywords in `data/input/browser`

We have the 200 most-shared web domains (from the SERPs above) in `data/intermediary/websites-labelled-as-pornographic.csv`.<br> 
We determine which of these sites self identify as pornographic by looking for "porn" in the search listings for each website. We found 132 of these websites to be pornographic.

We have aggregated tables and figures featured in our story in `data/output`. The table `volume-of-adult-rec-keywords.csv` contains both counts and percentages of recommended keywords that Google identifies as "adult", which keywords have majority self-described pornographic sites in their search results, and neither adult or pornographic.

## Notebooks
If you want to reroduce our results, the notebooks should be run sequentially.

### 0-search-analysis.ipynb
Gets the top-shared domains from the 1.9K keywords recommended by Keyword Manager. Determines how many recommended keywords' search results contain links to self-identified pornographic sites

Links: [GitHub](https://github.com/the-markup/investigation-google-keyword-planner/blob/master/notebooks/0-search-analysis.ipynb) | [nbviewer](https://nbviewer.jupyter.org/github/the-markup/investigation-google-keyword-planner/blob/master/notebooks/0-search-analysis.ipynb)

### 1-analysis.ipynb
For each of our eight inputs, we get the count and percentage of recommended keywords which Google claims are "[Adult](https://support.google.com/adspolicy/answer/6023699?hl=en)", and which keywords we found to be pornographic. This is also where the figure featured in our story is produced. 

Links: [GitHub](https://github.com/the-markup/investigation-google-keyword-planner/blob/master/notebooks/1-analysis.ipynb) | [nbviewer](https://github.com/the-markup/investigation-google-keyword-planner/blob/master/notebooks/1-analysis.ipynb)

## Licensing
Copyright 2020, The Markup News Inc.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.