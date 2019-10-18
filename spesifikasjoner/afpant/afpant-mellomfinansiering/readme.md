# Sikkerhet ved mellomfinansiering

Når bank trenger sikkerhet i kjøpers eksisterende bolig benyttes enten tinglysing av pant eller transporterklæring.
En transporterklæring tar ikke sikkerhet i oppgjøret, men gir megler fullmakt/ansvar for å utbetale egenkapital til banken med begrensning oppad til nettoprovenyet.
Gjennom å definere meldinger som kan flyte mellom bank og megler skal vi kunne digitalisere denne prosessen.

## Samtykke til tinglysing
Å tinglyse pant i grunnboken gir best sikkerhet, men har noen utfordringer.
* Megler kan ha tatt, eller være på vei til å ta, sikkerhet i eiendommen. Kjært barn har mange navn; Urådighet/Sikringsobligasjon/”AH_URK”

Utfordringen i dagens prosess, på papir, er at det tar lang tid på grunn av treg postgang. Dette gjelder både forsendelsen til Kartverket for pantedokumentet og forsendelsen til megler for påføring av samtykke.

Hypotesen er at digital prosess i stor grad vil eliminere utfordring med tidsaspektet. Det vil da bli enkelt å innhente samtykke på pantet og tinglyse dette for banken.
Hvor stor andel vil dekkes av digitalt samtykke til tinglysing?

## Transporterklæring
Dersom det blir vanskelig eller ikke ønskelig å etablere sikkerhet i grunnboken, benyttes transporterklæring.
Denne kan sees på som en avtale på linje med pantedokumentet som ikke tinglyses.

En transporterklæring gir megler fullmakt til å transportere nettoprovenyet til bankens ved oppgjør.
Banken ønsker en bekreftelse på at de får overført egenkapital fra gammel bolig, megleren svarer ofte ok, men en begrensning oppad til nettoproveny

Utfordringen med transporterklæring er:
* Megler ønsker ofte å ta egne forbehold, og vil aldri gå med på noe annet enn å utbetale nettoprovenyet til banken.  
* Megler må ikke miste denne avtalen!
* Det blir ikke synlig i grunnboken hvem som er kreditor

## Forslag til løsning
Løsningen for å samtykke til tinglysing er vesentlig enklere å implementere enn transporterklæring. Det er sånn sett mulig å dele arbeidet inn i to faser. 

### Fase 1: Samtykke til tinglysing

#### Flyt 
0. Bank sjekker om megler kan samtykke til tinglysing digitalt i AKELDO, dersom ja:
1. Bank oppretter pantedokument og får det signert av kunden
2. Bank sender signert pant til megler på kjøpers eksisterende bolig
    * En SDO med det digitalt signerte pantedokumentet fra kjøpers bank
    * Metadata (xml+xslt)i henhold til spesifikasjonen (@todo)
3. Megler svarer
    * Samme SDO som ble mottatt med påført signatur fra rettighetshaver (happy path). Signatur kan være av typen virksomhetssignatur eller personlig signatur fra signaturberettigede. 
    * Metadata (xml+xslt)i henhold til spesifikasjonen (@todo). Håndterer ev. feilmeldinger dersom alternativ flyt forekommer.
4. Bank sender dokumentet, med samtykke fra megler, til tinglysing som vanlig

Se [her for tekniske detaljer](afpant-samtykke-til-tinglysing-1-0-0.md)

### Fase 2: Transporterklæring

For transporterklæring må vi trolig definere et standardformat som alle kan benytte, som må kunne benyttes i signeringsprosesser og vises til kunden på en enkel måte.
Her må vi diskutere hvordan og om det er mulig å komme frem til et omforent format, og juss og sikkerhet må vurderes. 

#### Flyt
0. Banken sjekker om megler kan samtykke/motta transporterklæring digitalt i AKELDO, dersom ja:
1. Bank oppretter transporterklæring og får det signert av kunden
    * Mulig å benytte signert xml+xslt med BankID, eller PDF og strukturerte data ved siden av?
2. Bank sender signert transporterklæring til megler på kjøpers eksisterende bolig
    * En SDO med transporterklæring fra kjøpers bank til eiendomsmegler på kjøpers eksisterende bolig
    * Metadata (xml+xslt)i henhold til spesifikasjonen. Håndterer ev. feilmeldinger etc. 
3. Megler svarer 
    * Enten som påført signatur på mottatt SDO, eller som et eget signert, nytt, dokument som representerer hva megler forutsetter
    * Metadata (xml+xslt)i henhold til spesifikasjonen. Håndterer ev. feilmeldinger etc.
4. Bank beholder signert transporterklæring-svar som grunnlag for en eventuell regfull dag (at megler ikke utbetaler i henhold til avtale).
5. Når utbetaling skjer vil megler benytte transporterklæringen på lik linje med restgjeldssvar til å utbetale i henhold til avtale.
    * Må det forespørres om restgjeld på en transporterklæring, eller kan man forvente at beløpet ikke endrer seg i perioden? (Under forutsetning at salgssum dekker hele beløpet, selv om nettoprovenyet er avtalt)





