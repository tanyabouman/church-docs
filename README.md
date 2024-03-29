# Church Documents

**Warning**: if using a file manager and opening pdfs on your phone is too difficult,
please try apps instead:
- [Android Psalter app](https://play.google.com/store/apps/details?id=com.jrvermeer.psalter)
- [iOS Psalter app](https://apps.apple.com/us/app/the-psalter-1912/id1139689141)
- Psalmboek.nl apps: [Android](https://play.google.com/store/apps/details?id=nl.wimbokkers.psalmen) [iOS](https://apps.apple.com/us/app/psalmboek-nl/id594145882)

These are a few church-related documents that I keep on my phone.
I originally needed them because I had a Windows phone and no Psalter apps were
available, but I keep using them because I want the
[Grotenhuis transcriptions](https://digitalcollections.dordt.edu/grotenhuis_keyboard/342/)
on mobile.
The documents are all split into smaller pieces and then into separate folders because my
phone wasn't fast enough to deal with large pdfs or long lists of files.
I haven't checked whether my current phone can handle that.

## Contents

- `confessions-church-order`: [Doctrinal Standards, Liturgy, and Church Order](http://www.prca.org/component/jdownloads/finish/11/128?Itemid=0) from the PRCA website
- `new-psalter`: [the new Psalter](https://thepsalter.net/).  I'm not 100% sure whether these are the latest.
- `psalter`: original [1912 Psalter](http://books.google.com/books?id=Wm0Cl8tI8KgC) from Google books, interspersed with [Grotenhuis transcriptions](https://digitalcollections.dordt.edu/grotenhuis_keyboard/342/) from Dordt University, [new scans](https://github.com/jrvermeer/PsalterFiles/tree/master/1912/Score) from the Android app when there are changes  Psalters 414-434 are from the Android app, so many of them are missing verses.  Psalters 435-450 are [Genevan melodies]() from the Psalmboek.nl Android app.  It's just a melody line without words, and the rhythms are often different.
- `glory-to-god.pdf`: [Ere zij God](https://media.ldscdn.org/pdf/music/hymns-dutch/2003-01-1430-praise-to-god-nld.pdf) from a Mormon website

TODO:
- make scans for ones that need substitutes
- get new psalter updates
- figure out Glory to God in English

## Technical Details

Scripts and stuff:

```
pdftk psalter.pdf cat 29-30 output pages29-30.pdf
```

Download Android images and convert to pdf.
```
for f in {414..434}; do wget "https://raw.githubusercontent.com/jrvermeer/PsalterFiles/master/1912/Score/_$f.webp"; done
for f in *.webp ; do convert "$f" -page letter -gravity northwest "${f%.webp}.pdf"; done
for f in *.webp ; do convert "$f" -page letter "${f%.webp}.pdf"; done
```
