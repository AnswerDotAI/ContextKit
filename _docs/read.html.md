# Read


<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

## Goals

## Imports

## Defining read\_ functions

### URL

------------------------------------------------------------------------

### read_url

>      read_url (url, heavy=False, sel=None, useJina=False, **kwargs)

*Reads a url and converts to markdown*

<table>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>url</td>
<td></td>
<td></td>
<td>URL to read</td>
</tr>
<tr class="even">
<td>heavy</td>
<td>bool</td>
<td>False</td>
<td>Use headless browser</td>
</tr>
<tr class="odd">
<td>sel</td>
<td>NoneType</td>
<td>None</td>
<td>Css selector to pull content from</td>
</tr>
<tr class="even">
<td>useJina</td>
<td>bool</td>
<td>False</td>
<td>Use Jina for the markdown conversion</td>
</tr>
<tr class="odd">
<td>kwargs</td>
<td>VAR_KEYWORD</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

``` python
# httpx.get 
read_url('https://docs.fastht.ml/')[:200]
```

    '  * Home\n  * Learn\n\n  * __\n  * __\n\n__\n\n  1. Get Started\n\n  * Get Started\n\n  * Tutorials __\n\n    * FastHTML By Example\n\n    * Web Devs Quickstart\n\n    * JS App Walkthrough\n\n    * Using Jupyter to write'

``` python
# headless browser w/ playwrightnb
read_url('https://docs.fastht.ml/', heavy=True)[:200]
```

    '  * Home\n  * Learn\n\n  * __\n  * __\n\n__\n\n  1. Get Started\n\n  * Get Started\n\n  * Tutorials __\n\n    * FastHTML By Example\n\n    * Web Devs Quickstart\n\n    * JS App Walkthrough\n\n    * Using Jupyter to write'

``` python
read_url('https://docs.fastht.ml/',useJina=True)[:200]
```

    'Title: FastHTML – fasthtml\n\nURL Source: https://docs.fastht.ml/\n\nMarkdown Content:\nWelcome to the official FastHTML documentation.\n\nFastHTML is a new next-generation web framework for fast, scalable w'

``` python
read_url('https://docs.fastht.ml/',sel='#quarto-margin-sidebar')
```

    '## On this page\n\n  * Installation\n  * Usage\n    * Getting help from AI\n  * Next Steps\n  * Other languages and related projects\n\n  * __Report an issue\n\n## Other Formats\n\n  *  __CommonMark\n\n'

``` python
read_url('https://docs.fastht.ml/',sel='#quarto-margin-sidebar',heavy=True)
```

    '## On this page\n\n  * Installation\n  * Usage\n    * Getting help from AI\n  * Next Steps\n  * Other languages and related projects\n\n  * __Report an issue\n\n## Other Formats\n\n  *  __CommonMark\n\n'

### Github

#### Gist

------------------------------------------------------------------------

### read_gist

>      read_gist (url)

*Returns raw gist content, or None*

``` python
sample_gist_url = "https://gist.github.com/algal/a490024ad088de1b857531c83abef0a0"
read_gist("https://gist.github.com/algal/a490024ad088de1b857531c83abef0a0")[:200]
```

    "#!/usr/bin/env python3\nimport os, os.path, sys, urllib.parse, base64, subprocess\n\ndef on_iterm2(): return 'ITERM_SESSION_ID' in os.environ or os.environ.get('LC_TERMINAL','') == 'iTerm2'\n\ndef on_macOS"

#### URL

#### File

------------------------------------------------------------------------

### read_gh_file

>      read_gh_file (url)

*Reads the contents of a file from its GitHub URL*

``` python
read_gh_file("https://github.com/AnswerDotAI/fasthtml/blob/main/README.md")[:200]
```

    '# FastHTML\n\n\n<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->\n\nWelcome to the official FastHTML documentation.\n\nFastHTML is a new next-generation web framework for fast, scalable web\napplic'

### Local Files

#### Files

------------------------------------------------------------------------

### read_file

>      read_file (path)

------------------------------------------------------------------------

### is_unicode

>      is_unicode (filepath, sample_size=1024)

``` python
assert is_unicode('_quarto.yml')
```

#### Directory

------------------------------------------------------------------------

### read_dir

