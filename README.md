Opdracht: Doe een WCAG test op een bestaande website en rapporteer daarover.

## Titel Website

Ik heb website van de restaurant Oficina in Amsterdam getest. De website is kleurrijk en dynamisch, is beschikbaar in 2 versies - gekleurd en zwart-wit. De website bevat een menu met informatie, dynamische plaatje op achtergrond dat met de cursor meebeweegd en adresgegevens op de home pagina. 


<img width="1470" alt="image" src="https://github.com/aliceafanasieva/all-human-wcag-audit/assets/66431299/8da7d4ea-2a1a-4d33-85c2-e5bd5d360776">

## Resultaat van Lighthouse Accessibility Audit:

<img width="625" alt="image" src="https://github.com/aliceafanasieva/all-human-wcag-audit/assets/66431299/992d2df8-a573-4e86-9f00-6f2bbfbb2782">

### Problemen

1.  > **Image elements do not have `alt` attributes.** 

**Regel**

Alle afbeeldingen moeten alternatieve tekst bevatten om hun doel en betekenis over te brengen aan gebruikers van schermlezers.

**Oplossing**

Zorg ervoor dat alle informatieve `<img>`-elementen korte, beschrijvende alternatieve tekst hebben en dat alle decoratieve `<img>`-elementen lege alt-attributen hebben (bijvoorbeeld `alt=""`).

**Waarom belangrijk?**

Zodat de screen reader gebruikers het idee kunnen krijgen over de inhoud en doel van de afbeelding op de website. 


2.  > **Links do not have a discernible name.** 

**Regel**

Linktekst (alternatieve tekst voor `<img>`-elementen bij gebruik als links) moet herkenbaar zijn voor een schermlezer, mogen geen dubbel label hebben en moeten focusbaar zijn. Dat zorgt ervoor dat elke link een toegankelijke naam heeft.

**Oplossing**

Gebruik maken van `[aria-label]` element bij het beschrijven van de link betekenis in HTML zoals in onderstaande code:

`<a href="taxhike.html" aria-label="Read more about Seminole tax hike">[Read more...]</a>`

**Waarom belangrijk?**
Ontoegankelijke linkelementen maken een obstakel voor de toegankelijkheid, omdat ze een cruciaal rol spelen bij een website. 
Screen reader gebruikers moeten het idee hebben van waar de link naar verwijst. 


### Goede uitkomsten

>`[aria hidden="true"]` is not present on the document `<body>`.

Hulptechnologieën, zoals screen reader, werken inconsistent wanneer `aria-hidden="true"` is ingesteld op het document `<body>`.

> ARIA IDs are unique

De waarde van een ARIA-ID moet uniek zijn om te voorkomen dat andere instanties door ondersteunende technologieën over het hoofd worden gezien.

>`[user-scalable="no"]` is not used in the `<meta name="viewport">` element and the `[maximum-scale]` attribute is not less than 5.

Het uitschakelen van zoomen is problematisch voor slechtziende gebruikers die afhankelijk zijn van schermvergroting om de inhoud van een webpagina goed te kunnen zien. 

> Background and foreground colors have a sufficient contrast ratio.

Tekst met laag contrast is voor veel gebruikers moeilijk of onmogelijk om te lezen.  

!!!!!! Hier ben ik persoonlijk **niet mee eens**, de tekst op webpagina is wel moeilijk te lezen zoor laag contrast !!!!!!

> Document has a `<title>` element.

De titel geeft gebruikers van schermlezers een overzicht van de pagina, en gebruikers van search Engine vertrouwen er sterk op om te bepalen of een pagina relevant is voor hun zoekopdracht.

> `<html>` element has a `[lang]` attribute.

Als een pagina geen `[lang]`-attribuut specificeert, gaat een screen reader ervan uit dat de pagina de standaardtaal heeft die de gebruiker heeft gekozen bij het instellen van de screen reader. Als de pagina niet daadwerkelijk in de standaardtaal is, leest de screen reader de tekst van de pagina mogelijk niet correct voor.

> `<html>` element has a valid value for its `[lang]` attribute.

Door een geldige BCP 47-taal op te geven, kunnen schermlezers tekst correct aankondigen.

## Handmatige tests uitvoeren

### **Aanpak:**

* Begin met het testen van de website met je keyboard, zoals beschreven in het artikel "How To Do an Accessibility Review - Start with the keyboard"
* Test de website met een screenreader, zoals beschreven in het artikel "How To Do an Accessibility Review - Try it with a screen reader"
* Test de interactive elements en headings and landmarks van de website, zoals beschreven in het artikel "How To Do an Accessibility Review"
* Documenteer je bevindingen in de Wiki

### Resultaat

**Keyboard Accessibility**

De posities van de elementen zijn in de DOM, ze staan in logische volgorde. Interactive elementen waarop de user kan klikken (zoals navigatie links en linktekst) zijn focusseerbaar en beschikken over een focusindicator (een focusring). De elementen zoals headings, tekst en backgroundplaatje zijn niet focusseerbaar. 

De verborgen menu opent volledig alleen door het muis te gebruiken. Dus een aantal onderdelen van de website zoals _Terms of Service_ en _Subscribe to newsletter_  blijven verbogen voor keyboard users. 

Screenshots:

zichtbaar voor keyboard users:
<img width="1168" alt="image" src="https://github.com/aliceafanasieva/all-human-wcag-audit/assets/66431299/f1ceac17-21e2-4ab2-bac0-fd0ccce61717">

verborgen voor keyboard users:
<img width="1168" alt="image" src="https://github.com/aliceafanasieva/all-human-wcag-audit/assets/66431299/5571b783-f6c6-480b-8647-56c213e5bf30">

**Screen Reader Accessibility**

De VoiceOver begon automatisch elk element voorlezen. De VoiceOver zag ook de verborgen elementen uit de menu, terwijl ze niet geopend waren.
<img width="1168" alt="image" src="https://github.com/aliceafanasieva/all-human-wcag-audit/assets/66431299/2615fb67-27a9-41d8-a799-f0c213d85300">

De plaatje op achtergrond wordt vertoond als "unlabeled image". 
<img width="1361" alt="image" src="https://github.com/aliceafanasieva/all-human-wcag-audit/assets/66431299/05533751-5235-4c85-a676-cb8c34da4a84">

Om tekst om website voor te lezen moet de user van VoiceOver drukken op de plek waar de tekst staat, anders wordt het niet voorlezen. Op dat manier heeft een blinde gebruiker geen idee waar die op moet drukken en nog steeds blijft veel website content niet zichtbaar. De VoiceOver blijft zelf alleen de menu voor te lezen, kleine tekst in de menu, naam van pagina's, links onderaan de website. 

**Interactive elements Test**

De buttons in de menu container bovenaan de website hebben een `#f4e72a` hover als een indicator dat ze interactief zijn. De rest van de verborgen links bevatten geen hovers en dus geen indicatoren dat de elementen interactief zijn. 

<img width="397" alt="image" src="https://github.com/aliceafanasieva/all-human-wcag-audit/assets/66431299/64326f10-572a-4819-99f7-779476311c1d">

**Headings and landmarks Test**

Er wordt wel gebruik gemaakt van HTML hiërarchie, dus body, header, main, footer komen na elkaar. 

## Licentie

This project is licensed under the terms of the [MIT license](./LICENSE).
