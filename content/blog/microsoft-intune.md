---
title: "Microsoft Intune"
date: 2019-06-17T00:00:57+01:00
draft: false
banner: "/img/blog/intune/intune0.png"
author: "Julian Rasmussen"
categories: ["Office 365"]
tags: ["promo"]
---



## - <br> 

<p>Når vi snakker om skyen er «Device management» for mange et "glemt" kapittel, i alle fall for små og mellomstore bedrifter i Norge. Device management i skyen ble tidligere omtalt som MDM (Mobile device management), og mange tenkte nok at det bare gjaldt for Mobiler og nettbrett, - men tiden har endret seg og MDM omfavner nå PC og Mac`er også!</p>
<p>
Microsoft sin Intune-løsning har støtte for både Windows, MacOS, Android og iOS pr. dags dato. Dette betyr at de støtter de største operativsystemene som brukes ute i norske bedrifter. </p>
 <p>
Men hvorfor trenger akkurat du dette? Er det ikke greit at de ansatte selv har kontroll på maskinene? Jo, kanskje, men hvordan håndterer vi da bedriftens data som lagres på de ansattes telefoner eller pc`er? </p>
<p>
Med Office 365 er bedriftens data veldig enkel å få tilgang på, det holder at man logger seg inn på "office.com" med brukernavn og passord (+ MFA selvsagt) så har man derfra tilgang til epost, felles dokumenter i SharePoint, hjemmekatalogen i OneDrive for business eller andre sky-tjenester som er tilgjengeliggjort igjennom portalen. </p>
 <p>
Ok, så hva skal Intune hjelpe til med? 
</p>
<p>
Overordnet i en cloud only konfigurasjon vil det se slikt ut:

 </p>

  <img class="img-fluid mt-3 mb-3" src="/img/blog/intune/intune1.png" />

##### Registrering av enheter som kan få tilgang til bedriftens data   <br>

<p>

Ved at brukernes enheter registreres i firmaportalen (Intune-app) eller i Azure AD så vil man få kontroll på hvilke enheter brukerne har og får tilgang til bedriftens data med. 
 </p>

##### Sette krav til enheten
 <p>
Man kan lage samsvars krav til enhetene, som for eks. krever at maskinen har Antivirus, er oppdatert med siste oppdateringer og har kryptering av harddisken, før den blir markert som en "godkjent enhet". For Windows 10-maskiner kan man konfigurere opp til 28 sjekker, for MacOS opp til 18 sjekker. Man kan virkelig sette krav til enheten man skal dele alle bedriftshemmelighetene med.   
</p>
  <img class="img-fluid mt-3 mb-3" src="/img/blog/intune/intune2.png" />

##### Slippe inn ansatte basert på hvilken enhet de kommer fra 
<p>
- 
Ved bruk av Conditional Access sammen med Intune kan man kreve at enheten skal være "Compliant» i henhold til samsvarskravene vi konfigurerte i punktet over, om man skal kunne logge på "Office.com" og starte SharePoint.
</p>

  <img class="img-fluid mt-3 mb-3" src="/img/blog/intune/intune3.png" />
 
<p>
 Når man nå har registrert de mobile enhetene, som brukerne også bruker for personlige filer, får man et skille på bedriftsdata og personlige data i applikasjonen. Dette betyr at dersom enhetene blir stjålet, eller at den ansatte slutter i firmaet, kan man ved et par klikk slette bedriftens data (dokumenter, epost osv.) <br>
Man vil kunne blokkere datakopiering mellom den private delen av applikasjonen og den bedrifts-eide delen. 

  <img class="img-fluid mt-3 mb-3" src="/img/blog/intune/intune4.png" />

<br><br>
Tenker du nå at: - Ja! Litt mer kontroll på enhetene og dataene kunne jo vært greit?
<br><br>
Ta kontakt med Knut Skogvold på telefon 900 95 088 eller send en <br>
 <img class="card-img-top img-profil img-round mx-auto" src="/img/people/knut-round.jpg" style="float:right;">
<a href="kundeservice i pointtaken.no"  rel="nofollow" onclick="this.href='mailto:' + 'kundeservice' + '@' + 'pointtaken.no'">e-Post til kundeservice i Point Taken</a>
<br>
<br>


<br>
    <a class="btn btn-primary btn-full" href="/contact/" role="button">Vil du vite mer? Kontakt oss!</a>
<br>
<br>