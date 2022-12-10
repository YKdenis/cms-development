---
description: >-
  Stel een GitHub-repo in voor je site. Github is een website die veel
  ontwikkelaars gebruiken om een back-up te maken van hun code en deze online te
  delen.
---

# Aanmaken van een Github Repo

Door je code naar GitHub te uploaden, kan je vanaf meerdere computers op dezelfde codebase werken. Later zal je ook via Github aan continuous deployment doen. Een efficiente manier om je code up te date te houden! Later hier meer over. Laten we ons nu focussen op het aanmaken van een nieuwe Repository.

Elke codebase op GitHub wordt opgeslagen in zijn eigen repository (**ook wel een "repo" genoemd**). Om een nieuwe repository voor je artist agency te maken, navigeer je naar [https://github.com/](https://github.com/).

{% hint style="warning" %}
Ik veronderstel dat iedereen voor Github al een account heeft aangemaakt in een eerder vak.
{% endhint %}

1\) klik je op het plus icoontje in de rechterbovenhoek van de navigatiebalk. Selecteer **"New Repo"**.

![](<../../.gitbook/assets/image (82).png>)

2\) Wanneer je het formulier voor je nieuwe repo invult, kan je deze openbaar of privé maken. Dit heeft alleen invloed op de zichtbaarheid van je code op GitHub.&#x20;

{% hint style="warning" %}
Je site is nog steeds zichtbaar voor iedereen zodra je deze implementeert met Gatsby Cloud, Netlify of een ander hosting platform!
{% endhint %}

Laat de selectievakjes voor de initialisatie uitgeschakeld.

<figure><img src="../../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>

3\) Om je bestaande code van je computer naar je nieuwe GitHub-repository te pushen, voer je de onderstaande opdrachten in de command line in. Zorg ervoor dat je `YOUR_GITHUB_USERNAME` verwisselt met je GitHub gebruikersnaam en `YOUR_GITHUB_REPO_NAME` met de naam die je aan je GitHub-repo hebt gegeven (zoals artist-agency-2021).

{% hint style="info" %}
**Let op**: je voert elke lijn code apart uit!
{% endhint %}

<pre><code><strong>git remote add origin https://github.com/YOUR_GITHUB_USERNAME/YOUR_GITHUB_REPO_NAME.git
</strong>git branch -M main
git push -u origin main
</code></pre>

Als je bovenstaande commands hebt uitgevoerd dan zal je de code zien verschijnen in je GitHub repo.

<figure><img src="../../.gitbook/assets/image (220).png" alt=""><figcaption></figcaption></figure>

Super! Je Github repo is geïnitialiseerd! 🎉 Je kan nu al je aanpassingen pushen naar je repo. **Zorg er voor dat je dit regelmatig doet en vermijdt dat je code kwijt speelt!**

## GitHub voor het eerst gebruiken?

Als je een foutmelding krijgt over machtigingen wanneer je de code voor de eerste keer naar GitHub probeert te pushen, moet je mogelijks een **SSH-sleutel** instellen voor je GitHub-account. Hierdoor weet GitHub dat je computer toestemming heeft om codewijzigingen naar je externe repo's te pushen.

Voor instructies over het instellen van een **SSH-sleutel,** volg de **GitHub-handleiding**: [Verbinding maken met GitHub met SSH](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh).
