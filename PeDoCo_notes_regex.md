# Code and notes to making the PeDoCo language resourse

This .md file contains the iterative process with detailed notes and various regex bits of code to giving XML structure to the following publications provided as proofreading copies by the editors 

- S. Risberg, K. Salonen, *Appendix: Acta Pontificum Suecica. 2, Acta Poenitentiare: Auctoritate 
papae: the church province of Uppsala and the apostolic penitentiary 1410-1526*,
Diplomatarium Suecanum, Riksarkivet, Stockholm, 2008.

- P. D. Clarke, P. N. R. Zutshi, *Supplications from England and Wales in the registers of the
Apostolic Penitentiary, 1410-1503*. Volume I, 1410-1464, Canterbury and York Society, Vol.
CIII, Canterbury and York Society, Woodbridge, Suffolk, 2013.

- P. D. Clarke, P. N. R. Zutshi, *Supplications from England and Wales in the registers of the
Apostolic Penitentiary, 1410-1503*. Volume II, 1464-1492, Canterbury and York Society, Vol.
CIV, Canterbury and York Society, Woodbridge, Suffolk, 2014.

- P. D. Clarke, P. N. R. Zutshi, K. Wilson-Lee, *Supplications from England and Wales in the
registers of the Apostolic Penitentiary, 1410-1503*. Volume III, 1492-1503, Canterbury and
York Society, Vol. CV, Canterbury and York Society, Woodbridge, Suffolk, 2015.

And the text file that is the basis of the Latin text in the edition provided by the author

- Jørgensen, G. Saletnich, *Synder og pavemakt: botsbrev fra Den Norske Kirkeprovins
og Suderøyene til Pavestolen, 1438-1531*, Diplomatarium Poenitentiariae Norvegicum,
Misjonshøgskolens forlag, 2004.

The file is organized by edition, so that first the code and comments are on Swedish data, then Norway and lastly England and Wales. The citations from the editions are subject to copyright law and may not be reproduced without reference to their respective editors, as stated above per edition.

This file code is not meant as a publication, but as notes for improving transparancy of the conversion process.

# Notes for making sense of the Auctoritate file when opened in Word

General observations

## Auctoritate in a manageable format

### Initial checks on special characters and how the most important things are transferred

Open the pdf in Word: 
- line breaks doesn't work
- hyphens disappear - no, the hyphenation is different?!
  - direct: ~160 hyphens, copypaste: ~100 hyphens

Copypaste from Adobe Reader to Word: 
- line breaks are preserved
- page numbers and headers/footers become ordinary body text

Character searching:

- characters ``# { } $ ¤ £ \ § ½ @ % = ´ ` ^ ~ *`` not found
- `< [ ] ( / | &` are found

`<suppl/>`

and from the editing principles we read that:

`[ ]` *delenda* to be deleted  
`/` *nova codicis pagina* new page of a manuscript  
`< >` *supplenda* to be added  
`† †` *turbata* corrupt  
`+` *verbum vel verba* (*quae* the following word(s)  
*sequuntur*) add. added (in the manuscript)

 - 6: a reference number 1 in N1
 - ~22b: 1 and 2 in 'etc1' and 'etc2', also 161-162, 172, 180, 201 and morte1 164, 210 Stenus1...
6: (in the copypaste version 2022)
 - line numbers, folio numbers, in references pseudo small caps in Risberg's ISBERG.
Auctoritate's documents are partly copied in bundles in the office. E.g. 225-229 . How are they processed?
What about the hyphenation? Off?

Confusing passages within the text:
- 208: LunenSIS regens. - 'sis' is a capitalized font 11! just 'bigger'.
- 248: pape viti super - 'ti' is a smaller font 6.5! superscript
- 437b: at the end of 3o where 'o' is a smaller font 6.5! superscript

Reply from Kirsi Salonen:
- Lunensis - it's probably just an accidental use of the wrong font. It doesn't make any difference
- viti - when you look at the actual edition, you will notice that it is Pope Clement VI and the text has vi followed by ti as the superscript, i.e. vi-ti (= sexti).

How do I take into account that almost every document has some entry in the apparatus criticus? However, I think it is quite relevant to address the work done by Sara Risberg. Surely the manual work applies to each word or phrase individually? I think relevant to know what are the typical grammatical "challenges" in the penitentiary material. And what Sara has had to edit for a "better" Latin. 
And further, what has been that has not usually bothered to be copied into the register copies and has been completed by Sara. It takes a while, but I think it's worth the effort for later stages. There is variation between scribes on this and Sara deals with it in the introduction. However, formulas are regularly omitted in many documents.
And then again, on the other hand, is it relevant that footnotes contain references to canon law or biblical passages, for example? Or other editions? I think not, but I don't know. Do you have to do a Bible reference tag, etc.? Will be useful for genre/register analysis later?

I got help and guidance on italics from friend. Now we are wondering if html or xml would be a suitable format? `<>` is already used in Auctoratite, so it doesn't fit the format of the tag. This part still causes a problem and we have not got any further. Discussed *ANON supervisors*'s `#` suggestion. One possibility is to take `<>` out of Auctoratite.
Then, let's look at the a and b formats of the documents. Or one or the other? This has been explained in the introduction, so there are not many documents where this needs to be considered, but I still think we need to pick a guideline. If you take both, then each of the a and b versions should include information about what type of document it is. List below. 

Direct quote from the edition information:

"Furthermore, some documents about
to the office of the Penitentiary have been found in archives and
libraries in Sweden and Finland. If it is clear that these have their origin
in the Penitentiary, they have been included in the edition.
Despite the dominance of the documents preserved in the Vatican
Archives, the local archive and library collections form an important
addition, especially concerning the period prior to 1450 when the
Penitentiary records were still less accurate. The collections in the
Swedish archives contain seven documents related to instances that
cannot be traced in the archives of the Penitentiary.52 Furthermore,
Swedish and Finnish archives hold information on six Penitentiary cases
that are also to be found among the Penitentiary records."

Type of source                                   | Number of cases
-------------------------------------------------|  -----:
Littera ecclesiae                                |	1
Copy of supplication                             |	437
Original supplication                            |	1
Original supplication and its copy               |	1
Letter of grace                                  |	2
Letter of grace and copy of supplication         |	3
Copy of letter of grace                          |	5
Copy of letter of grace and copy of supplication |	3
Total                                            | 453

Risberg and Salonen

added #regest  

Next time, or sometime:
1. replace 8.5 in bold italics (i.e., the numbers between the text: bundles and a/b) with something else in single-spaced.
2. Add regest tags

## 11.6.2020

At some point each word will be auctorized in e.g. SPSS and then I think that the data needed for each edition word could be 
1. own id tag
2. the word itself
3. information about the document number 
4. information about the footnote referring to it, e.g. if there are several applications for the same file
5. information on the type of document, e.g. copy of the register or original application
6. whether the document belongs to the categories de promotis et promovendis, etc.
7. date of the document
8. the place/parish to which the document relates
9. the treatment of the word by the editor
10. basic form of the word
11. morphological analysis of the word
12. if the word is a proper noun, the form in the vernacular
13. information if it is part of a document entered in the register as a bundle

14. where the word appears in the document, e.g. salutation, ending, protocol, eschotocol, etc.
15. information about the Pope in whose era the document was handled, information about the approver, information about the procurator, etc.?
16. the word order number within the sentence
17. information on punctuation
18. open text field
 
## 16.8.2020 xml-experiment 

Auctoritate copypaste `tyko1 xmlexperiment2.docx`  
In the first document the following have been inserted:

```xml
<asiakirja aineisto=”Auctoritate” nro=”1” kategoria=”de uberiori” paivaus=”1410-05-28” paikka=””>
<regesta><nimi tyyppi=”rahvaankielinen”>Laurentius Johannis</nimi> from <paikka tyyppi=”kotiseurakunta”>Stockholm</paikka>, a cleric from the diocese of Uppsala and the
son of a priest and an unmarried woman, has earlier received dispensation from
illegitimacy through the bishop’s authority and permission to be promoted to minor
orders and to obtain an ecclesiastical office without the cure of souls. He now receives
a de uberiori dispensation to be promoted to Holy Orders and to obtain another
ecclesiastical office, including the cure of souls. The dispensation (is granted by the
cardinal penitentiary, bishop of Le Puy, <historiallinenlisatieto>Petrus Gerardi. For the cardinal penitentiaries, see Introduction, pp. 72–73; cf. app. crit. (The (anti)pope Alexander V reigned for only one year and died on May 3 1410.)</historiallinenlisatieto> and
) is valid for one other office and only
once.</regesta>
<editio><folio>1:17r</folio> Item similem gratiam facientes <nimi tyyppi=”latina”>Laurentio Iohannis</nimi> de Stokholmis
clerico Opsalensis diocesis, cum quo alias, ut non obstante defectu
natalium, quem patitur de presbytero genitus et soluta, ad omnes posset
minores ordines promoveri et beneficium ecclesiasticum, cui cura non
<folio>17v</folio> imminet animarum, / obtinere, auctoritate ordinaria fuit misericorditer 
dispensatum, cuius dispensationis vigore se fecit alias tamen rite clericali
caracteri insigniri. Supplicat igitur sanctitati vestre, quatenus sibi gratiam
facientes uberiorem, ut dicto non obstante ad omnes sacros ordines
promoveri et unum aliud beneficium ecclesiasticum, etiam si curam
habeat animarum, obtinere possit, secum dispensare dignemini per omnia 
ut supra in proxima. Fiat de speciali ad unum aliud et quod semel.</editio>
```
Supervisor *ANON* requested that the Latin words are in Conll form

File: `1_doc_experiment_word_list_data_experiment.xlsx`

→outline of how things could be

Probably, changes to this to get a conll format table. https://universaldependencies.org/format.html



## 17.2.2021
5 font letters, then all refer to a specific period of a specific papacy, including note_anchor tags


## 12.4.2022
All instances of font size 5 removed with content of type `[0-9][0-9][0-9]` deleted -anchor of historical notes

`([0-9]*)([])([0-9]*\.[0-9][][0-9]*)(^l)`

`</document><document number="\1" date="\3">\1\2\3\4`


To capture a line: `^13[0-9A-z .]*^13`

find the majority, number the right font `<[0-9]*>[ ][0-9]*\.[0-9A-z]*^13`

Replaced the headings with the following

`(<[0-9]*>[ ][0-9]*\.[0-9A-z]*^13)`

`<headingline>\1</headingline>`

363 replaced

went through all header lines and all headers starting with `<headingline>` and saved as version 2.1

## 17.8.2021

`<headingline>45 12.7 1414 Bologna` types still missing closing thing and endofplace and endofdate

made:  
`<headingline>3 4.11 1410 Bologna<endofplace>`  
`<headingline>1 28.5 1410<endofdate>`  

added to those that have a footnote an `<endofplace>` tag

`([a-z])(^13)(\</headingline\>)`  
`\1<endofplace>\2\3`  

`(\</headingline\>)`  
`\1<startregesta>`

## 19.8.2021
replacement that has not yet been used  
`(^13)(\<headingline\>)`  
`\1<endeditiontext><endofdocumententity>\2`  

Saved in version 2.7: Added missing last page, font replaced by Arial, language changed to Latin (World)

Marked the end of the editing line `<editions_line_end>`:  
Font size 9,5  
 `^13`  
 `<editions_line_end>^l`  
5,463 replacements

Saved version 2.8

apparatuses (also hits line numbers):  
Font size 7,5  
 `^13`  
 `<apparatus_line_end>^l`  
2734 replacements  
+5 manual corrections:  

font-size problem related to pseudo-small caps in names Size=6 `[A-Z]^13`: p. 196, 260, 266, 367, 409.

Nothing found with a-z.

Possible other problems appear to be single unlabeled rows, most likely caused by an end-of-line superscript or subscript, i.e. perhaps a numeral.


(The last line number 480 is not marked because it does not end the paragraph but the end of the document?)

Saved version 2.9

