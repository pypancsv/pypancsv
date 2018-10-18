# Salesforce: métadonnées personnalisées v. objets personnalisés

Une collègue, peu familière avec Salesforce, m'a demandée quelle était la différence entre « **métadonnées personnalisées** » et « **objets personnalisés** » pour stocker des données de configuration et de validation dans une organisation Salesforce.

J'ai répondu:

> * Selon Salesforce, s'il est possible, utilisez des **[métadonnées personnalisées](https://www.youtube.com/watch?v=kFwwcLxkkjI){:target="_blank"}**.  <br/> _(Elles survivent l'actualisation d'un environnement sandbox.)_
>
> * Stockez vos informations aux tables de bases de données (**objets personnalisés**) s'il faut créer des relations aux autres objets de votre organisation. <br/> _(Par exemple, s'il y a des utilisateurs qui vont générer des rapports sur ces données.)_

## Mon approche

Lorsque j'ai écrit un déclencheur Apex pour attribuer les enregistrements de notre objet « demande d'admission » aux utilisateurs corrects, j'ai fini par utiliser les deux approches:

### Métadonnées personnalisées

J'ai choisi une type de métadonnées personnalisées pour stocker des données simples concernant « qui gère chaque spécialisation ? »

* clé: le code qui indique un diplôme d'études supérieures que l'université offre
* valeur: un nom d'utilisateur chargé de recruter des étudiants au diplôme

### Objets personnalisés

J'ai choisi un objet personalisé pour stocker une liste d'états américains (abréviation et nom), avec quelques champs de référence indiquant les utilisateurs qui y gèrent divers aspects du recrutement d'étudiants en license.

* Nos utilisateurs ont besoin de générer des rapports, regroupés par utilisateur, avec les états qu'ils gèrent **et** les lycées qui y sont situés.  Donc il fallait pouvoir créer une relation de l'objet « lycée » à l'objet « état ».
* On peut [créer des relations entre métadonnées personnalisées](https://trailhead.salesforce.com/fr/content/learn/modules/custom_metadata_types/custom_metadata_types_create_md_relationships){:target="_blank"}, mais pas entre les types de métadonnées personnalisées et les objets personalisés.
  * Donc j'ai choisi un modèle « objet personnalisé » pour stocker les informations à propos des états, même si ces informations servent aussi comme données de configuration pour un déclencheur Apex.

### Considérations au sujet de l'interface utilisateur et au contrôle d'accès

Je vais vous révéler un secret :  ce n'est pas **qu**'à propos des besoins relationnels que j'ai choisi le modèle « objet personnalisé » pour les informations à propos de la gestion du recrutement en licence.

Le service admission en license changent les règles de « qui gère quoi » plusieurs fois par an.  Et les données de configuration sont, en réalité, beaucoup plus complexes qu'une seule liste d'états.

Actuellement, les interfaces utilisateur de Salesforce pour voir et enregistrer des données aux objets personnalisés sont supérieures à celles pour les métadonnées personnalisées -- surtout si l'on est utilisateur ordinaire.  Le contrôle d'accès, aussi, est plus facile à gérer pour les administrateurs.  Je voulais m'assurer que ça soit des utilisateurs ordinaires qui font plusieurs fois par an cette saisie de données, et non pas les administrateurs !

On m'a fait honte de cette position à Dreamforce.  Ben, je maintiens ma choix d'objet personnalisé pour raisons de relations entre objets.  Mais ... on a beaucoup répété qu'il est de bonne pratique de [construire ses propres interfaces utilisateur](https://trailhead.salesforce.com/fr/content/learn/modules/lex_dev_lc_basics){:target="_blank"} pour autoriser des utilisateurs ordinaires à modifier les métadonnées personnalisées en toute sécurité.  Je vous aurai prévenus !

#### Vidéos pertinentes de Dreamforce

1.  [« Build Awesome Configuration Pages with Lightning Components & Custom Metadata » de Dan Appleman](https://www.youtube.com/watch?v=Qr2tqjWnXgY){:target="_blank"}
2.  [« Crafting Flexible APIs in Apex Using Custom Metadata » de Gustavo Melendez & Krystian Charubin](https://www.youtube.com/watch?v=sGhAcGjQzyo){:target="_blank"}
3.  [« Create Guided User Experiences for Managing ISV Custom Metadata » de Beth Breisness & Randi Wilson](https://www.youtube.com/watch?v=nlqFB89DhfI){:target="_blank"}

---

# Salesforce Custom Metadata vs. Custom Objects

A colleague, new to Salesforce, asked me the difference between "**custom metadata**" and "**custom objects**" for storing "configuration and validation" information.

My answer is:

> * **[Custom metadata](https://www.youtube.com/watch?v=kFwwcLxkkjI)**{:target="_blank"} if you can. Salesforce says so.  <br/>*(And it survives sandbox refreshes!)*
> 
> * **Data tables (custom objects)** if you truly need it to be part of your data <br/>_(e.g. people will want to include it, hyperlinked to other data, in reports)_

## How I decided

When I wrote an Apex trigger that determined which User should "own" each "Admissions Application" in our org, I ended up splitting the configuration data in two.

Here's why.

### Custom Metadata

Used for a table that helps Apex code ask, "Who does this?"

* key:  the code for a graduate degree we offer
* value: a username responsible for recruiting people to that graduate degree

### Data (Custom Objects)

Used for a list of U.S. states, their full spellings, and fields with "lookup" links to the User table indicating who does what work for that state.

* There was strong demand to generate native Salesforce reports per User showing all the states they're responsible for and the high schools in those states.  It made sense to ensure that the "high school" table could have a "lookup" field to "state."
* Custom metadata can have "master-detail" and "lookup" relational links to other custom metadata, but it **can't** link to ordinary data.
  * This meant we needed to store the the "states" as data (custom objects), even though we would also be using it as configuration information for Apex triggers.

## UI & editability considerations

I'll let you in on a dirty little secret about _another_ reason I used **data** tables ("custom objects") for most of the Undergraduate Admissions counselor assignment configuration data.

Undergraduate Admissions tweaks their "recruiter assignment" business rules several times a year. The real-world configuration data for their business is a _lot_ more complex than a simple "list of U.S. states."

I'll be honest: Salesforce's user interfaces for hand-editing, viewing, and bulk-editing **data** is a lot more end-user-friendly than their user interfaces for the same operations on **custom metadata**, and setting granular "edit" permissions is a lot more sysadmin-friendly for data. I wanted to make sure end users, not sysadmins, were the ones whose time was spent tweaking the configuration several times a year!

I was thoroughly scolded at Dreamforce. Actually, I stand by my decision to use "data" tables, because there truly is a business need to report on the configuration data alongside normal data. But ... building your own user interfaces _(typically using Lightning Components)_ to help end users edit custom metadata was a big theme. You have been warned:

1.  [Dan Appleman's "Build Awesome Configuration Pages with Lightning Components & Custom Metadata"](https://www.youtube.com/watch?v=Qr2tqjWnXgY){:target="_blank"}
2.  [Gustavo Melendez & Krystian Charubin's "Crafting Flexible APIs in Apex Using Custom Metadata"](https://www.youtube.com/watch?v=sGhAcGjQzyo){:target="_blank"}
3.  [Beth Breisness & Randi Wilson's "Create Guided User Experiences for Managing ISV Custom Metadata"](https://www.youtube.com/watch?v=nlqFB89DhfI){:target="_blank"}
