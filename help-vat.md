---
---
# Eesti käibemaksu aruanne - kasutusjuhend
Antud funktsionaalsus võimaldab teil koguda vajalikke andmeid põhideklaratsiooni (vorm KMD) ja deklaratsiooni lisa (vorm KMD INF) jaoks ning esitada need XML-failivormingus.

## Kuidas koguda andmeid käibemaksuarunde jaoks
Funktsiooni KM väljavõtted abil saate väljavõtte põhjal eeltäita käibemaksu põhiaruande. Peate määratlema seosed KM väljavõtte ja käibemaksu aruande väljade vahel.

Avage **KM väljavõtted** ja muutke väljavõtet mida soovite aruandluseks kasutada. Saate valida iga KM väljavõtte rea kohta, kas eksportida rea tulemus KM aruandesse.
Selleks sisestage väljale **Lahtri nr.** vastav käibemaksu põhideklaratsiooni rea number. Kui lahkute välja või rea pealt, näete deklaratsiooni rea kirjeldust väljal **Lahtri kirjeldus**. 
Nõuanne: klõpsates väljal **Lahtri kirjeldus** avanevad kõik käibemaksu aruande read mida kasutada saate.

### Autode arv
Lisaks rahalistele väärtustele on käibedeklaratsiooni põhiaruandes kaks kogustüüpi välja:
* Äriotstarbel kasutatud autode arv (100%)
* Osaliselt ärilistel eesmärkidel kasutatud autode arv
Nende väljade eeltäitmiseks uutel deklaratsioonidel avage **KM aruande seadistus** ja lisage andmed vahekaardil **Eesti KM aruanne**.

## Kuidas koguda andmeid käibemaksuaruande lisa jaoks
Avage **KM aruande seadistus** ja vahekaardil **Eesti KM aruanne** seadistage järgmised väljad:
* Esitatav tehingupartner - valige, milliseid osapooli deklaratsioonis kasutatakse:
    * * Makse saaja hankija/Maksja klient*
    * * Müüja hankija/Ostja klient *
    * * Müüja hankija/Ostja klient (ainult KM reg. nr. olemasolul) * - selle valikuga kasutatakse Müüja hankija/Ostja klient juhul kui neil on **KM reg. nr.**, vastasel juhul kasutatakse Makse saaja hankija/Maksja klienti.
* Piirmäära summa - sisestage 1000.   
 
Andmed KM aruande lisa jaoks kogutakse **KM kanded** loendist. Õigete andmete kogumiseks vajalike tingimuste seadistamiseks avage **KM konteerimise seadistus**.

Iga käibemaksupõhise postitusgrupi kombinatsiooni jaoks saate määratleda, kas selle kombinatsiooniga postitatud tehing tuleb esitada või mitte, ning seadistada vajalikud eripärad.

Deklareeritavate ja mitte deklareeritavate tehingute automaatseks eraldamiseks tuleb tehingud postitada erinevate käibemaksukohustuslaste gruppidega. Tehingud, mida tuleb kirjeldada eranditena, tuleb postitada ka eraldi käibemaksukohustuslaste gruppidega.

Näited:
1. Tehingud ettevõtetega tuleb deklareerida ja tehinguid eraisikutega ei pea deklareerima. Seetõttu peaksid eraisikutest kliendid ja müüjad olema loodud eraldi **KM äri konteeringurühm** väärtusega (näiteks *MITTE KM KOHUSLANE*).
2.Kui arve(d) esitatakse ametialaste teenuste eest, mida seaduse ees käsitletakse kui konfidentsiaalseid, siis neid tehinguid ei pea deklareerima ja nende teenuste müük tuleks konteerimise peaks olema eraldi **KM toote konteeringurühm*.

Märkige linnuke **KMD INF-il ei deklareerida** nendele ridadele **KM konteerimise seadistuses**, mille tehinguid ei pea deklareerima. Ridadele, kus **KM %** on null, ei pea te **KM konteerimise seadistuses** linnukest panema - need tehingud välistatakse automaatselt.

Muutke **KM konteerimise seadistuses** neid ridasid millele te tahate seada erisusi. Valige erisuse kood väljal **KMD erisus müügil** või **KMD erisus ostul**. Erisust '03' ei pea, ega saagi lisada - see erisus lisatakse automaatselt kui müügiarvel on ridu nii käibemaksuga kui ilma.

