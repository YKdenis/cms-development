---
description: >-
  Je hebt waarschijnlijk al eens met applicaties zoals XAMPP, MAMP of Bitname
  moeten werken. Local by Flywheel is een soortgelijke applicatie maar met zijn
  eigen werking.
---

# Lokaal ontwikkelen met Local By Flywheel

[Local](https://localwp.com/) bevat alles wat je nodig hebt om lokale sites op te zetten en te gebruiken. Het is eenvoudig genoeg voor beginners, maar biedt ook tal van geavanceerde functies voor gevorderden. Daarboven op is de standaardversie van Local by Flywheel 100% gratis! De standaardversie laat ons toe om een onbeperkt aantal lokale websites te bouwen.

## Wat onderscheidt Local van XAMPP, MAMP, …?

### **Om WordPress lokaal te doen werken moet de lokale omgeving voldoen aan 3 voorwaarden:**

* Een database powered door MySQL
* Een webserversoftware, meestal apache of NGINX
* PHP moet geïnstalleerd zijn op je lokaal apparaat. 

Als je een applicatie zoals MAMP of WAMPserver gebruikt, wordt er op je computer automatisch een ontwikkelingsomgeving opgezet. Als je weinig kennis hebt van hoe MAMP of XAMPP op de achtergrond werkt, kan dat voor beginners snel problemen met zich meebrengen. Denk maar aan poorten die in conflict komen met elkander.

Local by Flywheel daarentegen creëert een container, een virtuele computer \(Virtual Machine\) dat op je computer leeft met haar eigen MySQL, Apache of NGINX, en PHP setup. Dit betekent dat elke site een volledig op zich zelf staande ontwikkelingsomgeving heeft en elk zijn eigen custom hosting configuratie kan hebben. Deze zal nooit in conflict komen met een andere virtuele omgeving of je lokale hoofd ontwikkelingsomgeving. Dit is een hoop kop zorgen dat we ons zullen besparen wanneer we meerdere lokale sites tegelijkertijd willen runnen.

{% hint style="info" %}
Dit klinkt allemaal heel ingewikkeld maar Local by Flywheel zet deze VM's \(containers\), in de achtergrond, automatisch voor ons op. Het enigste dat wij moeten doen is zeggen hoe we onze ontwikkelingsomgeving willen configureren. Wil je NGINX gebruiken of Apache, welke versie van PHP etc. Dit is allemaal heel gemakkelijk in te stellen via het gebruiksvriendelijk dashboard van Local by Flywheel.
{% endhint %}