A plan to fix the line end tags:
- match `^***<end tag>` : add `<start tag>` to the beginning
- delete `<end tag> \n <start tag>`


1.9.2021

went through (number followed by r or v) and put start and end tag for all these and then saved 3.0

20.9.
document 11 added foil tags

Continue adding header tags here  
`<headingline>225-229 14, 17, 20.12 1475 Rome<endofplace>`

make sure that the beginning is enclosed in both tags around each numeral

(0-9) font arial bold 8,5

Example of unclear case: 
```xml
<headingline>51-53 15.7 1455<endofdate>
 </headingline><startregesta>Johan Olofsson from the diocese of Turku and the son of an unmarried couple, and
Nils "Nutasson" from the diocese of Linköping, also the son of an unmarried couple,
and Johan Johansson from the diocese of Uppsala, the son of a priest and an unmarried
woman, are granted simple dispensations from illegitimacy (by Cardinal
Dominicus).

Item supplicatur pro parte Iohannis Olavi de soluto et soluta geniti et <lb_folio=“6:57v”/> Nicolai Nutason de soluto et soluta geniti et Iohannis Iohannis de<editions_line_end>
sacerdote et soluta geniti.<editions_line_end>
```

No difference is made here: `<headingline>275–276 7.7 1483<endofdate>
 </headingline><startregesta>`

Same entry 287-288 22.5 1485

561v is written in the margin of 372

check 206-207

1.10 reached so far, continue `<headingline>385-387 2.9 1501`


## 05.01.2022 

Doc. 402: at the beginning something wrong
 (assistant is investigating):
 2.7 vs 2.8: blank line in 9,5 font, becomes an extraneous tag, but what about the missing tag on line 1?

402 EndOfPlace is strangely missing?

404 122v (I think there were some of these later?)


05.01.2022

Done:

Visual Studio Code:
```xml
</apparatus>
<apparatus>
```
--Replace--  
Ctrl+Enter

and the same for `<editio>`

TODO:

Line numbers and other missing <edition> tags cause problems:
Do you mark the line numbers with something first, and then you can put a suffix at the end of the line numbers, and then do it normally?
Similarly, footnotes to the numbers mess up the adjacent numbers, e.g. No. 402
`<headingline>402236 31.10 1509 Rome`

Quotes `’ “ ”` etc. should probably be fixed. From the Word save or in the editor or in Python?

`<lb_folio="1:17r"/>` is not XML, how to fix? `<lb>` is the line beginning of TEI-xml, so it should be `<lb folio="1:17v"/>` ?
But if it's not always at the beginning of the line, then lb might be inappropriate?

Line numbers in TEI?:

https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-lb.html

`<lb n="5"/>Row five.`  # Like this?

In document 437 there is a folio marking 455r without tags

## 6.1.2022 completed documents exported in bundles


## 9.1.2022

Line numbers: Arial - Normal - 6pt hits only the line numbers, italics will include also other things.

```
Doc 46: 5 after the last line?!
Doc 92 5 in the middle of the line "5m cum cura..."
Doc 112 15 --,,-- "... u 15t in forma..."
Doc 232 20 --,,-- "Prefatus 20 igitur "
Doc 234 ac [ac] 5 postmodum
There must be 1-236 of these following, I just didn't notice!
Doc 236 r.20 someone has eaten a syllable and 20 jumped to the beginning of the next line
Doc 251 35 ut 35 infra
Doc 268 r. 5
Doc 284 like 236 above?
294 40 --,,--
300b 25 & 30 --,,--
303 45
318 35
319 10
325 25
332 20
340 10
342 25
344 20
349 10
360 65
361 10
405 25
416 10
418 15
427 50
435 35
440 35
442 25
447 25 35
449 10
451 35
452 20 middle
452 50
```

## 11.1.2022

I need to go through No, No, No and r foil references

`(:[0-9][0-9][0-9]r)`

`<lb_folio="\1"/>`

Must continue with those with 1 or 2 nro and `r` and then those with `:`

## 12.1.2022

line numbers inserted `\1<line number end>`

need to find the anchors of footnotes and mark bold text in the text critical apparatus


## 13.1.2022

done:

`([0-9]) *space*`

`\1<end of apparatus critucus number>`

`><note anchor="1"/>` and MUST REMEMBER TO REMOVE `<note_anchor><note anchor="1"/></note_anchor>` EXTRANEOUS

### A new round

#### Must be deleted first 
- [x] Sara Risberg and book title
- [x] page numbers
- [x] text-critical appendices
- [x] historical references
- [x] Vatican place markings
- [x] anchors for footnotes
- [ ] **hyphens!** In VS Code?

## 25.4.2022

Removed *formatting > font > size*: all 6 pt 1762 pcs -> consists of:
- line numbers,
- folios,
- end parts of fake-small-caps words in footnotes e.g. `ORHONEN` of `Korhonen`;

replaced by line break ^l

Removed Sara Risbergs and associated (even) page numbers:  
`[0-9][0-9][0-9]^13Sara Risberg`  
->  
`^l #line break`  
164 pcs.


Removed page header Auctoritate Papae's and their associated (odd) page numbers:  
`[0-9][0-9][0-9]^13Auctoritate Papae ^= Edition`  
`[0-9][0-9][0-9]^13Auctoritate Papae - Edition`  
->  
`^l`  
163 pcs  

208: LunenSIS regens. - 'sis' is a bigger font 11! just bigger
Replaced with 9.5 pt as around.

248: viti -> sexti

437b: 3o -> tertio

## 1.5.2022
Removed reference anchors 1-297:
- font 5 pt
- `[0-9][0-9][0-9][0-9]` - 198 pcs == ok and removed
- `[0-9][0-9]` apparently 100 pcs, one by one removed
- `[0-9]` 1-9 + 1, 1, 2 probably
- could not be found between the Latin
- `[a-z]` 69 characters omitted, including endings of ordinal numbers and word endings, not inside edition.
- manually changed a few 5 pt -> 8.5 pt, of which Doc 4-5 hit the title and were replaced by a line break in the Regesta deletion, corrected manually.
- 5pt " " -> 9pt " " these remain only in headings
- 5 pt nothing -> 9 pt nothing: may have contained line breaks.

#### Regestas removed
8.5 pt, not bold (because the numbers of the bundle references are also 8.5 pt):
- `blank` -> `^l` (leave blank lines)

#### Text-critical apparatus
- 7,5 pt, includes singular etc1's, where the number is 7 pt.
- 7 pt also includes paragraph breaks left over from page headers.
  - 7 pt `^p` -> 8 pt `^p` 326 pcs
- 50 pcs remaining in 7 pt size, deleted

also includes 9 pt size spaces from before

7,5 pt -> `^l`

## ADDING XML TAGS

## 8.5.2022
To be added based on the formatting, the rest will be done in Code?:
- `<i>` italics
- headings:
```xml
<document My_nr=”23” aucnro=”27” date=”1555-05-06” place=”Rome” canonlaw=”matrimonialibus”>
Lorem ipsum … 
</document>
```

#### To be added by replacement:
- ampersands: `&` replaced by `&amp;`
  - where are these used/found?
- additions: `<` replaced by `<addenda>`? and `>` replaced by `</addenda>`.
- `/` omitted? (They are foil changes) 

## 14.8.2022

### replace `<`, `>`, (`/`)  
- `<addenda></addenda>`  
- `/` removed? foil change  
- `&` -> `&amp;` can be done later

Removal of slashes: removed 110 slashes in font 9.5 `/` and replaced with "none"

### Add italics-tags: 

italicized; any character `x` -> `<i>x</i>`

`(?)`  
->  
`<i>\1</i>`

11 066 replacements made.

Next, delete `</i><i>`  
10733 replacements made.

### Heading line marking:

Font 10 pt

`(?)`  
->  
`<h2>\1</h2>`

And correction:  
`</h2><h2>` delete and  
`</h2> <h2>` also, replace with *space*. Because there is some 9 pt font size inside headings (from removing references?)

## 27.8.2022

Somewhere along the way, `<`'s have been replaced by `{`'s and `>`'s by `}`'s.
Header lines as specified above:
7488 replacements
7064 replacements (`</h2><h2>` deletion)
`</h2> <h2>` not found, although document 20 seems to have one!
The search function in the side panel finds 29, and then the replacement function part: 29 replacements. Could the font choice have been left ambiguous.
So now the end tags of h2 are on the next line, e.g:
```xml
<h2>22 15.1 1450 Rome
</h2>22a
```

## 28.8.2022

Replacement of special characters not allowed:
- `[ ]` delenda to be deleted
- `/` nova codicis pagina new page of a manuscript
- `< >` supplenda to be added was changed to { }
- `† †` turbata corrupt
- `+` verbum vel verba (quae the following word(s)
sequuntur) add. added (in the manuscript)

discarded `&` character 1 pcs -> changed 1 pcs to "and"
likewise replace those that the editor thinks should be deleted `[` with the tag `<del>` 53 pcs
`]` `</del>` as well 53 pcs


previously replaced addenda with `<>` given by the editor replaced with `{}` versions and now replaced with `{}` tags `<add>` 83 times and `</add>` 83 times

and six pieces of six crosses removed, three of the beginning of the word and three of the ending of the word.
`<unclear reason="illegible">
</unclear>`

Saved all at once: vers. 4.0_tags

Hyphens:

Doc 89 italics tag problem
```xml
<i>litteras confes- </i>
<i>sionales
```
corrected manually.

`-\n*`
`[ empty ]`
108 replaced. Resulted in some long lines.

```xml
<h2>130–133 3.12 1466 Rome
</h2>
```

 metadata <my_new_number><old_number><bundle entry info>
Risberg numbering = 130-133
<edition>

<old_ed_nr>130</old_ed_nr> Nicolaus Nicolai canonicus Aboensis; 131 Laurentius rector parrochialis
ecclesie Nerpis presbyter Aboensis diocesis; nobilis Bartichino Iapson et
eius uxor dicte diocesis; nobilis Iohannes Olafson ac Catherina eius uxor
petunt litteras confessionales ad perpetuum duraturas. Fiat de speciali

pro omnibus. Philippus sancti Laurentii in Lucina.
</edition>

```xml
<h2 id=”ap125” num=”130” to_num=”133” collective_bundle=”y/n” date=”1466-12-03” place=”Rome”>130–133 3.12 1466 Rome</h2>
```
```xml
<h2 id=”ap125” num=”130” to_num=”133”>130–133  <date when=”1466-12-03”>3.12 1466</date> <place>Rome</place></h2>
```

### metadata 
old Risberg nr = 130-133
<edition>
<docbreak num=”130”/> Nicolaus Nicolai canonicus Aboensis<docbreak num=”131”>;</docbreak> Laurentius rector parrochialis
ecclesie Nerpis presbyter Aboensis diocesis<docbreak num=”132”>;</docbreak> nobilis Bartichino Iapson et
eius uxor dicte diocesis<docbreak num=”133”>;</docbreak> nobilis Iohannes Olafson ac Catherina eius uxor
petunt litteras confessionales ad perpetuum duraturas. Fiat de speciali

pro omnibus. Philippus sancti Laurentii in Lucina.
</edition>

### VS Code heading lines:

357 hits
```xml
<h2>([0-9]*) ([0-9]*)\.([0-9]*) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1">$1 <date when="$4-$3-$2">$2.$3 $4</date>$5</h2>`

Problem: This is not able to add zeros to an ISO date. One solution: make four substitutions separately for different cases according to the length of the day and month numbers.

Doc 77 `<Rooma>` not replaced in Word `<Rome>`

```xml
<h2>([0-9]*) ([0-9]*).([0-9]*) ([0-9]*)(.*)
</h2>
``` 
hits doc 77 even if I was thinking it shouldn't  
‘.’ has to be escaped.  
reformat to  
```xml
<h2>([0-9]*) ([0-9]*)\.([0-9]*) ([0-9]*)(.*)
</h2>
```

(Without a place 14 items:
```xml
<h2>([0-9]*) ([0-9]*)\.([0-9]*) ([0-9]*)(.*)
</h2>
```
not including bundle entries.)