## Kuidas luua käibemaksuaruannet
Avage **KM tagastused(KMD)**, looge uus aruanne, määrake **Nr.** ja valige **Versioon** 'EST'.

### Andmete saamine
Andmete saamiseks aruandesse käivitage toiming **Soovita ridu**, valige kasutatav KM aruanne ja periood.

Funktsioon täidab KM deklaratsiooni aruande ridadel andmed (kui olete seadistanud eelmistes jaotistes kirjeldatud seosed) ja INF lisad all väljad **INF-A read** ja **INF-B read**.

**INF-A read** ja **INF-B read** ülevaatamiseks, klõpsake rea väärtusel.

Vajadusel saate manuaalselt lisada andmeid. Kui tahate näha mõne müügi või ostu kande detaile lisades, võite kasutada funktsiooni **Navigeeri**.

### Registreerimisnumbrite kontrollimine ja täitmine
Tehingupartneri nime kasutatakse deklaratsiooni kui tehingupartneri registreerimisnumber puudub. Võimalike tuvastamisprobleemide vältimiseks (nimi BC-s erineb veidi maksuameti andmebaasis olevast nimest) on soovitatav täita registreerimisnumbrid BC-s (kliendi/hankija kaardil).Puuduvate registreerimisnumbritega tehingupartnerite loendi vaatamiseks klõpsake lisadel **Reg.numbrita kliendid** või **Reg.numbrita hankijad**.

Puuduvate registreerimisnumbrite automaatseks täitmiseks võite mõlema lisaga kasutada funktsiooni**Uuenda andmed äriregistrist**. Pärast uuenduse jooksutamist, sisaldab nimekiri neid tehinguparntereid keda ei leitud äriregistrist. Muutke neid kliente/hankijaid ükshaaval kasutades funktsiooni **Päri äriregistrist** ja määrates otsitava ettevõtte nime.

## Deklaratsiooni esitamiseks XML-faili loomine
Märkige linnuke **Teata kõigist tehingutest**, kui soovite lisada nende tehingupartnerite arveid, kelle tehingute kogusumma jääb alla limiidi (1000 €).

Aruande XML-faili salvestamiseks klõpsake **Loo**. Laadige fail üles ja esitage E-maksuametis.

---
## Business Centrali konteeringute nõuded:
1. Konteeritud KM kanded on kohustuslikud kuna KM aruande lisade andmed põhinevad KM kannetel. Nõuet 1 toetab nõuete 2 ja 3 järgimine.
2. Tehingud tuleb konteerida kliendi ja müüja kaarte kasutades. Kliendikaartide ja hankijakaartide andmed peavad vastama nende tehingupartnerite tegelikule ettevõtteteabele.
3.Tehingud tuleb konteerida arve või kreeditarvena või peažurnaali kandena, kui dokumendi tüübiks on määratud arve või kreeditarve.
4. Deklareeritavad / deklareerimata tehingupartnerid tuleb luua koos erinevate käibemaksuga ettevõtluse postitusgruppidega. See võimaldab teil käibemaksu konteerimise seadistuses määratleda käibemaksu kirjendamise rühmade kombinatsioonid, mis tuleb deklareeritud andmetest välja jätta.
5. The items/services to be declared / not to be declared must be set up with different VAT Product Posting Groups. That allows you to define the combinations of VAT posting groups in VAT Posting Setup, which have to be excluded from the declared data.
6. Deklareeritavad / deklareerimata kaubad / teenused tuleb seadistada koos erinevate KM toote konteerigurühmadeg. See võimaldab teil KM konteerimise seadistuses määratleda käibemaksu kirjendamise rühmade kombinatsioonid, mis tuleb deklareeritud andmetest välja jätta.
7. Volitatud töötajate esitatud kuludokumendid tuleks üles panna ostuarvetena.
8. Ettemaksude deklareerimiseks peate konteerima ja väljastama ettemaksuarve(d), kuna käibedeklaratsiooni lisa põhineb arvete andmetel, mitte maksetel.
9. Et lisada ettemaksuarve deklaratsiooni alles pärast selle tasumist, peate kasutama BC funktsiooni Ettemakse realiseerimata käibemaks.
