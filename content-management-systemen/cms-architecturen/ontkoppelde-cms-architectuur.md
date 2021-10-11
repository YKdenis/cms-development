---
description: >-
  Een ontkoppelde CMS-architectuur ontkoppelt de back-end en front-end. Ze
  worden op een aparte server gehost en communiceren via een API.
---

# Ontkoppelde CMS-architectuur

Het grootste voordeel van een ontkoppelde CMS is dat je front-end agnostisch kan werken. Wat wilt zeggen dat je eender welke front-end kan gebruiken om de website uit te bouwen. De data zal vanuit de back-end via een API worden doorgestuurd. Deze data kan vervolgens worden gebruikt door eender welk front-end systeem.

Als developer kan je dus kiezen voor een front-end in Angular, React, Vue, ... noem maar op. M.a.w. de technologie waar jij, of je team, het liefst mee werkt.

Hoewel de back-end en de front-end onafhankelijk van elkaar werken, is de front-end vooraf bepaald met een gespecificeerde webtechnologie. De API wordt geschreven op manier waarmee beide systemen perfect met elkaar kunnen communiceren. M.a.w. de API is afgestemd om te werken met **één specifieke front-end technologie.**

{% hint style="info" %}
API staat voor **Application Programming Interface**, kort omschreven stelt verschillende systemen instaat om met elkaar te communiceren en gegevens uit te wisselen.
{% endhint %}

![Een ontkoppelde CMS-Architectuur](../../.gitbook/assets/image%20%28123%29.png)

## Pro's en cons van ontkoppelde CMS-architectuur

In een ontkoppelde CMS zijn de back-end en front-end afzonderlijk ondergebracht. Ontkoppelde CMS-architectuur is **front-end-agnostisch** en maakt gebruik van API's om content in onbewerkte vorm te leveren, waar dan ook. Velen beschouwen ontkoppeld als het **beste van twee werelden**: je hebt sjablonen om mee te werken zoals in een gekoppelde CMS-platform, maar je hebt de flexibiliteit van een headless CMS-implementatie.

### **Pro's:**

1. Snellere en flexibelere levering van inhoud dan een gekoppelde CMS;
2. Verbeterde beveiliging. Back-end en front-end worden op aparte servers gehost;
3. Minder afhankelijk van uitgevers en ontwikkelaars. Meer plaats voor maatwerk;
4. Toekomstbestendig, meer flexibiliteit en schaalbaarheid;

### **Con's:**

1. een ontkoppelde CMS is veel ingewikkelder dan een gekoppelde CMS. Het vereist extra ontwikkelingswerk.

