<h1 align="center">
  <br>
  <a href="https://github.com/elmoiv/redvid"><img src="https://github.com/elmoiv/redvid/blob/master/assets/favicon.png?raw=true" alt="Redvid icon" width="100px"></a>
  <br>
  Redvid
  <br>
</h1>
<h4 align="center">Smart Downloader for Reddit Hosted Videos</h4>

<p align=center>
  <a target="_blank" href="https://travis-ci.org/elmoiv/redvid" title="Build Status">
    <img src="https://api.travis-ci.org/elmoiv/redvid.svg?branch=master">
  </a>
  <a target="_blank" href="https://pypi.org/project/redvid/" title="Python Version">
    <img src="https://img.shields.io/badge/python-3.x-brightgreen.svg">
  </a>
  <a target="_blank" href="https://github.com/elmoiv/redvid/releases" title="Current Version">
    <img src="https://img.shields.io/github/v/release/elmoiv/redvid.svg">
  </a>
  <a target="_blank" href="LICENSE" title="License: MIT">
    <img src="https://img.shields.io/github/license/elmoiv/redvid">
  </a>
</p>

<h1 align="center">
  <br>
  Now available for Android*
  <br>
</h1>
<p align="center"><a href="https://play.google.com/store/apps/details?id=com.elmoiv.redvid"><img height="80px" src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Google_Play_Store_badge_EN.svg/1200px-Google_Play_Store_badge_EN.svg.png"></a></p>

## Features
* Download local hosted videos with audio.
* Requires only `requests` and `FFmpeg`.
* Ability to decide quality.
* Bypass bot detection.

## Installation
`redvid` requires Python 3.

Use `pip` to install the package from PyPI:

```bash
pip install redvid
```

Or, install the latest version of the package from GitHub:

```bash
pip install git+https://github.com/elmoiv/redvid.git
```

## Usage
Using *redvid* to download a video:
  - via terminal (using [`credvid.py`](https://github.com/elmoiv/redvid/blob/master/credvid.py)):
```console
> python credvid.py --help

usage: credvid.py [-h] -u URL [-p PATH] [-o] [-mxq] [-mnq] [-mxd MAXDURATION]
                  [-mxs MAXSIZE] [-am] [-px PROXIES]

Argument parser for redvid module

required arguments:
  -u URL, --url URL     Post URL for Reddit hosted video

optional arguments:
  -p PATH, --path PATH  Custom path for downloaded videos
  -o, --overwrite       Overwrite existing videos and ignore exception
  -mxq, --maxquality    Auto select maximum quality
  -mnq, --minquality    Auto select minimum quality
  -mxd MAXDURATION, --maxduration MAXDURATION
                        Ignore videos that exceed this duration (in seconds)
  -mxs MAXSIZE, --maxsize MAXSIZE
                        Ignore videos that exceed this size (in bytes)
  -am, --automax        Automatically download video with maximum size (Helps
                        for old reddit videos with unknown qualities)
  -px PROXIES, --proxies PROXIES
                        Download videos through proxies for blocked regions
```
  - via scripts:

```python
from redvid import Downloader

reddit = Downloader(max_q=True)
reddit.url = 'https://v.redd.it/c8oic7ppc2751'
reddit.download()
```
*or*
```python
__import__('redvid').Downloader(url='https://v.redd.it/c8oic7ppc2751', max_q=True).download()
```

## Installing FFmpeg
### Windows: 

https://m.wikihow.com/Install-FFmpeg-on-Windows

(*You may need to restart your pc after applying these steps*)

### Linux: 

`sudo apt install ffmpeg`

### Mac OS:

* install [Homebrew](https://brew.sh/):

  `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
  
* Then:

  `$ brew install ffmpeg`

## Tests
Here are a few sample tests:

  * [Video only](https://github.com/elmoiv/redvid/tree/master/tests/test1.py)
  * [Video with audio](https://github.com/elmoiv/redvid/tree/master/tests/test2.py)
  * [Get best quality according to given size (Automated)](https://github.com/elmoiv/redvid/tree/master/tests/test12.py)
  * [Choose PATH](https://github.com/elmoiv/redvid/tree/master/tests/test3.py)
  * [Auto-detect maximum quality](https://github.com/elmoiv/redvid/tree/master/tests/test4.py)
  * [Auto-detect minimum quality](https://github.com/elmoiv/redvid/tree/master/tests/test5.py)
  * [Skip file check and overwrite](https://github.com/elmoiv/redvid/tree/master/tests/test6.py)
  * [Silent download (No logging)](https://github.com/elmoiv/redvid/tree/master/tests/test7.py)
  * [Set maximum video size](https://github.com/elmoiv/redvid/tree/master/tests/test8.py)
    * [Set maximum video size (different technique)](https://github.com/elmoiv/redvid/tree/master/tests/test9.py)
  * [Set maximum video duration](https://github.com/elmoiv/redvid/tree/master/tests/test10.py)
    * [Set maximum video duration (different technique)](https://github.com/elmoiv/redvid/tree/master/tests/test11.py)
 
## Changelog
### v1.1.3:
  * [#20](https://github.com/elmoiv/redvid/issues/20) Added a feature to create a folder in case it does not exist.
### v1.1.2:
  * [#18](https://github.com/elmoiv/redvid/issues/18) Fixed bug when handling path that caused recursive directories.
### v1.1.1:
  * [#15](https://github.com/elmoiv/redvid/issues/15) Fixed bug when fetching reddit videos with expiry date.
### v1.1.0:
  * [#11](https://github.com/elmoiv/redvid/issues/11) redvid can now decide best quality according to given size.
  * Added support for old reddit videos.
  * Fixed bug where video qualities list can't be parsed.
### v1.0.9:
  * [#8](https://github.com/elmoiv/redvid/issues/8) Added the ability to disable logging.
  * Maximum video size can be set.
  * [#9](https://github.com/elmoiv/redvid/issues/9) Maximum video duration can be set.
### v1.0.8:
  * [#7](https://github.com/elmoiv/redvid/issues/7) Fixed a bug with quality fetching.
### v1.0.7:
  * `download()` will return file path again.
### v1.0.6:
  * [#5](https://github.com/elmoiv/redvid/issues/5) Can now download urls with **v.reddit.it** fromat.
  * [#4](https://github.com/elmoiv/redvid/issues/4) PATH can be choosed instead of current dir.
  * [#3](https://github.com/elmoiv/redvid/issues/3) Max/Min quality can be automatically set to skip quality query.
  * Added ffmpeg encoding to videos with no sound to be uploadable on some platforms.
  * Adjusted printed text and progress bars.

## Stargazers over time
[![Stargazers over time](https://starchart.cc/elmoiv/redvid.svg)](https://starchart.cc/elmoiv/redvid)

## Contributing
Please contribute! If you want to fix a bug, suggest improvements, or add new features to the project, just [open an issue](https://github.com/elmoiv/redvid/issues) or send me a pull request.

**Android version of Redvid is not open-source.*