Could these work:

#### replaced 90 pieces #hits those with a single-digit day and month
```xml
<h2>([0-9]*) ([0-9])\.([0-9]) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1">$1 <date when="$4-0$3-0$2">$2.$3 $4</date>$5</h2>`

#### ### corrected 32: those with one digit in the date, but two in the month
```xml
<h2>([0-9]*) ([0-9])\.(1[0-9]) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1">$1 <date when="$4-$3-0$2">$2.$3 $4</date>$5</h2>`

#### #### 170 replacements when there are two digits in the day and one in the month
```xml
<h2>([0-9]*) ([1-3][0-9])\.([0-9]) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1">$1 <date when="$4-0$3-$2">$2.$3 $4</date>$5</h2>`

#### ### 65 are replaced when there are two digits in both the day and month
```xml
<h2>([0-9]*) ([1-3][0-9])\.(1[0-9]) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1">$1 <date when="$4-$3-$2">$2.$3 $4</date>$5</h2>`

357 replacement made in a total of four batches, as should be found in the code above.


### Bundles:

225-229 awkward date mess, to be done by hand -> done by hand

```xml
<h2>([0-9]*)-([0-9]*) ([0-9]*)\.([0-9]*) ([0-9]*)(.*)
</h2>
```
finds 35 hits.

```xml
<h2>([0-9]*)–([0-9]*) ([0-9])\.([0-9]) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1" to_num="$2" bundle="y">$1–$2 <date when="$5-0$4-0$3">$3.$4 $5</date>$6</h2>`
9 items

```xml
<h2>([0-9]*)–([0-9]*) ([0-9])\.(1[0-9]) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1" to_num="$2" bundle="y">$1–$2 <date when="$5-$4-0$3">$3.$4 $5</date>$6</h2>`
2 items

```xml
<h2>([0-9]*)–([0-9]*) ([1-3][0-9])\.([0-9]) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1" to_num="$2" bundle="y">$1–$2 <date when="$5-0$4-$3">$3.$4 $5</date>$6</h2>`
18 items

```xml
<h2>([0-9]*)–([0-9]*) ([1-3][0-9])\.(1[0-9]) ([0-9]*)(.*)
</h2>
```
`<h2 num="$1" to_num="$2" bundle="y">$1–$2 <date when="$5-$4-$3">$3.$4 $5</date>$6</h2>`
6 items

9+2+18+6=35, very good!

That leaves two documents that have a date with a `/`
- documents: 7 and 77
- 77 angle brackets `<Rome>`

the bundle attribute is added to the first corrected ones:
`(num="[0-9]*")(>)`
`$1 bundle="n"$2`
357 pcs

Replaced the `<` `>` signs in the header with `{` `}`

```xml
<h2 num="77" bundle="n">77 <date when="1458">1458/1459</date> {Rome}</h2>
```

## 5.9.2022 hyphen problem

Some of the hyphens have not been transferred at all from pdf to Word. So they are missing without leaving a trace. Missing lines are (typically?) those followed by 270v or a line number, even at the beginning of the next line?
Adobe reader can't differentiate between hyphens and em-dashes in the search function, Firefox can, but for some reason it can't find all the hyphens (with good luck it finds exactly those hyphens that have been left out by Word! No good luck, it's random.)
Copypasting from Firefox: the `bene-dict` of document 2 is the ascii hyphen 0x2d, but Firefox can't find it.
Microsoft Edge finds a slightly different  hyphens than Firefox, maybe a little less?
And even Adobe Reader doesn't find all hyphens.
In Adobe Reader: 
DOC. 16:
Upsalensis is not found, its hyphen is found.
Doc. 17 None of these hyphens can be found in the Reader search.
- natalium is found and colours both lines from start to finish.
- ecclesiasticum is not found.
- auctoritate also colours two lines.
- obtinendum colours two lines.

### dealing with bundle entries:

need to keep Risbergs numbering and info about doc boundaries:
`<lb num=” [nro] “ >[nro]</lb>`
```xml
<h2 num="23" to_num="24" bundle="y">23–24 <date when="1450-02-07">7.2 1450</date> Rome</h2>
<edition>
<lb num=”23“>23</lb> Similem gratiam Christoforo Olavi scholari Aboensis diocesis de
soluto et soluta <i>genito</i>.
<lb num=”24“>24</lb> Similem Olavo Olavi eiusdem diocesis de soluto et soluta <i>genito</i>.
Fiat de speciali. Dominicus sancte Crucis.
</edition>
```

## 12.9.2022
DOC 51 backwards; check quotation mark type
`<lb num="51"/>`

 bundle="y">63-68 leaves text outside the tags at the beginning and end

hyphens corrected

### The hyphens, part 2: Linux
Evince: Apparently can find all hyphens, but can't distinguish them from em-dashes.

Okular: Seems to find all the hyphens, and distinguish them from the dashes! A bit weird/unpredictable where it starts searching, but it's so fast that you can search from the beginning with the button down.

## 26.6.2024 Towards the PeDoCo format

`<document>`

`<text>`

and 

`</document>`

`</text>`

395 replacements in both.

### TODO (see also [Combine XMLs – plans](#combine-xmls--plans)): 

- [x] Translate bundle tags -> bundle="y/n"
- [ ] `<h2>` -> split attributes to `<text>` and `<front>`
- [ ] Add PeDoCo numbering:
  - I Auctoritate
    - Just replicate auctoritate numbering? 1–453
      - No, number `<text>`'s continuously (`n="20"`), also keep auctoritate numbering (`onum="22"`)
    - versions (a/b)? `<version onum="22" version="a">`
    - bundles? `<div` ?
  - II England/Wales
    - numbers: 396–nnnn ?
  - III Norway 
    - numbers:


## 27.6.2024

Rename `bundle="` attributes  
395 replacements





# NORWEGIAN DATA

30) P.A. vol. 60, fol. 380v                                                               	Rubrica: De illegitimis
Gonini Tur. ii ½ .
In prima forma tantum pro parte Petri Olavi scolaris Nidrosiensis diocesis de soluto <geniti> et soluta <petitur, ut non obstante defectu natalium ad omnes etiam sacros ordines promoveri possit et in ipsis ministrare>.
Fiat de speciali, M<ercurius>, regens; et committatur episcopo Leglinensi Sanctitatis Vestre penitentiario ad presens in Romana curia residenti, quia orator est presens in eadem; fiat M>ercurius>.
92) P.A. vol. 25, fol. 13v                                                  	Rubrica: De matrimonialibus
Paulus Iohannis laicus et Solnet Beronisdeatter mulier Scaholtensis diocesis petunt cum ipsis dispensari de <matrimonio> contrahendo in quarto consanguinitatis gradu, quo invicem sunt coniuncti, cum legitimatione prolis exinde suscipiende.
Fiat de speciali, Iul>ianus>, titularis Sancti Petri ad Vincula.
Rome apud Sanctum Petrum, vii id. dec. anno sexto domini Sixti pape iiii.

 In order to match < and >, documents 29 and 92 were corrected

1 to replace < signs % 393 times
followed by > characters # with character 393 times

The ) character is then searched for
Found 144 - replaced by </num>

Add a start tag for the numbers
([0-9]{3}</num>)

([0-9]{2}</num>)
and {1}
resulting in
<num>98</num> 144 times
Add information about the archival location:
(</num>)
$1<archive>
And close the archive tag by hitting the word
(Rubrica) (142 Times)
</archive>$1
This hits too many Rubrica words, so delete the ones with no location information, i.e.
as. 1, 
Then close the three tags 
(\[Ingen)
</archive>$1 all 144 PA locations contained in the file are compressed
a closing tag is added to the end of the <header> line

want to add an edition starting tag to those that do not have a title
(rubrikkangivelse\])
$1\n <edition> done three times
Then, in those with the word header
(</header>)
$1\n <edition>

Marking the editing text as bundles
(<num>)
</edition>\n\n$1

Start the edit by replacing
the end of the header
header and <edition>'

### Back: Where are the hyphens?
At least some of the hyphens have disappeared at the commit:
 6b8564 Remove hyphens. 28 Aug 2022

I think there was a problem here:  
`-\n*`  
`[ empty ]`  
108 replaced. Resulted in some long lines.

## March 1, 2023

### Hyphens corrected  

`-\s`  
`*\s*(\w*\s)`  

`$1`  
(line break Ctrl-Enter)  
66 pcs  
Note! This breaks line pairs with a comma or period at the end of the first word of the second line! Manually corrected 5 of them.

### `<document>` tags:

`<h2`  
`</document>`

`<document>
<h2`  
395 pcs, the first one and the bug was fixed by hand.

### Several wittnesses

bundle="y">
bundle="y" several_wittnesses="n">
bundle="n">
bundle="n" several_wittnesses="n">
We have gone through the documents with version a and b. Added some useful tags. 7 documents, versions a and b.

# ENGLAND AND WALES DATA

7 Oct. 2022 

Deleted:

    footnotes

Remaining:

    Editions
    Keep the paragraph division! (26 Oct 2022 How do you know when a page break is a copy change and when it is not?)

Replacement:

    / // \
        what is the TEI marking for these?
        \ / Text added above the writing line
        / \ Text added on the line
        \\ // Text added in the margin


    &, <, > if found
        <> not found,
        & is found only on the first pages, and in the footnotes for the combinations of bachelor and doctor and 581. [Florence], 25 September 1442. John Digon, BCL & CnL, priest

Font size:

    all editions are 10 pt: including titles and others.
    except docs 16: xiiiio and xvio o. And ac 28, 148, ...?, 461, 462, 487, 488, 489, 492, 501, 541, 617, 636, 642, 643, 515
    doc 420 Thomas Wollemi
    at least some of these have a font size of 5,5 pt

    [Rome, at Sta Maria Maggiore]

    there are probably other locations as well

    footnotes 9 pt, footnote 6 pt and 10 pt

    size 10 also the footnote numbers, and the footnote suffix (which should be removed first? with regexes?) \nSupplications . . . [0-9]*n . . . Supplications/Eugenius/ . . . or \nSupplicationsxx.indd.*\n

Can the whole paragraph with "Same grant as xxx sought" be deleted?

Are there any references in the edits? At least in ac 528 there is reference 173. Font 10 pt. I guess I have to look for numbers at the end? Which should not be in Latin?

- The edits start indented, but at the page break the indentation disappears.
- Footnotes that continue from the previous page continue on the next page directly after the last line, without a line break. However, the font is reduced. Big problem if you mark the end of a reference line and delete the whole line. E.g. Ac 15, 77, 

It may be easiest to just delete all the extra by hand.

One could try to search for a bold number with several paragraphs before the next one.  
nn. the document starts.  
nn without a period: reference to a document. However, it may end at the end of a sentence (which is usually not in bold).  
[lorem ipsum matrimonialibus] heading   
There does not appear to be anything else in bold.  
If you search for anything in bold, then e.g. the ac-numbers on the page before the Editorial Notes are not found?! The previous 10 pt condition had apparently been left to haunt again, found the next day.

[sic] obviously means an error in the original. TEI-marking by hand?  
[fol. ..] entry in doc 556, and in others.  
Doc 618: at the end of the crucis is the sign of the cross, and in others  
Doc 715: the cross is a plus! Fiat D. s. +.   
Doc 622 contains a pair of curved brackets (). Are there many elsewhere, in the regesta?

### Oct 8, 2022
Document numbers hit:  
Search in bold, use special characters  
`[0-9]*\.`

Highlights 1192 items.
There are 1198 documents, 6 are missing.

Doc 177 (calendar) is missing a dot in the number. I wonder if there are any elsewhere?
[1147] full
[1119] calendar
[1076] full
982.: (Approved with 984.) corrected with a non-highlighter dot
[951] calendar
[920] calendar
[1118] calendar

The number matches. But are there any mutually exclusive errors?

