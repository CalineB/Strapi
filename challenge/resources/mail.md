*De* : Ton boss \<michel@propel.io>

*À* : Toi qui lit ce message \<newcomer@propel.io>

*Sujet* : Ton premier projet

----

Salut Gontran ! (oui, je sais que tu t'appelles pas Gontran, mais comme peu de personnes s'appellent Gontran, ça met tous les nouveaux sur un pied d'égalité ; promis, je retiendrai ton prénom quand tu auras fini ta période d'essai :smirk:)

Bienvenue chez Propel !

Je pense que Gisèle t'a déjà fait faire le tour des locaux. En fait, oui forcément, puisque tu lis ce message sur ton PC professionnel. Tu as aussi fait la connaissance de tes collègues et de Davido, le lead dev. Davido, il est sympa mais il est très très occupé : n'hésite pas à épuiser tous les moyens possibles pour trouver une réponse à ta question avant de lui poser.

Bon ! On parle de ton projet ? J'ai signé hier un petit média indépendant qui souhaite commencer petit : ils ont besoin d'un blog simpliste. Les points suivants ont déjà été décidés :
- les articles ont un titre, un chapeau (sous-titre) et un corps
- les articles pourront avoir une ou plusieurs catégories (sport, cuisine, ...)
- on garde trace des dates de modif + une date d'écriture initiale, et l'auteur de l'article
- le filtrage par catégorie est une priorité, celui par auteur beaucoup moins

- *et si tu as le temps et l'envie, prévois un système de suggestions : quand un visiteur lit un article, l'idée serait de lui en proposer 2 autres (en se basant sur les catégories)*

C'est Jérémy qui va se charger du front. Ca sera le principal utilisateur de notre API. Mais présentement, il est en train de récupérer d'une soirée un peu trop arrosée, je lui ai donné 2 jours de repos. Donc concentre-toi sur l'API, utilise Insomnia pour tester que tout roule ! Dès que tu as fini, fais-moi signe et donne-moi l'url de ton repo, que je teste tout ça !

Pour la deadline, ils nous mettent un peu de pression : semaine prochaine, ils voudraient une première version qui tourne. Donc si tu peux avoir une ébauche d'API qui tourne d'ici ce soir, je t'en serai éternellement reconnaissant pour quelques jours :-)

Éclate-toi !

Mich'


<details><summary>
Hey, t'es encore là ? T'as du mal à démarrer ? (Spoiler section)
</summary>

Je crois que Davido est dans le coin pour t'aider à structurer ton travail !

**Message de David :**

Hey ! Une fois que tu auras installé Strapi, généré un projet (`custom`), et connecté à une BDD `Postgres` en local, voila grosso modo ce dont on a besoin :

- D'un super-administrateur (nous, les devs') qui peut gérer la structure de la BDD et les règles de l'application, etc...

- D'un administrateur "éditeur" (Joseline, du média indépendant) qui a le droit de créer des articles et des catégories, et les publier, mais pas le droit de modifier la structure de l'app !

- D'une clé API (pour Jeremy), afin qu'il puisse consommer les données de notre API.

- Et surtout d'une API avec :
  - une route qui renvoie tous les articles, avec leurs catégories
  - une route qui renvoie tous les articles qui contiennent un mot recherché dans leur titre.
  - une route qui renvoie tous les articles d'une catégorie.
  - **=> Noter/documenter ces routes lorsque vous les trouver. Ou les implémenter si elles n'existent pas !**

- (bonus) une route qui renvoie les articles _en lien_. Un article est en lien avec un autre si :
  - il partage au moins une catégorie commune avec l'autre article
  - son titre contient au moins un mot commun avec le titre de l'autre article
  - ce n'est pas l'article lui même
- (super bonus) la possibilité d'ajouter des photos dans les articles (regarde un peu où sont stockées les photos ensuite !)

</details>

<details><summary>
Hey, t'es encore encore là ? T'as du mal à lancer Strapi ? (Spoiler section)
</summary>

- La doc est [là](https://docs.strapi.io/developer-docs/latest/getting-started/introduction.html)
  - Pour l'installation, c'est [ici](https://docs.strapi.io/developer-docs/latest/setup-deployment-guides/installation/cli.html#creating-a-strapi-project)

Un peu d'aide ? 

- 1. Vérifie que ta version de Node est bien `18`.

- 2. Créer un utilisateur Postgres `strapiblog` une base de donnée `strapiblog` via `psql` comme d'habitude.

- 3. Créer un projet Strapi via le terminal : `npx create-strapi-app@latest strapiblog`
    - Choose your installation type -> `Custom (manual settings)`
    - Choose your default database client -> `Postgres`
    - Database name -> `strapiblog`
    - Host -> laisser vide
    - Port -> laisser vide
    - Username -> `strapiblog`
    - Password -> celui que tu as choisi pour ton user Postgres
    - Enable SSL connection -> `N` (important)

- 4. Il n'y a plus qu'à fouiller dans le dossier `package.json` pour savoir comment lancer l'application :tada: !

</details>
