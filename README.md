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









