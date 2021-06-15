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

Examples:
1. Transactions with companies have to be declared and transactions with private persons do not have to be declared.  Therefore, the customers and vendors who are private persons, should be posted with separate **VAT Business Posting Group** (e.g. *PRIVATE*)
2. When invoice(s) is/are issued for professional services which are treated as confidential by the laws, those transactions do not have to be declared and the sale of those services should be posted with separate **VAT Product Posting Group**.

Place a check mark to the **KMD No Declarating on INF** to those **VAT Posting Setup** lines, of which transactions do not have to be declared. You do not have to place a check mark to the **VAT Posting Setup** lines where **VAT %** is zero – those transactions will be excluded automatically.

Edit the **KM konteerimise seadistus** lines where you want to set up specialities. Select the speciality code to the field **KMD Speciality on Sale** or **KMD Speciality on Purchase**. Specialty '03' does not have to be and cannot be set up – this specialty will be added automatically if sales invoice has lines with VAT and also lines without VAT.

## How to create VAT Report
Open **VAT Reports** (or **VAT Returns**), create a new report, assign **No.** and choose 'EST' for **Version**.

### Getting the data
To get the data to the report, run the action **Suggest Lines** and choose the VAT statement to use and a period.

The function fills the VAT declaration data on the report lines (if you have set up the relations described in previous sections) and VAT declaration appendixes under the fields **INF-A Lines** and **INF-B Lines**.

To review the **INF-A Lines** and **INF-B Lines**, drilldown on these fields.

If needed, you can manually add data. When you want to see the details of some sales or purchase transaction on the appendixes, you can use **Navigate** function.

### Checking and completing of Registration numbers
Transaction partner name is used on the declaration if transaction partner registration number is missing. However, to prevent possible identification problems (name in BC is slightly different from the name in Tax Office database) it is recommended to fill in registration numbers in BC (on customer/vendor card). To review the list of the transaction partners with missing registration numbers, click on the appendixes **Customers without Reg. No.** or **Vendors without Reg. No.**

In order to automatically complete the missing registration numbers, you can use the function **Update Data from Business Register** in both lists. After running the update, the lists will contain those transaction partners who were not found in Business Register. Edit those customers/vendors one by one, by running function **Query from Business Register** and specifying the company name to search.

## Creating the XML file for submitting the declaration

Place the check mark **Report All Transactions** if you wish to include the invoices of those transaction partners, whose transactions total amount is below the limit (1000€).

Click **Generate** to save the report into XML file. Upload and submit the file in E-Tax Board.

---
## Requirements for postings in Business Central:
1. Posted VAT Entries are required, because VAT report appendix data is based on VAT Entries. The requirement 1 is supported by following the requirements 2 and 3.
2. Transactions must be posted, using customer and vendor cards. The data of customer and vendor cards has to match the actual company information of those transaction partners.
3. Transactions must be posted as invoice or credit memo, or from the General Journal, when document type is defined as Invoice or Credit Memo.
4. The transaction partners to be declared / not to be declared must be set up with different VAT Business Posting Groups. That allows you to define the combinations of VAT posting groups in VAT Posting Setup, which have to be excluded from the declared data.
5. The items/services to be declared / not to be declared must be set up with different VAT Product Posting Groups. That allows you to define the combinations of VAT posting groups in VAT Posting Setup, which have to be excluded from the declared data.
6. The expense documents submitted by authorized employees should be posted as purchase invoices.
7. In order to declare prepayments, you must post and issue prepayment invoice(s), because the appendix of VAT Declaration is based on invoicing information and not payments information.
8. In order to include prepayment invoice in declaration only when it has been paid, you have to use BC functionality Prepayment Unrealized VAT.