>      read_dir (path, unicode_only=True, included_patterns=['*'],
>                excluded_patterns=['.git/**'], verbose=True, as_dict=False)

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 34%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th><strong>Type</strong></th>
<th><strong>Default</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>path</td>
<td></td>
<td></td>
<td>path to read</td>
</tr>
<tr class="even">
<td>unicode_only</td>
<td>bool</td>
<td>True</td>
<td>ignore non-unicode files</td>
</tr>
<tr class="odd">
<td>included_patterns</td>
<td>list</td>
<td>[’*’]</td>
<td>glob pattern of files to include</td>
</tr>
<tr class="even">
<td>excluded_patterns</td>
<td>list</td>
<td>[’.git/**’]</td>
<td>glob pattern of files to exclude</td>
</tr>
<tr class="odd">
<td>verbose</td>
<td>bool</td>
<td>True</td>
<td>log paths of files being read</td>
</tr>
<tr class="even">
<td>as_dict</td>
<td>bool</td>
<td>False</td>
<td>returns dict of {path,content}</td>
</tr>
<tr class="odd">
<td><strong>Returns</strong></td>
<td><strong>str | dict</strong></td>
<td></td>
<td><strong>returns string with contents of files read</strong></td>
</tr>
</tbody>
</table>

``` python
read_dir('.',verbose=False)[:200]
```

    '--- File: ./_quarto.yml ---\nproject:\n  type: website\n\nformat:\n  html:\n    theme: cosmo\n    css: styles.css\n    toc: true\n    keep-md: true\n  commonmark: default\n\nwebsite:\n  twitter-card: true\n  open-g'

### PDF reader

------------------------------------------------------------------------

### read_pdf

>      read_pdf (file_path:str)

``` python
read_pdf('./test_dir/test.pdf')
```

    ' \n  \n   \nThis is a test PDF document. \nIf you can read this, you have Adobe Acrobat Reader installed on your computer. '

### YT Transcript

------------------------------------------------------------------------

### read_yt_transcript

>      read_yt_transcript (yt_url)

``` python
yt_url = "https://youtu.be/MRtg6A1f2Ko?si=C7YZU6FFLdi6v9rk"
s = read_yt_transcript(yt_url)
s[:200]
```

    '- [Tim] A widescreen\niPod with touch controls, a revolutionary mobile phone, and a breakthrough internet\ncommunications device. (energetic music) (phone vibrating) Profound new intelligence capabiliti'

### Google Sheet

------------------------------------------------------------------------

### read_google_sheet

>      read_google_sheet (url)

``` python
read_google_sheet('https://docs.google.com/spreadsheets/d/17Q3LzRCyM4md28IBxzSSERpaafLgOH8MjH5r6UkyVz8/edit?gid=0#gid=0')
```

    b'Band Pull Around/Aparts\r\nShoulder Dislocations Straight\r\nShoulder Dislocations Side\r\nSuperman Dislocation\r\nScorpion Chest Stretch\r\nLatt Pulldown\r\nTwisty Shoulders\r\nRotator Cuff Pull\r\nWide bent over row'

### Google Doc

``` python
def gdoc_url_to_parseable(url):
    pattern = r'(https://docs\.google\.com/document/d/[^/]+)/edit'
    replacement = r'\1/export?format=html'
    return re.sub(pattern, replacement, url)
```

``` python
# Test the function
result = gdoc_url_to_parseable("https://docs.google.com/document/d/13g-IDyuJyk5wE60bOH1YhhFgW8rlh2LnSXccBS0CQd0/edit")
print(result)
```

    https://docs.google.com/document/d/13g-IDyuJyk5wE60bOH1YhhFgW8rlh2LnSXccBS0CQd0/export?format=html

------------------------------------------------------------------------

### read_gdoc

>      read_gdoc (url)

``` python
read_gdoc("https://docs.google.com/document/d/13g-IDyuJyk5wE60bOH1YhhFgW8rlh2LnSXccBS0CQd0/edit")[:200]
```

    '# Top heading\n\nHello this is a context reading test\n\n## Heading 2\n\nBolded text is here as well as italisized\n\n  * I have bullets\n  * Of things\n\n## Heading 3\n\nAnd ordered\n\n  1. Lists\n  2. Of\n  3. Thing'

## Next:

### GitHub Repo

How to use it:

``` python
d = read_gh_repo(ghurl,as_dict=True)
d.keys()
```

``` python
d[list(d.keys())[0]]
```

``` python
d = read_gh_repo(ghurl,as_dict=True,verbose=False)
d.keys()
```
