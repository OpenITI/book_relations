# book_relations

- Relations between books are indicated in OpenITI in the field `40#BOOK#RELATED##` in the book YML files. 

- Please write the URI of the related book (or author, if no specific book is known or existed) in that field, 
and indicate its relationship with the YML's book between brackets (for codes for specific relations, see below). 

  E.g., to express that al-Ṣafadī's Ghayth al-Musajjam is a commentary on al-Ṭughrā'ī's Lāmiyyāt al-ʿAjam:

  ```
  00#BOOK#URI######: 0764Safadi.GhaythMusajjam
  ...
  40#BOOK#RELATED##: 0513Tughrai.LamiyyatCajam (COMM.sharh)
  ```

- If the book is not in the corpus, you can use the author and title instead of the URI (put them between square brackets, e.g., `[Porphyry, Isagoge]`).

- Use semi-colons to separate related books, e.g.:

  ```
  00#BOOK#URI######: 0625AnonComp.Juz
  ...
  40#BOOK#RELATED##: 0607IbnTabarzad (COMP.juz); 
      0604SittKataba (COMP.juz)
  ```

- In order to make updating book relations as easy as possible, we list relationships only on book-to-book basis,
and only in the yml file of the most recent book of each pair. 

- If you want to express more complex chains of relationships between books, please split them into pairs. 

  E.g., Ibn Muḥammad Ḥusaynī’s *Ṣilat al-takmila*, which is a continuation of Ibn al-Mufaḍḍal al-Muqaddasī’s *Wafayāt al-naqala*. Ibn al-Mufaḍḍal al-Muqaddasī’s work on its part is a dhayl to Ibn al-Akfānī’s continuation (*Dhayl dhayl tārīkh Mawlid al-ʿulamāʾ wa-wafayātihim*) of ʿAbd al-ʿAzīz al-Kattānī’s continuation (*Dhayl tārīkh Mawlid al-ʿulamāʾ wa-wafayātihim*) to Abū Sulaymān al-Rabʿī’s [=Ibn Zabar] *Tārīkh Mawlid al-ʿulamāʾ wa-wafayātihim*. 

  * In book yml file `0695IbnMuhammadHusayni.SilatTakmilaLiWafayatNaqala.yml`:

  ```
  00#BOOK#URI######: 0695IbnMuhammadHusayni.SilatTakmilaLiWafayatNaqala
  ...
  40#BOOK#RELATED#: 0611IbnMufaddalSharafDinMuqaddasi.WafayatNaqala (CONT.dhayl)
  ```

  * In book yml file `0611IbnMufaddalSharafDinMuqaddasi.WafayatNaqala.yml`:

  ```
  00#BOOK#URI######: 0611IbnMufaddalSharafDinMuqaddasi.WafayatNaqala
  ...
  40#BOOK#RELATED#: 0524IbnAkfani.DhaylDhaylTarikhMawlidCulama (CONT.dhayl) 
  ```

  * In book yml file `0524IbnAkfani.DhaylDhaylTarikhMawlidCulama.yml`:

  ```
  00#BOOK#URI######: 0524IbnAkfani.DhaylDhaylTarikhMawlidCulama
  ...
  40#BOOK#RELATED#: 0466CabdCazizKattani.DhaylTarikhMawlidCulama (CONT.dhayl) 
  ```

  * In book yml file `0466CabdCazizKattani.DhaylTarikhMawlidCulama.yml`:

  ```
  00#BOOK#URI######: 0466CabdCazizKattani.DhaylTarikhMawlidCulama
  ...
  40#BOOK#RELATED#: 0379MuhammadRabci.TarikhMawlidCulama (CONT.dhayl) 
  ```

  A script will assemble these links and collate the full chain of transmission.
  
- if a book relation falls into more than one category, add more than one category between the brackets, separated by commas.

  E.g., `40#BOOK#RELATED#: 0379MuhammadRabci.TarikhMawlidCulama (CONT.dhayl, ABR.mukhtasar)`
  
- 

## List of the codes for types of relations between books/authors:
The main categories are in all-caps, subcategories in lower case. Subcategories can be used to represent the Arabic terminology used for the type of book relations.

NB: some of the Arabic terms can be used for quite different phenomena (e.g., takhrīj); the terms that are mentioned under more than one main category are highlighted in the table.

### ABR
The current work is an abridgement of work A

Subcategories:

* ABR.muhadhdhab
* ABR.tahdhib
* ABR.mulakhkhas
* ABR.talkhis
* ABR.wajiz
* ABR.mujaz
* ABR.mukhtasar
* ABR.ikhtisar
* ABR.<mark>ikhtiyar</mark>
* ABR.khulasa
* ABR.muqtasar
* ABR.iqtisar
* ABR.muqtadab
* ABR.nazm

