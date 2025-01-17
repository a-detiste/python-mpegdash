
# python-mpegdash

MPEG-DASH MPD (Media Presentation Description) Parser compatible with Python 3+.

[![Build Status](https://img.shields.io/github/workflow/status/sangwonl/python-mpegdash/Build%20Status?label=Python%202.7%2B%20builds)](https://github.com/sangwonl/python-mpegdash/actions?query=workflow%3A%22Build+Status%22)
[![License](https://img.shields.io/github/license/sangwonl/python-mpegdash?style=flat)](https://github.com/sangwonl/python-mpegdash/blob/master/LICENSE)

* * *

## Installation

```bash
$ pip install mpegdash
```

* * *

## Test

```bash
$ python -m unittest discover
```

* * *

## Usage

```py
from mpegdash.parser import MPEGDASHParser

# Parse from file path
mpd_path = './tests/mpd-samples/sample-001.mpd'
mpd = MPEGDASHParser.parse(mpd_path)

# Parse from url
mpd_url = 'http://yt-dash-mse-test.commondatastorage.googleapis.com/media/motion-20120802-manifest.mpd'
mpd = MPEGDASHParser.parse(mpd_url)

# Parse from string
mpd_string = '''
<MPD xmlns="urn:mpeg:DASH:schema:MPD:2011" mediaPresentationDuration="PT0H1M52.43S" minBufferTime="PT1.5S"
profiles="urn:mpeg:dash:profile:isoff-on-demand:2011" type="static">
  <Period duration="PT0H1M52.43S" start="PT0S">
    <AdaptationSet>
      <ContentComponent contentType="video" id="1" />
      <Representation bandwidth="4190760" codecs="avc1.640028" height="1080" id="1" mimeType="video/mp4" width="1920">
        <BaseURL>motion-20120802-89.mp4</BaseURL>
        <SegmentBase indexRange="674-981">
          <Initialization range="0-673" />
        </SegmentBase>
      </Representation>
    </AdaptationSet>
  </Period>
</MPD>
'''
mpd = MPEGDASHParser.parse(mpd_string)

# Write to xml file
MPEGDASHParser.write(mpd, './tests/mpd-samples/output.mpd')
```

* * *

## License

This project is released under the MIT license.
Please read and agree to the license before use, it can be found in the [LICENSE](LICENSE) file.
