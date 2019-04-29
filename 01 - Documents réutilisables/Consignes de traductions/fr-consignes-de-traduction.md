# Consignes de traduction

## Recommandations d'ordre général

* Gardez à l'esprit le public ciblé en utilisant un ton qui lui soit adapté.
* Soyez cohérent dans le ton et dans les formes employées sur l'ensemble du chantier de traduction.
* Respecter les règles de typographie qui s'appliquent à la langue cible.  
  Ex: en français, les doubles ponctuations sont précédées et suivies d'un espace et le premier est insécable.

## Syntaxe HTML

Le langage HTML, utilisé pour décrire les pages web, fourni un vocabulaire de balises pour structurer les contenus et les rendre compréhensibles par les navigateurs, les lecteurs d'écran et les moteurs de recherche. Chaque balise a une signification précise quant à la fonction du texte dans la page (titre, lien, citation).

Les balise HTML sont délimitées par des crochets (ex: `<strong>`) et peuvent porter des attributs (ex: `<a href="http://example.com" title="An example">`).

Les balises fonctionnent par paires. La première balise annonce le début d'une nouvelle section de texte (ex: `<p>` ouvre un nouveau paragraphe) et la seconde annonce sa fin (ex: `</p>` termine un paragraphe. Notez le '/' qui le différencie de la balise ouvrante.). Pour ne pas briser la mise en page du document, **ces paires doivent restées équilibrées**. Il convient également de conserver l'ordre d'imbrication des balises.  
Exception notable au fonctionnement par paire : la balise `<br/>`, forcant un retour à la ligne, s'utilise seule.

Appartenant à un vocabulaire normé, **les noms des balises et des attributs doivent être conservés lors de la traduction**. Ainsi le nom de balise `strong` ne doit pas être remplacé par `stark` pour une traduction allemande et le nom d'attribut `title` ne doit pas être remplacé par `titre` pour une traduction française.

**Le contenu entre les balises** ouvrantes et fermantes **et les valeurs des attributs**, soit le contenu placé entre guillemets à la droite du signe '=', **doivent être traduits ou adaptés à la langue cible**. Dans le cas où la traduction entraine une réorganisation des composants d'une phrase ou d'un texte, les balises de mise en forme appliquées à une portion de texte (ex: pour créer un lien ou une emphase) doivent lui rester associées.

```HTML
<p>La <strong>théorie de la relativité
  d'<a href="https://fr.wikipedia.org/wiki/Albert_Einstein#Biographie"
  title="Biographie d'Albert Einstein">Albert Einstein</a></strong>
  fut publiée en 1905.</p>
```

```HTML
<p><strong><a href="https://en.wikipedia.org/wiki/Albert_Einstein#Biography"
  title="Albert Einstein's biography">Albert Einstein</a>'s theory of
  relativity</strong> was published in 1905.</p>
```

### Mots-clés réservés du langage HTML

Certains attributs applicables aux balises du langage HTML attendent comme valeur des mots-clés spécifiques, propres au language (ex: `<a target="_blank">`, `<em class="muted">`). **Ces mots-clés ne doivent pas être traduits**.

### Entitées HTML

Certains caractères spéciaux peuvent être encodés sous la forme d'une entitée HTML (ex: `&raquo;` pour `»`). **Il est recommandé de laisser ses caractères sous cette forme**.

Au besoin, consulter [la liste des entitées HTML](https://dev.w3.org/html5/html-author/charref) pour référence.

## Espaces réservés

Certaines chaînes de caractères sont utilisées pour afficher sous une forme plus littéraire des informations dynamiques. Par exemple, dans la chaîne `Votre commande N°2019036001`, le numéro de la commande est variable. Dans les chaînes de caractères à traduire, vous trouverez pour ce type d'informations des espaces réservés.

Un espace réservé peut être noté sous plusieurs formes :

* `%{placeholder-name}` dans sa forme la plus simple (ex: `Votre commande N°{reference}`, `Étape %{current}/%{total}`)
* `%<placeholder-name>F` avec une précision supplémentaire du format
* `%F` dans sa forme concise, ne précisant que le format attendu

Le format 'F' précise le type de données attendu à cet emplacement. Parmis les formats pris en charge et régulièrement rencontrés, on note 'd' pour un nombre entier (ex: `%<count>d résultat(s) pour votre recherche`), 'f' pour un nombre à virgule (ex: `Dont T.V.A. %<rate>f%%`) et 's' pour une chaîne de caractères (ex: `À utiliser avant le %<date>s`).

Le format peut également être précédé de modificateurs précisant la mise en forme et la conversion exacte à appliquer aux données lors de leur insertion dans la chaîne de caractère. Au besoin, consulter [l'article sur la notation 'printf' sur Wikipédia](https://en.wikipedia.org/wiki/Printf_format_string#Format_placeholder_specification) pour référence.

D'une façon générale, **le nom et le format d'un espace réservé ne doivent pas être modifiés lors de la traduction**. Il doit en revanche être déplacé au sein de la phrase pour que celle-ci conserve son sens dans la langue cible.

## Cas particuliers : routes, urls et fragments d'urls

Certaines chaînes de caractères sont destinées à être utilisées pour construire des adresses URL lisibles et mémorisables.

Dans la langue d'origine, **ces chaînes de caractères suivent un format qui doit être conservé dans la langue cible** :

* Les lettres qui possèdent un équivalent minuscule non accentué doivent être remplacées par celui-ci (Ex: 'É' sera remplacé par 'e').
* Les espaces, ponctuations et autres caractères non alpha-numériques doivent être remplacés par des tirets '-' (Ex: `C'est le printemps` sera remplacé par `c-est-le-printemps`).
* Une chaîne ne doit jamais commencer ou se terminer par un tiret '-'.
* Plusieurs tirets successifs doivent être remplacés par un unique.

Ces chaînes sont normalement identifiées comme telles par le nom de la ressource à laquelle elles appartienent (ex: 'routes') ou par un commentaire à l'attention des traducteurs.