### COMM
The current work is a commentary of work A / the words of person A

Subcategories:

* COMM.hashiya
* COMM.sharh
* COMM.tafsir
* COMM.<mark>takhrij</mark>
* COMM.nukat
* COMM.tawdih
* COMM.tacliq
* COMM.radd

### COMP
The current work is a compilation of work A / words of person A

Subcategories:

* COMP.muntaqa
* COMP.<mark>ikhtiyar</mark>
* COMP.muntakhab
* COMP.<mark>takhrij</mark>
* COMP.khulasa
* COMP.juz
* COMP.mashyakha
* COMP.thabat
* COMP.barnamaj
* COMP.tasmiya
* COMP.sualat
* COMP.diwan


### CONT
The current work is a continuation of work A

Subcategories:

* CONT.takmila
* CONT.takmil
* CONT.tadhyil
* CONT.dhayl
* CONT.sila
* CONT.tali
* CONT.mustadrak
* CONT.tamam

### TRANSL
The current work is a translation of work A

Subcategories:

* TRANSL.paraphrase

### TRANSM
The current work transmits work A / words of person A

Subcategories:

* TRANSM.riwaya


# ADDENDUM: Suggestion for update (MGR)

For AUTHOR YAML:

`40#AUTH#RELATED##: teacher_of@0771Subki`

- all relationships are described in this field; tags describe the relationship of the main author to other people. In the example above, taken from `0748Dhahabi`, the record says `0748Dhahabi@teacher_of@0771Subki` (the first part of the triple is dropped, as it is derived from the record itself).
- the same format might be efficient for BOOK YML.

## Example of AUTHOR Template

```
00#AUTH#URI######: XXXShuhra (autoupdated)
10#AUTH#ISM####AR: Fulān
10#AUTH#NASAB##AR: b. Fulān b. Fulān b. Fulān b. Fulān
10#AUTH#KUNYA##AR: Abū Fulān, Abū Fulānaŧ
10#AUTH#LAQAB##AR: Fulān al-dīn, Fulān al-dawlaŧ
10#AUTH#NISBA##AR: al-Fulānī, al-Fāʿil, al-Fulānī, al-Mufaʿʿil
10#AUTH#SHUHRA#AR: Ibn Fulān al-Fulānī
10#AUTH#DESCRIPT#: Essentially, for nisbaŧs, but those that are not given
  in the sources in their Arabic forms (like poet, historian, biographer, etc.)
20#AUTH#GEOGRAPH#: born@AlthurayyaURI, died@AlthurayyaURI, visitied@AlthurayyaURI, resided@AlthurayyaURI
30#AUTH#DATES##AH: born@YEAR_MON_DA, died@YEAR_MON_DA (X+ for unknown)
40#AUTH#RELATED##: relation_type@AUTH_URI, comma separated
80#AUTH#BIBLIO###: src@id, src@id, src@id, src@id, src@id
90#AUTH#COMMENT##: a free running comment here; you can add
  as many lines as you see fit; the main goal of this comment
  section is to have a place to record valuable information,
  which is difficult to formalize into the above given categories.
99#AUTH#RESTATUS#: not finished
```
## Example of BOOK template

**NB:** Perhaps, fields MSS, EDITIONS, TRANSLAT, STUDIES, LINKS can be merged in the same manner as well?

```
00#BOOK#URI######: XXXShuhra.IsmKitab (autoupdated)
10#BOOK#TITLEA#AR: Kitāb al-Muʾallif
10#BOOK#TITLEB#AR: Risālaŧ al-Muʾallif
10#BOOK#GENRES###: src@keyword, src@keyword, src@keyword
20#BOOK#GEOGRAPH#: written@AlthurayyaURI, finished@AlthurayyaURI, comma separated
30#BOOK#DATES##AH: written@YEAR_MON_DA, finished@YEAR_MON_DA (X+ for unknown)
50#BOOK#RELATED##: relationship@BookURI
80#BOOK#MSS######: permalink, permalink, permalink
80#BOOK#EDITIONS#: permalink, permalink, permalink
80#BOOK#TRANSLAT#: permalink, permalink, permalink
80#BOOK#STUDIES##: permalink, permalink, permalink
80#BOOK#LINKS####: permalink, permalink, permalink
90#BOOK#COMMENT##: a free running comment here; you can add
  as many lines as you see fit; the main goal of this comment
  section is to have a place to record valuable information,
  which is difficult to formalize into the above given categories.
99#BOOK#TITLE####: Title of the work for book/website (most commonly used title)
99#BOOK#RESTATUS#: not finished
```