### Oct 9, 2022
Search: bold, use special characters
([0-9]*\.) 
Replace with:
`</document><document nrEW="\1">`
`\1` or `$1` or what was in Word? (in Word `\`, in VS Code `$`)

### Oct 10, 2022

Order of importance

off // \\\\ types  
remove unnecessary English elements  
markup of English regesta

should we open volumes II and III and see what solutions are there

### Oct 21, 2022
Supplications-02.indd*^13
find the end of lines!
234 items, 235 pages?
Can these be removed or are they needed to identify page endings?

### 22 Oct 2022
Todo:
x delete / \:t
replacement with tags? but not before removing other non-xml characters.
x check other non-xml tags < & (> ' "), everything else ok, but what about regexes?
x remove/replace end of page lines
mark document boundaries with tags

### 23 Oct 2022
Supplications-02.indd*^13
<pb/>
234 replacements, 235 pages?

(26.10.) Aha! Space! Replaced by hand.  
Supplications- 02.indd 152 04%11%2012 17:00:51 91 Eugenius IV (1431-1447)

But does '/' // \ interfere with replacements? Taken out at this point, add back in later!  
`<pb/>`  
`<pb>`  
234 replacements

Note: `<pb>` should mark the beginning of the page, not the end! (No other effect but page numbers go the other way?) https://tei-c.org/Vault/P5/2.1.0/doc/tei-p5-doc/en/html/ref-pb.html

`/ // \\ \`:  
\ / Text added above the writing line  
/ \ Text added on the line  
`\\\ //` Text added in the margin

/ corpus. %.  
50 replacement (including the space at the end of the line. "Aha!")

\ korv. ¤  
39 replacements

Doubles first:  
`\\\` or `¤¤¤`  
`<add place="margin">`  
1 replacement

`//` or `%%`  
`</add>`  
1 replacement

what kind of challenges are there

in what ways could the item have been marked by an x

stratification

interpretations may be open to different opinions

what others can learn from this

### 26 Oct 2022
now left:  
% 46 pcs  
¤ 37 pcs.

¤Text added above the line%  
`<add place="above">Text added above the line</add>`

%Text added on the line¤  
`<add place="inline">Text added on the line</add>`

(¤)(*)(%)  
`<add place="above">\2</add>`  
34 replaced

(%)(*)(¤)  
`<add place="inline">\2</add>`  
3 replaced

Remaining:  
¤ No results  
% 9 pcs, all in references  
Good!

`<pb>` back to `<pb/>`, 235 replacements, number ok.

& replaced by `&amp;`
10 replacements, so these should be in the references.

Todo:  
Document boundaries  
small fonts
overstrike <del rend="overstrike"></del>, done like italics in Auctoritate?  
https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-del.html

Accidentally found discussion from years ago:  
https://cpb-us-e1.wpmucdn.com/blogs.rice.edu/dist/8/2082/files/2013/10/TEI-HURC604-2013-2.pdf

### 29. lokak. 2022

kursiivit:
- add `<i>` tags like auctoritate.
- [sic]
  - apparently an error in the original, how to mark? As such? `<i>` tags good to have
- [recto something] 
- what would be the correct TEI notation?
- [ this is an addendum ]
  - `<add doer="editor">` what is the correct format?

Can you just delete everything in 9 pt font? Then the reference numbers will remain in the footer as well. And small fonts will remain, after the numbers, or at least on their own line, hopefully.  
But: the footnotes continue from the previous page => the numbers end up at the end of the text.

Try Libreoffice (7.4.2):
- crashes sometimes, once when scrolling ac. 36, now not.
- test now 7.3.6.2
- footnotes continue from the previous page? broken in docs.15 and 77
- indentation issue like Word
- font sizes are pretty much the same as in Word
- regex'es & font styles
- shows paragraph styles Pa38-Pa63, but can't search with these???


475: ref 136: [de gratia] incorrectly crossed out

### Footnotes omitted, document tags outlined:  
9 pt off  
over 434 replacement  
`<document numbers>` insertion  
font 10 pt, bold  
`([0-9]{1;4})\.`  
(comma to be replaced by semicolon in Finnish locals, list separator)  
`</document>^l^l<document num="\1">\1.`  
1191 replacement, = 1198-7, ok  
begin and end of the file manually.  
177 point added and then replaced. saved 1.6  
[920] etc not corrected; [] not in bold.  
Bold in square brackets included  
`\[([0-9]{1;4})\]`  
`</document>^l^l<document num="\1">[\1]`  
replaced 6 pcs.

The suffix goes too long in these:

Fiat de speciali et quod semel.  
De sancto sepulcro et sancto Iacobo `<add place=”inline”>`et commutatione votorum`</add>`  
Supplicationes signate per dominum cardinalem Aniciensem maiorem penitentiarium de mense Maii [recte Aprilis] pontificatus domini Alexandri pape V anno primo.
`</document>`


Saved 1.8, headings and ingresses still on the wrong part of the closing tags.

Correction?
```
replace (bold text) -> </document>\1
search </document> * </document> -> </document>
```
line numbers in a row before `<pb/>`: delete the whole line.
numbers go on the same line doc. 15, 77, ...
if the line ends in `</pb>`, the whole line is replaced by just `</pb>`.


## 2023-08-23 Word adjustment 10 months later

Eng_W_material_copy_paste_1.8_document_limits-ready.docx

### Mark regesta and calendae entries:

`\<document num="(*)"\>(*)^13`

`<document num="\1"><regesta>\2</regesta>^13`

1198 replacement, Eng_W_document_copy_paste_1.9_regestat-eka-company.docx

FIXME regesta ends with a page break! E.g. ac. 7.
Whether: Search ...^13[  
Calendae stuff to be done separately. Ex. 101.  
And are all [place]? Certainly not 94, 151, 154, regesta [Rome], [Florence]. 
What about doc 34, for example? Text in italics, is doc 37 text in italics the same?  

#### Try to find `</regesta>' at the end of the page
`\</regesta\>^13[0-9 ]`  
You only match one number. How about repetition?

> The construction {0,} (find zero or more of the preceding item) is refused as incorrect syntax.

And; a semicolon is required instead of a comma in Finnish syntax:

`\</regesta\>^13[0-9 ]{1;}`  
works. 
- Are there any references in all of them? (no)
- Or even a space? ( )

Page break = ^12  
Not found in the whole document: ^12, ^n, ^m  
But this works instead:  
`\</regesta\>^13[0-9 ]{1;}\<pb/\>^13`

***Note:***  
`\</regesta\>(^13[0-9 ]{1;}\<pb/\>^13)(*)^13`

`\1\2</regesta>^13`

110 replacement. v. 1.91a 

**NO**: edit may contain multiple copies, must search `</document>`.

FIXME `\</regesta\>(^13[0-9 ]{1;}\<pb/\>^13)(*)\</document\>`

FIXME `\1\2</regesta>^13`

**NO**: No regesta in the edit, doc 17 broken, 1.91a. So was the end of the regesta in the page break and broke?

The edition is indented 0.42 cm / 0.17", but this can only be found in a search if you enter it as an exact value of 12 pt. (If the edition continues beyond the page break, the first paragraph is not indented, but we were not interested in editions at the current moment.)

Does any paragraph setting persist beyond the page break?

## Proto: correct regesta page boundaries.

### Mark nested paragraphs `<p>`

`(*)^13`  
Indentation: left 12 pt  

`<p>\1</p>^13`  
545 replacements. (Up to doc 7, double `<p>`.)

And now, of course, as `<p>` continues across the page break, the continuation is not a p or anything else. Can this be fixed in the same way as the regesta changes? How do you know what the next page continues on? `not <`?

Plan:  
`</p>` + page break rotation + paragraph break + whatever (so ^13 ?)  
  
`\<p\>(^13[0-9 ]{1;}\<pb/\>(*^13)`  
But the next page can continue with anything!

***Document 15 is not indented!*** Why? Are there others? At least Doc 78. The original 15 is indented.
- v. 1.6 not included (document limits)
- v. 1.5 is nested.

Search: `</regesta>` + page break code+ possible paragraph breaks + `<p>`  
Replace with: eiregestaa + page break code + possible paragraph break + `</regesta>` + `<p>`  

`\</regesta\>(^13[0-9 ]{1;}\<pb/\>^13)(*)\<p\>`  
`\1\2</regesta>^13<p>`  
69 replacements

What happened to doc 17:
married with legitimation of any issue. Reg. 1, fol. 56r.  
\- `</regesta>`.  
9 10 `<pb/>`  
\+ `</regesta>`

**DOC 633: regesta does not end, no suffix.**


### Latin main take aways:

`\</regesta\>(*)\</document\>`

`</regesta></edition></edition></document>`

Popes and document types and diverse explanations are on the wrong side of the document.

### Plan:

1. Mark the popes etc.
1. Change the position of the elements as appropriate.

### Places and times:

?

### Names of popes:

`(*)^13`  
(Bold) 14 pt

`<pope>\1</pope>^13`
6 replacements, JOHN XXIII corrected manually.

But * finds only one character at a time. Where does the greedy search come from? ^13 would help, but apparently it's no longer in bold, so can't be found.

Searching with just 14 pt works! Except JOHN XXIII name is followed by a reference-* in size 8, breaks off..

### Document types:

Bold Italic 10 pt

Same as the pope, search brackets/paragraph/line breaks are not bold italics. Need to do like the italics?

Greedy search trick:
https://superuser.com/questions/993886/greedy-match-in-ms-word-regular-expression

So something like this:  
`(*[!¤]{1;})`  
bold italics

Sort of worked, but with an upper limit at the lower limit. The upper limit is 255, a higher one will give an error. 
So this finds {1;6} 6 character long text strings. {1;255} will not hit shorter ones.

Surrounding square brackets not in italics! Do:  
`[<type>(*)</type>]`  
`<type>[1]</type>`

### Square brackets

[Bononie],  
[sic] (content in italics)  
[cuius dispensationis] 





## 2023-08-30 Return to v. 1.5, before 'document limits'
## No, return to 1.3, cross-outs to be tagged

Goals for refinement: 
- fix missing indentations e.g. ac 15 and 78
- mark popes and types in time so that they come on the right side of the bullet points

---------
### Collection of old ones:

##### 1.0:  
DOC 982: "984." period bold out.  
##### 1.1:  
 Introduction etc. initials removed.  
##### 1.2:  
- Supplications... -> `<pb>` (without slash)
- / -> %
- \ -> ¤
- \\\\ // -> `<add place="margin">`
- (Doc 486 p. 91 Supplications- 02 with space is left)
- (Doc 816 "de speciali D. /%s. †. I.\..¤. Reg. 4": as if the periods were included in the substitution, why? Seems ok.)
##### 1.3:
DOC 486 p. 91 space Supplications corrected
##### 1.4:
- %¤ -> `<add place="above"/"inline">`
- (At least in doc 609 the overline also appears in the tags, including the ending tag: `ex<add place="above">cons</add>istente`")  
**FIXME: STRIKETHROUGHS SHOULD BE MARKED BEFORE THIS?**  
Search for `Superscripted: <` / what about italics-slashes-...?  
The p-letter is crossed out in Doc 715.
#### 1.5:
- `<pb>` -> `<pb/>`
- & -> `&amp;`
#### 1.6:
- Doc 177 dot reportedly added
- `<document>` tags, numbers
- footnotes removed (numbers left, up and down)
- Doc 77 some strange formatting, 78, 513 - 514, (692-694, 822, 893, 977)
#### 1.7:
 Doc 920, 951, 1076, 1118, 1119, 1147 [] in bold: [920] etc
#### 1.8:
 document tags for 1.7 corrected manually
#### 1.9:
regesta tagged, page breaks bugs: regesta always ends with a page break.
#### 1.91a:
pagination and regesta,  
14, 101, 269, 303, 322, 430, 446, 452, 463, 510, 554, 575, 600 fixed,  
17, 38, 48, 66, 81, 85, ..., ***420***, ... many more broken. Do I have to fix it by hand?
#### 1.91b:
`<p>`-stamps 12 pt for indented paragraphs.

#### 1.92
pagination of regesta cases  
broken 48+53, 66+77, 81+82, 85+87, ...

---------
So, I have to go back to v. 1.3.

#### The task ms word:
- x manual corrections bold .
- x / \ --> % ¤
- manual corrections: 177 point, bold [ ] 920 etc. 6pcs
  - saved v. 2.01
- footnotes omitted, 9 pt
  - 89_711 replacement, saved v. 2.02.
- & -> `&amp;` Doc 581 regesta
  - saved 2.03
- strikethrough `<del>`? 515 dig_tur (tur with lower case, same as in original? FIXME)
  - 801 replacement + 724 replacement deletion of spaces
  - saved 2.04
- `<i>` ( not found in `<`:and version 1.92)
  - 106_578 + 104_081 replacements
  - saved 2.05
- %¤ -> `<add>`
  - for some reason had to be done by looking through
  - saved 2.06
- `<pope>` 14 pt, JOHN XXIII corrected manually.
  - saved 2.07
- `<type>` Bold Italic 10 pt + square brackets included
- other stuff in the middle, identification?
- `<pb>` -> `<pb/>`
- `<document>`
- `<p>` 12 pt
- `<regesta>` 

#### The task vscode / python:
- remove reference numbers from edits. And at the same time from footnotes?
- Delete the whole paragraph with "Same grant as xxx sought"?
--------------

#### Strikethroughs are done like auctoritate's `<i>`t

`(?)`  
Use wildcard characters  
Strikethrough, No Double Strikethrough

`<del>\1</del>`  
801 replacement.

`</del><del>`  
( No wildcards or anything else)

`( empty)`  
724 replacements

doc 9: where does `<</del>` come from? A minor mix up in the word diff entry? Yes, it looks good.

#### italics as in auctoritate
`(?)`  
Use wildcard characters  
Font: Italics

`<i>\1</i>`  
106_578 replacements

`</i><i>`  
((No wildcards or anything else)

`( empty)`  
104_081 replacement

### 26. October 2022 -> 31.8.2023
now remaining:  
% 46 pcs 37 (were there 9 /'s in the footnotes?)
¤ 37 pcs 37  

¤Text added above the line%  
`<add place="above">Text added above the line</add>`

%Text added on the line¤  
`<add place="inline">Text added on the line</add>`

(¤)(*)(%)  
`<add place="above">\2</add>`  
34 replaced - same but wrong, 

(%)(*)(¤)  
`<add place="inline">\2</add>`  
3 replaced - 0

Replaced by eyeballing everything through.

Remaining 2023-08-31:  
¤ No results  
% --,,-- 
Good!

## 2023-09-01 DOC 15 indentation again

v. 2.07
Again the Doc 15 indentation is broken, and the gap disappeared between regesta and edition, the P-sign of the track change is there.

- 2.06 broken
- 2.05 broken
- 2.01 intact
- 2.03 broken
- **2.02 broken:** (9 pt deleted)

### Return to 2.01

Around the doc 15 paragraph change, there seems to be no 9 pt anywhere.

But at the end of this edit track there is ***from the previous page a continuous underscore*** @ 9 pt, probably something to do with it.

DOC 78, same thing, footnotes continues from the previous page.

If you delete the reference in doc 15 with the del button, the indentation stays! But if you then delete *9 pt, the indentation disappears again. (88879 replacements, not saved)

When replacing one by one, the 9 pt search hits the edition endnote character, should only the alphanumeric characters be deleted? 

Remove all but paragraph breaks:  
`[!^13]`  
Font: 9 pt

`(blank)`  
89263 replacement

**No indentation remains** (the page break reference numbers are in different paragraphs, so old indentations have to be changed when reusing).

Saved 2.1.0

& -> `&amp;` doc 581 regesta  
1 compensation  

Saved 2.1.1

`(?)`  
Use wildcards  
Strikethrough, No Double strikethrough

`<del>\1</del>`  
801 compensation.

`</del><del>`  
(Ei yleismerkkejä tai muutakaan)

`(tyhjä)`  
724 replacements

(Apparently `//></><add place="margin">` has also been replaced already, I think it's from 1.2 onwards.)

Saved 2.1.2

## In what order should things be done?

1. footnotes - remove 9 pt
1. manual corrections
   - only at the beginning or at the end or at the last minute
1. temp corrections `/ \` -> `% ¤` ( -> `<add>`)
   - is it enough to replace `/`
1. `<del>`
   - before add
1. italic
   - span tags must end up inside the paragraph
1. `<add>`
1. `<pope>`
1. `<type>`/category
1. `<p>` indented 12 pt
1. `<document>` boundaries
1. `<regesta>`s
1. `<edition>`s

-----------------------

### 2023-09-04 `<i>`, `<add>`, `<pope>`

**Test:** `<document>`, `<regesta>`, `<edition>` to 2.07.

`(*)^13`  
Indent left 12 pt

`<p>\1</p>^13`  
545 replacements (a couple of unindented ones, the total remains short)

And that leaves the couple of post-page breaks to be corrected manually.

Saved 2.0.8test

Continue with 2.1.2 as usual.

--------------------------

## New plan for block type elements:
1. 12 pt indented `<p></p>`
1. **4321.** bold == `<document><regesta>`
1. `[!p][!>]<p>` -> `</regesta><edition>` ( confusing `<i>` or other?)
1. `</p>[!<][!d]` -> `</edition></document>` ( here the beginning `<document>` is mixes up the results)

--------------------------------

#### Indented paragraphs (12 pt) `<p>`

`(*)^13`  
Indent: left 12 pt  

`<p>\1</p>^13`  
548 replacement.

Saved 2.1.3

#### `<document num><regesta>` add start tags 

**4321.** font 10 pt, bold  
`([0-9]{1;4})\.`  

`<document num="\1"><regesta>\1.`  
1192 replacement

**[4321]** Bolded with square brackets  
`\[([0-9]{1;4})\]`  

`<document num="\1"><regesta>[\1]`  
replaced 6 pcs.

Saved 2.1.4

#### `</regesta><edition>`

`[!p][!>]<p>` add escaping and paragraph break:  
`([!p][!\>])^13\<p\>`

`\1</regesta>^13<edition>^l<p>`
298 replacements

saved 2.1.5

----------------------

Plan to fix the paragraphs at page boundaries. 

`(</p>*<pb>*)</regesta>^13<edition>^l` add escaping:  
`(\</p><pb><*)\</regesta><13<edition><^l`  
This is greedy, but maybe it's ok.

`\1</p>^13`
Replace not tested

----------------------

#### `</edition></document>`

Find breaks that are just before a `<document num=...`:  

`</p>^13<document`  
No wildcards

(`</p>^l</edition>^l</document><document`)  
(`</p>^13</edition>^l</document><document`)  
`</p>^13</edition>^l</document>^13<document`  
214 replacements

Saved as 2.1.6

Find others:  

`\</p\>^13([!\<])`  

`</p>^13</edition>^l</document>^13\1`  
91 replacements

Saved as 2.1.7

---------------------------------

## IDEA: 

Make a second version with only the indented Latin/edits. And even a third version with just the unindented ones.

You can then use these to do some magic with python or some perl.

**But** the edits at the beginning of the page will be left out.

----------------------------------

### Count documents in Latin:

`<document num*<p>*</document>` add escaping:  
`\<document num*\<p\>*\</document\>`

It works otherwise, but the end tags are so broken that it doesn't work.

----------------------------------

TODO: i, add, pope, type, pb, spaces?

### 2023-09-05

Apparently doc 609 is broken in this version too, but now the other way around: `<del>ex¤</del>cons%istente` 

`Iacobo %et commutatione votorum¤` Other in italics, characters not. I think it's equally broken, did the i/add replacements in either order.

#### `<add>`

### 26 Oct 2022 -> 31 Aug 2023 -> 5 Sep 2023
now remaining:  
% 46 pcs 37 37 (were there 9 /'s in the footnotes?)  
¤ 37 pcs 37 37 37  

¤Text added above the line%  
`<add place="above">Text added above the line</add>`

%Text added on the line¤  
`<add place="inline">Text added on the line</add>`

`¤(*)%`  

`<add place="above">\1</add>`  
Replaced by eyeballing, there were a few problem spots. The amount was not hit.

`%(*)¤`  
`<add place="inline">\1</add>`  
Corrected by eyeballing, no issues? The amount was not hit.

n. 3 replaced

Remaining 2023-09-05:  
¤ No results  
% --,,-- 
Good!

Saved 2.1.8

#### `<i>`

`(?)`  
Use wildcard characters  
Font: Italics

`<i>\1</i>`  
106_578 replacements (same)

`</i><i>`  
 (No wildcards or anything else)

`( empty)`  
104_081 replacement (same)

Saved 2.1.9

#### `<pope>`

`(*)^13`  
14 pt

`<pope>\1</pope>^13`
6 replacements, JOHN XXIII corrected by hand.

Saved 2.2.0

#### `<type>`

( Popes and types centered, font size distinguishes)

`(*)`  
font: 10 pt  
Paragraph: centered  

`<type>\1</type>^13`
36 replacements

Saved 2.2.1

#### `<pb>`

`<pb>`  
No special characters

`<pb/>`  
235 replacements

Saved 2.2.2

#### Other notes

`</type>^13(<i>*</i>)^13<doc`  
`\</type\>^13(\<i\>*\</i\>)^13\<doc`  

`</type>^13<jotain>\1</something>^13<doc`  
6 replacements

Oops, the letters became bold, and the paragraph became centered. It follows the formatting of that type of paragraph, I guess.

Many also got a wrong pagination, not all of them.

At some point at the end of p. 4-5, a paragraph-switching-tab-mayhem has been added. A couple of saves earlier? Some accidental presses in Word?

Saved 2.2.3

-------------------------------------------------------------

***READY?***  
*veni, vidi, fini*

-------------------------------------------------------------

### Word save settings: 

*File* - *File* - ... - .txt  

- Character encoding
  - was supposed to be utf-8 by default, but apparently you have to select it manually
- Add line breaks
  - line up the whole text (to the length of the print line?)
- Do not add line breaks
  - Line breaks with paragraph breaks, and ^l's
- Allow character substitution
  - replace curved hyphens with straight ",'; partly good
  - replace dashes with ascii dashes, bad
  - what happens to the crux characters?
    - D. s. †. comes through as irreplaceable

Use:
- character encoding utf-8
- do not add line breaks
- do not allow character substitution


-------------------------------------------------------------

Are all unedited regests now missing the final tags?  
Yes, maybe the correction works just as well in vscode?

(in regex ^ is not)  
`([^>]\n)<doc`  
825 pcs

`$1</regesta>\n</document>\n<doc`  

`([^rv][^>]\n)<doc`  
4 pcs, 1 corrected, the remaining 3 are dot and space or folio format differences.

`([rv][^>]\n)<doc`  
821 (1 corrected)

`([^>])\n<doc`
824 replaced.

-------------------------------------

Single line documents:  
`<document .*\n</document>`  
806 pcs.

`(<document .*)\n<pb/>`  
15 pcs  
`$1</regesta>\n</document>\n<pb/>`  

`(<document .*)\n<pb/>\n<doc`  
A couple were fixed in the previous step, now 6 left.
`$1</regesta>\n</document>\n<pb/>\n<doc`  
Undo messed something up but all 6 replaced.

`(<document .*)\n<pb/>\n`  
5 left, seem to be relevant.

What do you use to find the ones with more lines, e.g. reference numbers before pb?

\d number  
\n line break  
   space  

`[\d\n ]*\n<pb/>`  
235 matches  

`[rv][\d\n ]*\n<pb/>`  
1 match, fixed manually

`([rv]\.[\d\n ]*)\n<pb/>`  
87 matches with this literal '.'  
90 with any char '.'

`$1</regesta>\n</document>\n<pb/>`  


`([rv]\.)([\d\n]*)\n<pb/>`
87 matches

`$1</regesta>\n</document>$2\n<pb/>`  

These also include editions!
Let's fix them first:

`$1</regesta>$2\n<pb/>\n<edition>`

Oh, if it continues `<document>` then there is no edition!

`([rv]\.)([\d\n ]*)\n<pb/>\n<doc`  
68 matches

`$1</regesta>\n</document>$2\n<pb/>\n<doc`  
All replaced (watching hard)

`([rv]\.)([\d\n]*)\n<pb/>`  
16 matches  
Usually `<p>`, sometimes `<pope>` or `<type>` or `</england_wales>`

`$1</regesta>$2\n<pb/>\n<edition>`
`<p>`s replaced, watching.

4 left.

Doc 940 wrong: The footnote anchor was regexed in the [\d\n ] group.  
Fixed.

-----------------------------------------------

**DOc 468: word in the middle of the page change!**
(in regesta)
-----------------------------------------------

`(fol\. [\drv–\.]{0,10}\.)(\n<[^/])`  
16 matches


`$1</regesta>\n</document>$2`  
All replaced. Most were `<type>`, one `<i>`.

--------------

Why was there a `</ument>` at end of doc 82? And 606?  
Fixed.

--------------

Tags on Doc 515 is just a mess, too long?  
Fixed.

--------------

Doc 781 is weird:   
```
Reg. 4, fol. 34r.
7<document num="82">
```
It's like that in the final Word, but ok in v. 1.1. Not checked other versions.

It's the 7 from number of doc 782! Missing also from the doc nr in regesta. Nothing else found with `\d<docu` .  
Fixed.

It's also missing the 781 end tags.  
Fixed.

----------------

pb-type combination @ doc 1142 fixed.


-----------------

`<document`  
1198 matches  
`</document>`  
1234 matches  
Not good.

`</document>\n[^<do]{3}`  
141 matches  
left 100 matches after the following long corrections.

Doc 30: messy page break. 

Is 
```
Premonstraten
sis,
```
OK?
NOK, fixed, by moving the 4 characters to previous page.

Doc 53 similar to previous.  
Doc 78 --,,--  
Doc 87 --,,--  
Doc 118 --,,--  
Doc 150 --,,--  
Doc 422 --,,--  
Doc 426 --,,--  
Doc 432 --,,--  
Doc 450 --,,--  
Doc 452 --,,--  
Doc 456 --,,--  
Doc 474 --,,--  
Doc 485 --,,--  
Doc 487 --,,--  
Doc 492 --,,--  
Doc 518 --,,--  
Doc 596 --,,--  
Doc 618 --,,--  
Doc 629 --,,--  
Doc 636 --,,--  
Doc 682 --,,--  
Doc 704 --,,--  
Doc 712 --,,--  
Doc 715 --,,--  
Doc 718 --,,-- also actual para break   
Doc 720 --,,--  
Doc 727 --,,--  
Doc 732 --,,--  
Doc 750 --,,--  --,,--  
Doc 841 --,,--  
Doc 845 --,,--  
Doc 852 --,,--  
Doc 944 --,,--  
Doc 968 --,,--  
Doc 996 --,,--  
Doc 998 --,,--  
Doc 1037 --,,--  --??--  
Doc 1049 --,,--  
Doc 1076 --,,--  
(why not doc 1077 matched?)  
Doc 1147 --,,--  
xml-extension woke, fixed some add-tags.  
1162 "Phi." Full stop not in italics, del tags around it.
615 pb /edition /doc
625 --,,--

Where is this `<p>` from?  
`<document num="709"><p>709. [Rome]`
`"><p>` There are no others.  
I took it out.  
In the same footnotes: `34 o to` are lower case letters between the footnotes. I took out.  
I had to add the suffixes to the same. And `<regesta>`.

Now it's well formed.

----------------------------

Number of `<edition>`s: 268.

Number of Latin words?
- in `<edition>`
- no notes or deletions?
- yes adds?


-----------------------------

TODO:
- remove footnote anchors (python?)
- `<pb/>`s?
- mark dates
- mark locations?
- remove editionless documents?
- replace ’ -> ' ? And others? †? +?

----------------------------------------------------------------------------

# Volume II

## pdf to docx testing

pdf - Adobe Reader - Copy Ctrl+A, Ctrl+C - Paste to Word: Empty document, Ctrl+V  
Same result as first try, not much formatting.

The edition in Latin are indented in the pdf (eg. doc 1216), but why is it not preserved in the copypaste?

Try number one. Suddenly it looks the same as the previous copypaste, e.g. after a page break the indentation disappears. Should this one have been opened directly in Word?


-----------

Open the **pdf straight in Word, looks much better**: Indentations are there, even after page breaks!

Abbreviations are indented negatively to half out of page, but we are not interested in them?

Page breaks in docx are different from the pdf, and different between the copypaste and straight versions. But the footnotes are then in the middle of the page.

--------------

- (Copypaste Firefox to Word: Only txt comes through, hard linebreaks.)
- (Copypaste Chrome to Word: Only txt comes through, hard linebreaks.)

--------------

pdf in Google Drive -> Open in Google Docs -> Save as docx -> Mostly the same as import straight into Word, font changes to Arial. 

***Except***: There is only 1530 and a half documents! Was the download interrupted or is it just bad?

And what about the automatic numbering?

## Notes about formatting

*(opened-straight-in-Word version)*

The arrow after a document number is not a tab (not found with search \t), what is it? A paragraph setting?  
WARNING: The numbering is automatic, they cannot be edited, they cannot be searched at all! And if one is removed, the others change!

Can they be un-automaticized?  
Yes: https://wordribbon.tips.net/T010248_Converting_Automatic_Numbering_to_Manual_Numbering.html

1. Open the document whose numbering you want to convert. (You may want to open a copy of the document so that you don't mess up the original document.)

1. Press Alt+F11. Word displays the VBA Editor.

1. Press Ctrl+G. This opens the Immediate window. (If you get any other type of dialog box, such as the Find and Replace dialog box, then you aren't working in the VBA Editor; you are still in Word. Close the dialog box, make sure the VBA Editor is active, and then repeat this step.)

1. Type the following in the Immediate window:
  `ActiveDocument.Range.ListFormat.ConvertNumbersToText`

1. Press Enter.

Saved as v. 1.0.2

### symbols

These are the same as Vol I & II:

|symbol | meaning                           |
|-------|-----------------------------------|
|`[ ]`  | *In edited entries:*              |
|       | Text supplied by the editors *or* foliation (Roman)|
|       | Editorial comments on text *or* headings supplied by the editors (italics)|
|       | *In calendared entries:*          |
|       | Text supplied by the editors in English (Roman)|
|       | Latin text supplied by the editors (italics)|
|`[. . .]` | Missing text                   |
|`( )`  | *After the main text in entries printed in full*: |
|       | General editorial comments (italics)|
|       | *In calendared entries*:          |
|       | Original wording (italics) *or* editorial comments (Roman)|
|`\ /`  | Text added above the writing line |
|`/ \`  | Text added on the line            |
|`\\ //`| Text added in the margin          |

### Replacements:

`<`,`>` not found  
`&` 15, of which 3 in regestas and none in editions.  
`/` 104   
`\` 92  
`//` 7  
`\\` 7    
`¤`, `%` Not found  

Should have replaced the slashes before next steps.

Now have to use wildcards: `[!<]/` , escaped as `[!\<]/`


### Font sizes, indentations, etc

How are the page headers and footers saved in `.txt`? Hopefully not at all?

–They are found at the end, luckily, because some of the actual text ended up there! 

### 9 pt:

Footnotes are again at 9 pt. With the anchors at 10 pt.

Long footnotes continue on the next page. Looks quite clean.

Left page: page numbers 9 pt

doc 1276: There is an upper "i" in size 9 pt!
- also doc 1269–1271 "a" and "t".
- 1077?
- 1391 "t"
- 1468 "r"
- 1693 a
- 1708 a
- 1868–1874 ta in Sta
- 2078 "o" 3o inside edition!
- 2102–2107 "ta"
- 2202 "o" in iiio inside edition!
- 2521– Sta
- 2716 "o" in iiiio inside edition!
- 2736– Sta
- 2757 "am" Swaffham (Swafemam)
- 2983–2984 "o" iio inside edition!
- 3189 "o" xxiiio inside edition!



Superscript in footnote is in size 8 pt (note 223, 225 after doc 2546, 234 after 2580)

Superscripts can be found with the Word search tool!
- Can it change the size of all superscripts to eg. 8.5 pt?
  - ss9->ss8.5, ss8->ss7.5?
- or wrap in `<sup>` (TEI)
- maybe both!

doc 2012 at the end there is a centered paragraph:  
Et cum litteris declaratoriis super tertio et quarto gradibus consuetis. Fiat Iul.  
What is it? End of the edition? Something else?

- Same with 2151.
- And 2172.
- 2178
- 2196 at the beginning?
- 2811
- 2867 beginning, clearly part of the edition?
- 3108 --,,--, also, these should not be paragraphs of their own?
- 3132 --,,--
- 3143 --,,--
- 3314 --,,--



### 14 pt

Popes



Use ^& in *find* to add `<i>` tags:
https://wordribbon.tips.net/T012991_Adding_Tags_to_Text.html


## Tags tags

#### Indented edition paragraphs:
`(*)^13`  
Indentation: Left 12.5 pt

`<p>\1</p>^13`  
909 replacements

#### `<type>`:

`(*)^13`  
Bold, Italic, Centered

`<type>\1</type>^13`  
23 replacements

What happened before doc 3363?  
```xml
De perpetuis, ‘Cupientes’, confessionalibus, sententiis generalibus, et altaribus portatilibus284<type></type>
```
Oh yeah, there is no paragraph end (^13) except after the number which is not bold.

Fixed manually.

#### `<pope>`:

`(empty)`  
(No wildcards!)  
14 pt

`<pope>^&</pope>`  
3 replacements

Saved as 1.1.0

#### `<jotain>`:

`(*)^13`  
Not bold, Centered

`<jotain>\1</jotain>^13`  
all replaced. (32/2 = 16 replacements)

Most (all?) of these are actually `<p>`'s.  
Plan: search for `</p><jotain>` and `</jotain><p>` and `</jotain><jotain>` with a proper replacement (`</p><p>` probably).  
Or simply just `<jotain>` -> `<p>`!

Saved as 1.1.1

### Replacements, better late than never

Now use wildcards: `[!<]/` , escaped as  
`[!\<]/`  
`([!\<])/`  

`\1%`  
97 replacements

Check 1422 `\\compartim//`  
Only first / replaced, do it again: 7 replacements. OK

2892: margin note väärin päin (?):  
`quarto %% affinitatis\\ gradibus`

`([!\<])\`  

`\1¤`  

`\` can be replaced straight: 92 replacements

### del, add

doc 1217: del-add close by

`(empty)`  
(No wildcards)  
Overstroke

`<del>^&</del>`  
218 replacements

Saved as 1.1.3  
(1.1.4 accidentally saved on top, tried to remedy using undo. Hopefully worked... seems reasonable.)

Doubles first:  
`\\` eli `¤¤`  
`<add place="margin">`  
7 replacements

`//` eli `%%`  
`</add>`  
7 replacements

doc 2892 fixed manually.

Saved as 1.1.4

-----------------------------

In this case this makes it search only inside one `<p>` paragraph, is there a way to do it inside any paragraph?  
`¤(*)%`  
indentation 12.5 pt

`<add place="above">\1</add>`  
Replaced watching, no problems.

`¤([a-zA-Z ]{1;30})%`  
works (but only for letters and spaces). And seems to require multiple passes. 

`%(*)¤`  

`<add place="inline">\1</add>`  
Korvattu silmällä katsoen, ei ongelmapaikkoja? Lukumäärä meni ohi.

We could also set a maximum length for the match, something like:  
`%(?{1;30})¤`  
Does not limit the length, why?  

(Replace ; -> , in English locale)

Repeat the above searches, and `¤(*)%` and `%(*)¤` until:  
`¤` not found  
`%` 12 in footnotes (are actual /'s.)

Replaced % with /  
12 replacements

Saved as 1.1.5

### TODO: `document`, `edition`, `regesta`, remove 9 pt (add `<pb/>`?), `<i>`, `<sup>`

Can we do a `</document>^l<document num="">`?  
`<type>`s and `<pope>`s end up on the wrong side.

Replace superscript 8,5 / 7,5 pt.   
Add `<sup>`.

### `<sup>`:

`(empty)`  
Font 9 pt, superscript
(no wildcards(?))

`^&`  
Font: 8.5 pt  
55 replacements

Saved as 1.1.6

### Remove footnotes:

`(empty)`  
Font 9 pt  
(no wildcards)

`(empty)`  
852 replacements

Saved as 1.1.7  
(9 pt is left in page headers?)

`(empty)`  
Superscript

`<sup>^&</sup>`  
58 replacements (apparently 3 leftovers in footnotes)

Doc 2221: empty `<sup> </sup>`?!  
Nothing visible in the pdf.

and empty in doc 2222:  
`cessare<sup> </sup>sed `  
There is a smaller space in the pdf.

Both tags and formatting removed.

Saved as 1.1.9

### <document num="">

`^13[0-9]{4}\.`  
seems to find only document numbers.

-------------------------------------

(When `</p>` is overstriked, it's tagged like this:  
```xml
.<del></p>
</del>1617.	Rome
```
There are probably others.)

Just remove all `<del></***></del>` combinations?

`\</del\>[0-9]{4}`  
Finds only doc 1617 in 1.2.1b, `<p>` and `<del>` fixed manually.

-------------------------------------

The doc number search with the ^13 will not find the problem case above.

`([0-9]{4})\.`  
Bold

`</document>^l<document num="\1">\1.`  
2128 replacements

Saved as 2.1.0a

(  
`^13([0-9]{4})\.`  
(No formatting)  
`^13</document>^l<document num="\1">\1.`  
2185 replacements  

Saved as 2.1.0b  
)

Number of documents should be 3408-1199+1 = **2210**

Doc 1673 is [1673] etc. Some are bold, some are not.

`\[([0-9]{4})\]`  
17 matches in b-version  
doc 2177 has the problematic number, [1482] in text

`^13\[([0-9]{4})\]`  
16 matches?! in b-version

--- 1524 not replaced in b-version, why? ---

`\[([0-9]{4})\]`  

`</document>^l<document num="\1">[\1]`  
17 repl

Saved as 1.2.1b

doc 1617 fixed, see above. 

Saved as 1.2.2b

Are we on the right track with the b-version? Comparing 1.2.0a and b crashes Word–no,it doesn't crash, just stutters.  
Differences: 1356, 1414–1430, ***1524*** (after a page break), (***1617*** (after a `</del>`)), 1626, 1734, 1784, 1805, 2203, (25pcs now), 2204–2206, 2210–2215, 2220–2225, 2370, ***2367 error! fixed***, 2472, 2480, 2989, 3011, 3036, 3054, 3081, ***3084 error! fixed***, 3100, 3108–3109, 3112–3115, ***3223 error! fixed***, 3361–3362, 3408 (+36pcs = 61pcs).

Usually the stop is not bold?

but 2185-2128 = 57
1617 makes a difference of 2, what's the other one? 1524 after a page break?

1524, 1617, and erroneous 2367, 3084 and 3223, fixed.

Saved as 1.2.3b 

------------------------

What are the "sought by"s in the page headers?

Removal of footnotes resulted in anchors (on the same line) going together like this:
```
18, fol. 263v.
111112
113
```
------------------------

### TODO: `<edition>`, `<regesta>`, `<pb/>`, `<i>`

#### `<pb/>`

This finds a single line of footnote anchors before a page break:  
`[0-9]{1;}^t^13`  
Replacement would result in:  
```xml
12\t\n<pb/>
13\t\n<pb/>
14\t\n<pb/>

```
Should we do `<pb/>` in vscode? Or is it needed at all?

#### `<edition>`, `<regesta>`

How?

#### `</regesta><edition>`

`([0-9][v|r].)^13\<p\>`  

`\1</regesta>^13<edition>^l<p>`  
385 replacements

Saved as 1.3.0


`([0-9][v|r].)^13\</document\>`  

`\1</regesta>^13</document>`  
1640 replacements

Saved as 1.3.1

1640  
+385  
––––  
2025

`<document num=”[0-9]{4}”>` escaped:  
`(\<document num=”[0-9]{4}”\>)`  

`\1<regesta>`  
2201 replacements

#### `</edition>`

```xml
</p>^13</document>  
    ^
```
`(\</p\>^13)(\</document\>)`  

`\1</edition>^l\2`  
393 replacements

Saved as 1.3.3

#### `<i>`

`(?)`  
Use wc's  
Font: italics

`<i>\1</i>`  
227136 replacements

Saved as 1.3.4

`</i><i>`  
(No wc'c)

`(tyhjä)`  
222173 replacements

Saved as 1.3.5


# vscode

### Quotes

`num=”(\d{4})”`  

`num="$1"`  
2201

`<add place=”above”>`  

`<add place="above">`  
58

`<add place=”margin”>`  
7

`<add place=”inline”>`  
20

`”`  
No results

-----------------------------

## Random fixes 

`<i><type>`De matr...

End regestas, editions, documents...

-------------------------------

Doc 1428: Last paragraph not inside `<p>`. Why?
```xml
<del>Et quod committatur episcopo Lu[n]doniensi vel eius vicario in spiritualibus, cum in diocesi sua moram trahat de presenti et in futuro trahere intendat, et dictum monasterium de Syon sui diocesis existat</del>. Committatur et si, vocatis vocandis, premissa vera esse invenerit et quod exponens ultra in voto non processerit, declaret ut petitur.
```

-------------------------------

End and/or add tags where RedHat xml-extension complains.

Fix ampersand in Doc 1651.

### document reference error in 1818

Inside Doc 1818: `<document num="1805">` in error


Doc 2003 not marked:
```xml
<p>Fiat de speciali et expresso et componat cum datario A. episcopus Lunensis regens.</p>
31

2003	], <i>14 October 1477. Brian Sungleton (</i>recte <i>Singleton?) and </i>
```
The missing `. Rome [at St Peter’s` is in the page header, even in the original .docx! Fix it by looking at the pdf.

Also in doc 2003. `</i>\n<i>` removed.

### document reference error in 2177

Inside Doc 2177: `<document num="1482">` in error

Doc 2524: Indented `<p>` not marked, why?  
Footnote anchors 220 removed from doc 2518 and 2524 (middle of the edition at a page break that was for some reason left out from the xml.)

TODO: 2566 unmarked. Why?
- punkt missing from the number in the .docx (already in the first version)
- pdf has a punkt.
- whatwhy?

fixed. Added the '.'

## 2023-09-13 rest of the end tags

Now it's valid.

`<document num="`  
`<regesta>`  
2201 pcs.

3408-1199+1 = 2210

O-ou! Use python to find missing documents:
```python
for i in range(1199, 3408):
    # exists = is there a `<document num="+str(i)` in the file?
    if not exists:
        # raise hell.
```

`<edition>`  
430 pcs

`<p>`  
911 pcs

`<jotain>`  
16 pcs.

Results from find_missing_docs.py
```
Document 1708 missing. (Missing the dot, added tag and dot.)
Document 1725 missing. (Seems it was the same thing.)
Document 1740 missing. (Same)
Document 1777 missing. (Missing the dot and the paragraph break. In the pdf it looks normal, but MS Word got it wrong.)
Document 2010 missing. (The ". Rome [at St Peter’s" has ended up in the page header. With the dot.)
Document 2017 missing. (Again, ". Rome [at St Peter’s" in the header)
Document 2554 missing. (Missing the dot.)
Document 2581 missing. (Missing the dot.)
Document 2594 missing. (Missing the dot.)
```
(Also removed  
`<sup>tum</sup>`  
in the footnotes after doc 2580  
and notes 223, 225. Tried to find all.)

## Stuff wrongly in the page headers

Check "Remove page headers from the end" (8990abb7)

There are
- 5 missing dots `.`
- 2 `. <i>Rome</i> [<i>at St Peter’s</i>`
- 2 `sought by` 

Only found one sought by in ***1561***, where's the other one?

***1524***!

There are 296 'sought by's in the pdf. And now 294 in the xml, after adding 2. Do we need two more? Or are they in the introduction or footnotes?

The first sought by in the pdf is in doc 1227. So not in intro.

Search the original docx for a 9 pt "sought by", there's only one in note 46.

Compare pdf and xml bisecting:  
***1542*** missing a sought by!

So, 1524, 1542, 1561:  
"sought by" is last words of the first line of the page, after an (automatic?) doc number.

Now the numbers match.


# Volume III

## Documents

Documents number 3409–4085  
677 documents

Open straight in Word.

Remove introductions, 

*Saved as 1.0.0*

Eyeballing the docx, I don't see any weird crap in the page headers (or footers). **But there was at least a point, see 1.1.0!**

Remove indexes from the end. 
- Why is the paging different when pressing `del` at the last content page, before an empty page?
- When selecting the last character and deleting it, the paging does not seem to change?!

*Saved as 1.0.1*

Un-automatic numbers

*Saved as 1.0.2*

Remove empty page 2.

*Saved as 1.0.3*

### symbols

Same as Vol I and II

#### Replace &, /, \

`<`,`>` not found  
`&` 6, of which 1 in regestas and 0 in editions. Replaced with `&amp;`  
`/` 44   
`\` 40  
`//` Not found  
`\\` Not found    
`¤`, `%` Not found  

`/` 44, replaced with `%`   
`\` 40, replaced with `¤`  

*Saved as 1.0.4*

### Font sizes

Are like Vol II:
- Footnotes 9 pt
- Regesta & edition 10 pt
- superscript in edition 9 pt

14 superscripts, none in footnotes.

There is a point in page 168 header (easier to see when 10 pt text is yellow). Where is it from? **3961**?

Again, first line of the page. After an automatic number.

*Saved as 1.1.0*

### Plan:

make superscripts 8.5 pt, add `<sup>`

`(empty)`  
Font 9 pt, superscript
(no wildcards)

`^&`  
Font: 8,5 pt  
14 replacements

Saved as 1.1.6

`(empty)`  
Superscript

`<sup>^&</sup>`  
14 replacements

*Saved as 1.1.2*

### `<p>`

Indentation is again (left, ) 12.5 pt.

<del>

### Remove footnotes:

`(empty)`  
Font 9 pt  
(no wildcards)

`(empty)`  
461 replacements

Saved as 1.1.3  

`(empty)`  
(No wildcards)  
Overstroke

`<del>^&</del>`  
90 replacements

Saved as 1.1.4  

De matrionalibus broken on page 2.
- ok in 1.1.2
- broken with the removal of 9 pt (1.1.3)
- there is a 9 pt paragraph change at the end of Matrimonialibus?!
- same with De diversis before doc 3546!

</del>

#### Fix:

`^13`  
Font: 9 pt

`^13`  
Font: 11 pt  
7 replacements

(The end having a different attribute might prove useful, so change font to 11 pt instead of 10 pt. [***Later observation: most of the parabreaks are 11 pt?!***])

*Saved as 1.1.3 resize...*

### 9 pt Again:

`(empty)`  
Font 9 pt  
(no wildcards)

`(empty)`  
461 -> 445 replacements

(Now it didn't replace the 9 pt in page headers?! Before it did. Circa 9 examples. 445 + 9 + 7 = 461, ok?)

*Saved as 1.1.4 remove...*

### `<del>` again:

`(empty)`  
(No wildcards)  
Overstroke

`<del>^&</del>`  
90 replacements

*Saved as 1.1.5*

### `<add>`:

(No doubles //)

Doc 3472 `<add>` and `<i>` close by

`¤([a-zA-Z ]{1;30})%`

`<add place="above">\1</add>`
(don't know how many, replaced watching.)

`%([a-zA-Z ]{1;30})¤`

`<add place="inline">\1</add>`  
counted 24 replacements, no problems

`%(*)¤`  

`<add place="inline">\1</add>`  
Problems were with '.', '[]', '<>', len > 30, 

`¤(*)%`

`<add place="above">\1</add>`  
2 replacements

`¤`, `%` Not found.

*Saved as 1.1.6*

### `<i>`:

`(empty)`  
Fontti: Kursivoitu

`<i>^&</i>`  
1892 replacements

Looks nice, did not notice any tags ending up in the neighboring parahraph. Or on the wrong side of `<del>` or `<add>` tags.

*Saved as 1.1.7*

### `<p>`:

`(*)^13`  
Indention 12.5 pt

`<p>\1</p>^13`  
452 repl

*Saved as 1.2.0*

`(empty)`  
Bold, Italic, Centered

`<type>^&</type>`  
6 repl.

### Observation P font sizes

The `<type>` paragraph breaks were 9 pt? – I changed them to 11 pt. Now it seems (almost?) all paragraph breaks are 11 pt? Only `<p>`-breaks are 10 pt?

#### `<pope>`:

`(empty)`  
(No wildcards)  
14 pt

`<pope>^&</pope>`  
1 replacement. Yes, there's only one pope in Vol III.

*Saved as 1.2.1*

#### `<jotain>`:

`(*)^13`  
Not bold, Centered

`<jotain>\1</jotain>^13`  
11 repl.

*Saved as 1.2.2*

### `</document><document num="">`:

`([0-9]{4})\.`  
Bold

`</document>^l<document num="\1">\1.`  
638 repl

*Saved as 1.2.3*

(677 needed, 39 missing.)

first and last fixed manually.

`\[([0-9]{4})\]`  
Not found.

`^13([0-9]{4})\.`  
eg. 3578  

`^13</document>^l<document num="\1">\1.`  
35 repl.

These tags became Calibri or Times New Roman non bold.

Still 4 missing. It's easier to find them in vscode/Python.

*Saved as 1.2.4*

### `<regesta>`:

`(\<document num=”[0-9]{4}”\>)`  

`\1<regesta>`  
673 replacements (ok count)

#### `</regesta><edition>`:

`([0-9][v|r].)^13\<p\>`  

`\1</regesta>^13<edition>^l<p>`  
152 replacements

(Missing on page breaks and after eg. "145r–v". Quite good.)

*Saved as 1.2.5*

#### `</regesta></document>`:  

`([0-9][v|r].)^13\</document\>`  

`\1</regesta>^13</document>`  
397 repl.

*Saved as 1.2.6*

#### `</edition>`:  

`(\</p\>^13)(\</document\>)`  

`\1</edition>^l\2`  
193 repl.

*Saved as 1.2.7*

Is it done?

# vscode

### Quotes

`num=”(\d{4})”`  

`num="$1"`  
673

`<add place=”above”>`  

`<add place="above">`  
7

`<add place=”margin”>`  
0

`<add place=”inline”>`  
33

`”`  
No results

Fix order of `<type>` and `</document>`

---------------------
Inside 3749:  
Reference to 3702 erroneously as a document.  
Fixed

3756 --,,--

Doc 3950 untagged. Was missing dot.

3974: paragraph breaks not properly read in Word. Fixed after the pdf.

--------------------------------

Python find_missing_docs.py says:

```
Document 3874 missing. (Dot missing.)
Document 3895 missing. (Dot missing.)
Document 3910 missing. (Dot missing.)
Document 3927 missing. (Dot missing.)
Document 3940 missing. (Dot missing.)
```
First documents of the page in printed volume.

---------------------------------

677 documents, find_missing_docs.py prints nothing. Looks good.

`<edition>` 215 matches

# Statistics

|        |Editions|
|--------|--------|
|Vol I   |    268 |
|Vol II  |    430 |
|Vol III |    215 |
|sum     |    913 |

Finding out how many words there are in the Eng/Wa editions

laiska osumaan

</edition>(\n|.)*?<edition>

| |Words in Latin|
|-|--------------|
|E/W1 | 38027 |
|E/W2 | 56736 |
|E/W3 | 35109 |


# Combine XMLs – plans

*Goal: Combine all data into one xml.*

England Wales is closest to what we want. Transform everything towards that format.

Fix `[<i>recte]` etc to `<add>` tags before combining.

- Editor additions recte
- Editor additions analogical
- inline/overline/margin additions in original
  - `<subst>`
- deletions

e.g:

- `[<i>sic</i>]`
  - There is no correct form
  - https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-sic.html
    - `how <sic>we can</sic> prove`
    
```xml
<choice>
 <sic>we can</sic>
 <corr>can we</corr>
</choice>
```
- `[<i>Bologna</i>]`
- `[<i>recte </i>dispensare]`
- `Maii </i>[recte <i>Aprilis</i>]`
  - sometimes the mistakes are not linguistic...
- `cuius fructus etc. [redditus et proventus] quatuor`
  - what's this? addition?
- `Owyllum [<i>recte </i>Gwyllum]`
- `merentes (?)`



```xml
<root>
<document numHM="123" edition="AP" origNum="15" type="De Natalium / N/A" date="1490-12-25" place="">
<regesta>(optional)</regesta>
<edition>(required)
<p>(required)</p>
</edition>
```

edition="AP" "SP" "EW" / less cryptic  
Auctoritate Papae, Synder og Pavemakt?, ?

The following would perhaps be more TEI like, like a document:
(What format should we aim at? The original Medieval documents? Some of the editions?)

```xml
<penitentiary>
  <document>
    <title><num>123</num>. / <edition>Auctoritate Papae</edition> <origNum>15</origNum>: <diocesis>Nidrosiensis Diocesis</diocesis>
      <date when="1490-12-25">Dec 25 1490</date> <place>Rome</place>, <type>De Natalium</type></title>
    <regesta></regesta>
    <editionText>
      <p></p>
    </editionText>
  </document>
</penitentiary>
```



## Bundle entries
collected_entry="y"

## Add dates to Norway data

```xml
<date when="1523-12-24">24. desember 1523</date>
``` 
OR 
```xml
<num>2</num><date>1523-12-24</date>
``` 
OR
```xml
<num>2</num><date when="1523-12-24"/>
``` 
OR 
```xml
<num>2</num><date when="1523-12-24">1523-12-24</date>
``` 
Needs to be consistent with other editions.


## remove footnote numbers .py

First add `<pb/>` into England Wales II and III

And remember: Vol I has `<pb/>`s without numbers.

`([0-9][\n0-9\t]*\n)`  
Seems to work! At least for EngWal-II  
353 matches

`$1<pb/>\n`  
All replaced in Vol 2.

***Nota bene***: the footnote numbers start again from 1 when pope changes in Vol 2! But not in Vol 3.

In Vol 3:  
177 matches, all replaced.


# Counting words

### EW1:

[('684', 32), ('630', 39), ('687', 41), ('5', 43), ('349', 48), ('1043', 49), 
  . . . 
('474', 461), ('518', 494), ('517', 639), ('515', 797)]

### EW2:

[('2080', 39), ('1377', 50), ('1385', 51), ('3033', 51), ('1380', 52), ('1336', 53), ('2983', 53), ('3039', 54), ('1391', 55), 
  . . . 
 ('2219', 375), ('3112', 375), ('2222', 394), ('3361', 398), ('2221', 424), ('3115', 447)]

### EW3:

[('3944', 38), ('3941', 41), ('3956', 56), ('3954', 58), ('3945', 64), ('3961', 65), 
  . . . 
 ('3578', 436), ('3964', 487), ('3628', 523), ('3974', 565), ('3675', 770)]

### AP:

(Include about 4 words from the title: no, date, place.) 

[('28', 16), ('120', 16), ('139', 17), ('32', 18), ('134', 19), ('38', 20), ('94', 20), ('138', 21), ('111', 22), ('141', 22), ('148', 22), ('429', 22), ('21', 23), ('83', 23), ('30', 24), 
  . . . 
('427', 497), ('232', 500), ('160', 506), ('293', 513), ('439', 518), ('260', 526), ('360', 640), ('22', 718), ('234', 748), ('279', 903), ('437', 1182), ('300a&b', 1267), ('372a&b', 1713)]

#### `<version>`:

22  
length = 226  
length = 486  
60  
length = 94  
length = 279  
88  
length = 122  
length = 25  
279  
length = 411  
length = 486  
300  
length = 566  
length = 695  
372  
length = 420  
length = 1285  <--- Winner!  
437  
length = 478  
length = 698  

### SP:

[(1, 28), (6, 31), (43, 31), (118, 31), (130, 32), (63, 34),
  . . . 
 (16, 406), (45, 430), (29, 458), (80, 483), (71, 517), (78, 582), (76, 587), (86, 587), (84, 772)]


## 27.6.2024 Plan Auctoritate bundles

Now:
```xml
<text n="13" source="AP" onum="13" to_num="15" type="FIXME" bundle="y" several_wittnesses="n">
<front>
<docDate><date when="1448-02-04"/><placeName type="place-issue">Rome</placeName></docDate>
</front><body>
<lb onum="13">13</lb><p>Supplicatur sanctitati vestre pro parte devoti vestri Nicolai Laurentii
clerici Upsalensis diocesis, quatenus non obstante defectu natalium,
quem patitur de presbytero genitus et soluta, dignetur sanctitati vestri
ut supra. Fiat de speciali. Dominicus sancte Crucis.</p>
<lb onum="14">14</lb><p>Similiter dispensatum est Erico Mathie clerico Upsalensis diocesis
simili defectu non obstante.</p>
<lb onum="15">15</lb><p>Similiter Iohanni Mathie clerico Upsalensis diocesis simili defectu
non obstante.</p>
</body>
</text>
```

Get rid of `<lb>`? and the text number `>13<`

Possible TEI tags: div, group, ...?

## 3.7.2024 Protocol, context, escatocol

This is the only google hit:

https://books.google.fi/books?id=wgCKSlhpd90C&lpg=PA119&ots=vuSB66oFDb&dq=tei%20xml%20protocol%20escatocol&hl=fi&pg=PA119#v=onepage&q=tei%20xml%20protocol%20escatocol&f=false
https://books.google.fi/books?id=wgCKSlhpd90C&pg=PA119&lpg=PA119&dq=tei+xml+protocol+escatocol&source=bl&ots=vuSB66oFDb&sig=ACfU3U3J4xgB3WKI8I3l9GNFcihic0wcAg&hl=fi&sa=X&ved=2ahUKEwiIrei2h4uHAxVxLBAIHWcwC98Q6AF6BAgFEAM#v=onepage&q=tei%20xml%20protocol%20escatocol&f=false

```xml
<text>
  <front>
    <div type="regest" xml:lang="deu">
      <byline>interpoliert</byline>
      <p>Patriarch Pilgrim [I.] von Aquileia bestätigt die Übergabe des Eigengutes Oberburg
        durch den Edlen Diepold von Kager und dessen Frau Truta an die Kirche von Aquileia,
        dotiert mit einem Teil dieses Besitzes das Benediktinerkloster Oberburg, 
        ...</p>
    </div>
  </front>
  <body xml:lang="lat">
    <div type="protocol">
      <div type="invocatio">In nomine patris et filii et spiritus sancti ...</div>
      <div type="intilutatio">Idcirco nos Peregrinus dei gratia sancte ...</div>
      <div type="arenga">Quoniam universis maxime ecclesiarum prelatis in ...</div>
    </div>
    <div type="context">
      <div type="publicatio">notum esse volumus omnibus Christum ...</div>
      <div type="narratio">qualiter Dyebaldus nobilis quidam de Chagere ...</div>
      <div type="dispositio">allodium suum Obbemburch sicut et ipsi ...</div>
      <div type="sanctio">Preterea interdicimus ne aliquis eiusdem ecclesie ...</div>
    </div>
    <div type="escatocol">
      <div type="subscriptiones">Huius igitur donationis testes sunt ...</div>
      <div type="datatio">Actum est hoc Aquilegie ..</div>
    </div>

  </body>
</text>

```

