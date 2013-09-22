## bbc_radio_tracklisting_downloader.py
A Python script that downloads radio tracklistings from BBC's website and outputs to a text file.
Licensed under GPL v3 (see COPYING).
***

**This branch tries to add a lyrics tag containing the tracklisting to the relevant audio file that has been downloaded with `get_iplayer`.**

Uses code from [beets](https://github.com/sampsyo/beets) by Adrian Sampson.

### Usage examples
Run `bbc_tracklist.py` from the command line. The required argument is the BBC programme id, the 8 characters that are found at the end of iPlayer URLs such as:`http://www.bbc.co.uk/iplayer/episode/<programme id>/<programme name>` or programme information URLs such as: `http://www.bbc.co.uk/programmes/<programme id>`. 

Optional arguments are `<directory>` and `<filename prefix>`. If either of these are omitted, output will be to the current path.

The script generates a string of the format:

`Programme title`    
`Programme broadcast date`    
  
`Artist`  
`Title`  
`Record label`  
`***`

This is used to try to tag an audio file in `<directory>` and with a filename **prefix** `<filename prefix>`, that is the name of the file without e.g. the .MP3 extension. First, it tries to tag an M4A file, then an MP3. If it fails to find (or write to) an appropriate audio file, it falls back to creating a text file.
***
### get_iplayer usage
If downloading a radio programme with [get_iplayer](http://www.infradead.org/get_iplayer/html/get_iplayer.html), adding an argument of the form `--command "/home/get_iplayer/bbc_tracklist.py <pid> <dir> <fileprefix>"` should result in a text file containing the tracklisting in the same directory as your downloaded audio file. (Change `/home/get_iplayer` to point to wherever the script is located.)
***
### Dependencies and issues
* Tagging of M4A files seems to break playback in [Rockbox](http://www.rockbox.org), though they appear to play OK on e.g. Rhythmbox, foobar2000. MP3s seem unaffected.
* Requires [BeautfulSoup]((http://www.crummy.com/software/BeautifulSoup/) and [mutagen](http://code.google.com/p/mutagen/); `pip install -r requirements.txt` should install everything you need.
* Tested on Python 2.7.3 on Windows (Windows 7 64-bit) and Linux (Raspbian). (I suspect it doesn't work with Python versions earlier than this due to improvements in Python's HTMLParser introduced in 2.7.3.)
* Tested with BeautifulSoup 4.1.3; later versions should be fine.
* po:short_synopsis sections not handled yet.
