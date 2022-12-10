# Query Variabelen

#### Bekijk onderstaande link voor de officiële documentatie omtrent Query Variabelen:

{% embed url="https://graphql.org/learn/queries/#variables" %}

### Query Variables

In de GraphiQL IDE kan je **query variabelen** meegeven om je queries generiek te maken. Variabelen moeten gedefinieerd worden van boven bij de operatie naam a.d.h.v. van **een dollar-teken**. Je definieert wat voor soort type je variabele is. In het voorbeeld hieronder is dat "`ID`" wat voor identifier staat. Het **uitroepteken(!)** laat weten aan GraphQL dat we strikt een identifier verwachten een geen ander type zoals bv. een string of integer.

Bij de **operation name "**`NewQuery`**"** geef je een variabele mee genaamd `$slug` en laat je graphQL weten dat het een `ID` verwacht. Vervolgens geef je de variable  `$slug` in de artist query als parameter mee aan `id`. De parameter `idType` zetten we op `SLUG`, zo weet GraphQL dat we een artist willen opvragen m.b.v. een slug. Je kan hier ook `DATABASE_ID`, `URI` of `ID` meegeven indien je het via een andere identifier wenst op te halen maar voor deze cursus zal je uitsluitend de `SLUG` gebruiken als `idType`.

<figure><img src="../../../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>

bovenstaande query zal een artist ophalen a.d.h.v. een slug. Een slug is het laatste deel van een URL. Je kan de slug te weten komen door naar je artist te navigeren en op Edit te klikken. **Het laatste deel van de URL bij permalink is de slug**.&#x20;

<figure><img src="../../../.gitbook/assets/image (204).png" alt=""><figcaption></figcaption></figure>

Ten slotte kan je in het veld **Query Variables** een JSON-geformatteerd object meegeven waarin je de variabele "`slug`" definieert.

Als je de query nu uitvoert zal je dit als response krijgen:

<figure><img src="../../../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>

Indien we de query willen hergebruiken en een andere artist willen opvragen dan kan dat gemakkelijk door de "`slug`" in ons JSON-object aan te passen naar een andere waarde. We hebben een **generieke/herbruikbare** **query** gedefinieerd!

#### Bekijk onderstaande link voor de officiële documentatie omtrent Query Variabelen:

{% embed url="https://graphql.org/learn/queries/#variables" %}
