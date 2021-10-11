---
description: >-
  Bij het definiëren van een headless CMS-architectuur is het belangrijk om te
  begrijpen hoe deze zich verhoudt tot een ontkoppelde CMS-architectuur.
---

# Headless CMS-architectuur

Headless is eigenlijk **een subset van een ontkoppelde architectuur**.

Beide hebben een back-end voor het beheren, opslagen en leveren van content. Maar het belangrijkste verschil is de manier waarop de API wordt geschreven: **in tegenstelling tot een ontkoppelde CMS heeft een headless CMS geen gedefinieerd front-end-systeem.** M.a.w. de API is niet specifiek afgestemd om te verbinden met één front-end systeem.

{% hint style="info" %}
Dit klinkt waarschijnlijk een beetje abstract. Een gemakkelijke manier om het verschil tussen een headless en een ontkoppelde CMS-architectuur te begrijpen, is door losgekoppeld als proactief te beschouwen en headless als reactief.
{% endhint %}

Als men begint met het opzetten van een ontkoppelde CMS dan wordt er **van te voren bepaald welke front-end technologie men zal gebruiken.** Tijdens het bouwen van de back-end zal men proactief rekening houden met de gekozen front-end technologie.

Bij het opzetten van een Headless CMS weet men nog niet van te voren welke front-end of zelfs front-ends met de back-end zullen communiceren. De API wordt geschreven op een manier zodat eender welke front-end data kan ophalen en wegschrijven. Dit geeft veel meer flexibiliteit en schaalbaarheid aan je project. Je kan gemakkelijk veranderen van front-end technologie en je kan de back-end hergebruiken voor een ander front-end systeem.

{% hint style="info" %}
Bijvoorbeeld: Een e-commerce winkel die een front-end heeft in React maar wilt uitbreiden naar native applicaties voor iOS en Android.

Als ze een headless CMS hebben dan moeten ze alleen een front-end voor beide besturingssystemen maken. Aangezien de API front-end agnostisch is kan de back-end worden hergebruikt!
{% endhint %}

![Headless CMS-Architectuur](../../.gitbook/assets/image%20%2852%29.png)

## Pro's en cons van headless CMS-architectuur

Headless CMS-architectuur is een subset van een ontkoppelde CMS m.a.w. het deelt bijna alle voordelen. Zonder een aangewezen front-end biedt een headless CMS echter de grootste flexibiliteit om inhoud op verschillende platformen te publiceren. In tegenstelling tot ontkoppeld, kan je met headless dynamische inhoud publiceren op elk apparaat dat via IoT \(Internet of Things\) is verbonden. Van alle drie de CMS-architecturen biedt headless CMS de meeste controle over hoe en waar je inhoud wordt weergegeven.

Een nadeel is dat headless CMS-platformen meestal geen gebruikersinterface hebben, daarom kan het moeilijker zijn om een ​​nauwkeurige live preview te zien dan bij ontkoppeld. Om deze redenen zijn headless-platforms het meest geschikt voor bedrijven met een robuust team van ontwikkelaars die er de voorkeur aan geven hun favoriete frameworks en tools te gebruiken.

### **Pro's:**

1. Grootste flexibiliteit en schaalbaarheid. "één API, meerdere front-ends.";

### **Con's:**

1. Meeste headless CMS-platformen hebben geen deftige gebruikersinterface;
2. een headless CMS is veel ingewikkelder dan een ontkoppeld CMS. Het vereist extra ontwikkelingswerk.

## Extra resources 📚

{% embed url="https://www.smashingmagazine.com/2021/08/history-future-jamstack-cms/" caption="Geschiedenis van JAMstack" %}

