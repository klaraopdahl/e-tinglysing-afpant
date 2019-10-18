# Forspørsel om samtykke til tinglysing

[Les mer om bakgrunnen for meldingen her](readme.md)

Forespørsel sendes fra bank til megler for å innhente samtykke til tinglysing.
Det forventes at positivt svar levers som definert under.

## Forespørsel om samtykke

### Manifest
(BrokerServiceInitiation.Manifest.PropertyList)

|Manifest key|Type|Required|Beskrivelse|
|--- |--- |--- |--- |
|messageType|String|Yes|ConsentForRegistrationRequest|

### Payload
En ZIP-fil som inneholder 
  * XML med requestdata ihht. [definert skjema](../afpant-model/xsd/dsve-1.0.0.xsd)?
  * SDO (Signed Data Object) av pantedokumentet

#### Om payload *(request)*
- En xml-fil som er i henhold til xsd-filen?
- Se eksempel på presentasjon @todo Ikke definert enda

##### Model
- @todo Ikke definert enda

## Samtykke til tinglysing (svar)
Svar fra bank til megler.

### Manifest
(BrokerServiceInitiation.Manifest.PropertyList)

|Manifest key|Type|Required|Beskrivelse|
|--- |--- |--- |--- |
|messageType|String|Yes|ConsentForRegistrationResponse|

### Payload
En ZIP-fil med pantedokument påført digitale signaturer fra rettighetshaver (virksomhet eller ihht. Enhetsregisteret)
		
#### Om payload *(response)*

##### Positiv resultat
- Må være en xml-fil som er ihht. [definert skjema](../afpant-model/xsd/dsve-1.0.0.xsd)?
- Se eksempel på presentasjon @todo Ikke definert enda

##### Model
- @todo Ikke definert enda

##### Negativt resultat
- @todo:Må definere hvor ack/navk-informasjon skal legges

## Eksempel

### Forespørsel
@todo Ikke definert enda

### Svar
@todo Ikke definert enda
