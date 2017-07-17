---
published: false
---
## [lucasfan2004](http://www.adventuregamestudio.co.uk/site/games/game/401/)

To make it work on linux:
- require wine
- download/unzip archive
- create config manually [acsetup.cfg](https://appdb.winehq.org/objectManager.php?sClass=version&iId=9721)
```
[sound]
digiid=-1
midiid=-1
digiwin=1096302880
midiwin=-1
digiindx=0
midiindx=0
digiwinindx=0
midiwinindx=0
[misc]
gamecolordepth=16
defaultres=1
screenres=1
letterbox=0
windowed=0
refresh=0
[language]
translation=English
```

- install timidity + freepats (for backgroudn music)
- run timitidy in background
```
timidity -iA -B2,8 -Os -EFreverb=0&
```

- launch game (can be configured through autexe.run)

- enjoy!

## [solution](http://gamesolutions.efzeven.nl/maniac-mansion-deluxe-walkthrough-lucasfan2004/)
