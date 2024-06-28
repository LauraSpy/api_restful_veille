
#**Dossier Les API RESTful**

###Par Alexandra, Laura et Lucile

##**Structure de notre dossier**
1. Concept de base
  - API : Interface de Programmation d'Application permettant à différentes applications de communiquer entre elles.
  - REST : REpresentational State Transfer, un style architectural pour les systèmes distribués, principalement utilisé pour les services web.
2. Principes de REST
  - Stateless : Chaque requête du client au serveur doit contenir toutes les informations nécessaires à la compréhension et au traitement de la requête. Le serveur ne stocke aucune donnée de session entre les requêtes.
  - Client-serveur : Séparation des responsabilités entre le client (qui fait des requêtes) et le serveur (qui répond aux requêtes).
  - Mise en cache : Les réponses doivent indiquer si elles sont mises en cache pour améliorer les performances.
  - Interface uniforme : Utilisation d'une interface commune et standardisée pour interagir avec les ressources.
  - Système en couches : L'architecture peut être composée de plusieurs couches (sécurité, gestion des API, etc.).
  - Code à la demande (optionnel) : Le serveur peut temporairement étendre ou personnaliser la fonctionnalité du client en transférant du code exécutable.
3. Méthodes HTTP
  - GET : Récupérer des informations d'une ressource.
  - POST : Créer une nouvelle ressource.
  - PUT : Mettre à jour une ressource existante.
  - DELETE : Supprimer une ressource.
  - PATCH : Mettre à jour partiellement une ressource.
4. Design des Ressources et des Endpoints
  - Ressource : Toute donnée importante que l'API peut manipuler (par exemple, utilisateurs, commandes, produits).
  - Endpoints : URL spécifiques qui représentent ces ressources. Exemple :
    - GET /users : Récupérer la liste des utilisateurs.
    - POST /users : Créer un nouvel utilisateur.
    - GET /users/1 : Récupérer les détails de l'utilisateur avec l'identifiant 1.
    - PUT /users/1 : Mettre à jour l'utilisateur avec l'identifiant 1.
    - DELETE /users/1 : Supprimer l'utilisateur avec l'identifiant 1.
5. Authentification et Sécurisation des API
  - OAuth : Protocole d'autorisation permettant aux utilisateurs de partager des ressources privées avec un tiers sans divulguer leurs informations d'identification.
  - JWT (JSON Web Token) : Jeton sécurisé qui permet de vérifier l'identité de l'utilisateur et de transmettre des informations entre parties de manière sécurisée.
6. Gestion des Erreurs et Statuts HTTP
  - 200 OK : La requête a réussi.
  - 201 Created : Une nouvelle ressource a été créée.
  - 400 Bad Request : La requête est incorrecte ou mal formée.
  - 401 Unauthorized : Authentification nécessaire.
  - 403 Forbidden : Accès refusé, même si authentifié.
  - 404 Not Found : La ressource demandée n'existe pas.
  - 500 Internal Server Error : Erreur serveur.
7. Documentation et Bonnes Pratiques
  - Documentation claire : Utiliser des outils comme Swagger/OpenAPI pour documenter l'API.
  - Versionnement : Indiquer la version de l'API dans les endpoints (par exemple, /v1/users).
  - Retourner des messages d'erreur clairs : Fournir des informations détaillées sur les erreurs pour faciliter le débogage.
  - Utiliser HTTPS : Toujours sécuriser les communications pour protéger les données.

###**Conclusion**
Les API RESTful sont essentielles pour permettre la communication entre différentes applications via le web. Comprendre les principes REST, les méthodes HTTP, le design des ressources, la sécurisation, et la gestion des erreurs est crucial pour créer des API robustes et efficaces.


##**Développement des concepts**
1. Concept de base

###**API (Application Programming Interface)**

Imaginez que vous êtes dans un restaurant et que vous voulez commander de la nourriture. Vous avez un menu (la liste des choses que vous pouvez commander) et un serveur (la personne qui prend votre commande et vous apporte la nourriture). Une API, c'est un peu comme le menu et le serveur combinés pour les applications.
  - Menu : Liste des choses que vous pouvez demander (des informations, des actions).
  - Serveur : Celui qui prend votre demande, la transmet à la cuisine (une autre application ou un serveur), et vous ramène le résultat (les données ou la réponse à votre demande).
En d'autres termes, une API est une manière pour différentes applications de parler entre elles et de demander des services ou des informations, sans avoir à savoir comment l'autre application fonctionne en détail.

###**REST (REpresentational State Transfer)**

REST est comme une série de règles pour concevoir ces menus et serveurs pour les applications web. Il dit essentiellement :
  - Utilisez les choses simples que tout le monde connaît déjà : Comme les adresses web (URL) et les actions de base (comme obtenir des informations, envoyer des informations, mettre à jour des informations, etc.).
  - Ne gardez pas de souvenirs : Chaque demande doit être complète et indépendante. C'est comme si chaque fois que vous parlez au serveur dans le restaurant, il ne se souvient pas de votre dernière commande. Vous devez tout lui redire à chaque fois.

2. Principes de REST

###**Stateless (Sans état)**

Imaginez que chaque fois que vous parlez au serveur dans le restaurant, il ne se souvient jamais de vous ni de ce que vous avez commandé avant. Vous devez tout redire à chaque fois : votre nom, ce que vous voulez, etc. De cette façon, chaque commande est indépendante. Pour les applications, cela signifie que chaque requête (demande) doit contenir toutes les informations nécessaires, car le serveur ne garde pas en mémoire ce qui s'est passé avant.

###**Client-serveur**

Dans un restaurant, il y a vous (le client) et le serveur (qui vous sert). Vous ne vous occupez pas de la cuisine, vous ne faites que demander ce que vous voulez et recevoir votre commande. De même, en informatique, le client (votre application ou vous) fait des requêtes, et le serveur (l'autre application) répond. Ils ont des rôles distincts.

###**Mise en cache**

Imaginez que le serveur du restaurant vous dise que certaines choses du menu ne changent jamais et que vous pouvez les mémoriser pour les prochaines fois. Cela rend le service plus rapide parce que vous n'avez pas à demander des choses que vous savez déjà. En informatique, les réponses du serveur peuvent être mises en cache (mémorisées temporairement) pour accélérer les futures requêtes similaires.

###**Interface uniforme**

Cela signifie que toutes les interactions avec le serveur utilisent les mêmes règles simples. Imaginez que peu importe ce que vous commandez ou à quel serveur vous parlez, vous utilisez toujours le même processus : regarder le menu, choisir, commander. Pour les applications, cela signifie que les requêtes suivent un format standard, ce qui les rend faciles à comprendre et à utiliser.

###**Système en couches**

Pensez à un restaurant avec différentes sections : une section pour les boissons, une pour la nourriture, une pour les desserts. Vous faites une seule commande, mais elle est gérée par différentes sections avant de revenir à vous. En informatique, une architecture en couches signifie que la requête peut passer par plusieurs étapes ou services (comme sécurité, gestion des données, etc.) avant de vous donner une réponse.

###**Code à la demande (optionnel)**

Parfois, le serveur peut vous donner quelque chose de spécial pour améliorer votre expérience, comme un échantillon gratuit ou une nouvelle sauce à essayer. De même, un serveur informatique peut, si nécessaire, envoyer un morceau de code à votre application pour lui donner de nouvelles capacités temporaires.

**En résumé**, une API RESTful est un moyen structuré pour les applications de communiquer en utilisant des règles simples et standardisées. C'est comme avoir un menu clair dans un restaurant et un serveur qui suit toujours les mêmes étapes pour prendre et livrer vos commandes, de manière indépendante et efficace.

##**Une API REST, qu'est-ce que c'est ?**

Une API REST (également appelée API RESTful) est une interface de programmation d'application (API ou API web) qui respecte les contraintes du style d'architecture REST et permet d'interagir avec les services web RESTful. L'architecture REST (Representational State Transfer) a été créée par l'informaticien Roy Fielding.

![il est magnifique](https://www.golem.de/1209/94430-42921-i_rc.jpg)




---

#**Qu'est-ce qu'une API ?**

Une API est un ensemble de définitions et de protocoles qui facilite la création et l'intégration de logiciels d'applications. Elle est parfois considérée comme un contrat entre un fournisseur d'informations et un utilisateur d'informations, qui permet de définir le contenu demandé au consommateur (l'appel) et le contenu demandé au producteur (la réponse). 

##**Cas d'utilisation d'une API**

Par exemple, l'API conçue pour un service de météo peut demander à l'utilisateur de fournir un code postal et au producteur de renvoyer une réponse en deux parties : la première concernant la température maximale et la seconde la température minimale.

En d'autres termes, lorsque vous souhaitez interagir avec un ordinateur ou un système pour récupérer des informations ou exécuter une fonction, une API permet d'indiquer au système ce que vous attendez de lui, afin qu'il puisse comprendre votre demande et y répondre. 

Vous pouvez vous représenter une API comme un médiateur entre les utilisateurs ou clients et les ressources ou services web auxquels ils souhaitent accéder. 


##**Avantages des API**

Pour une entreprise, c'est aussi une solution pour partager des ressources et des informations, tout en maintenant un certain niveau de sécurité, de contrôle et d'authentification, en déterminant qui est autorisé à accéder à quoi. 

Autre avantage des API : vous n'avez pas besoin de connaître le fonctionnement exact de la mise en cache, c'est-à-dire de savoir comment vos ressources sont récupérées ni d'où elles proviennent.


#**REST**

REST est un ensemble de contraintes architecturales. Il ne s'agit ni d'un protocole, ni d'une norme. Les développeurs d'API peuvent mettre en œuvre REST de nombreuses manières.

Lorsqu'un client émet une requête par le biais d'une API RESTful, celle-ci transfère une représentation de l'état de la ressource au demandeur ou point de terminaison. Cette information, ou représentation, est fournie via le protocole HTTP dans l'un des formats suivants : JSON (JavaScript Object Notation), HTML, XLT, Python, PHP ou texte brut. Le langage de programmation le plus communément utilisé est JSON, car, contrairement à ce que son nom indique, il ne dépend pas d'un langage et peut être lu aussi bien par les humains que par les machines. 

Autre point à retenir : les en-têtes et paramètres jouent également un rôle majeur dans les méthodes HTTP d'une requête HTTP d'API RESTful, car ils contiennent des informations d'identification importantes concernant la requête (métadonnées, autorisation, URI, mise en cache, cookies, etc.). Il existe des en-têtes de requête et des en-têtes de réponse. Chacun dispose de ses propres informations de connexion HTTP et codes d'état.

Une API RESTful doit remplir les critères suivants :
  - Une architecture client-serveur constituée de clients, de serveurs et de ressources, avec des requêtes gérées via HTTP
  - Des communications client-serveur stateless, c'est-à-dire que les informations du client ne sont jamais stockées entre les requêtes GET, qui doivent être traitées séparément, de manière totalement indépendante
  - La possibilité de mettre en cache des données afin de rationaliser les interactions client-serveur
  - Une interface uniforme entre les composants qui permet un transfert standardisé des informations. Cela implique que :
    - les ressources demandées soient identifiables et séparées des représentations envoyées au client ;
    - les ressources puissent être manipulées par le client au moyen de la représentation reçue, qui contient suffisamment d'informations ;
    - les messages autodescriptifs renvoyés au client contiennent assez de détails pour décrire la manière dont celui-ci doit traiter les informations ;
    - l'API possède un hypertexte/hypermédia, qui permet au client d'utiliser des hyperliens pour connaître toutes les autres actions disponibles après avoir accédé à une ressource.
  - Un système à couches, invisible pour le client, qui permet de hiérarchiser les différents types de serveurs (pour la sécurité, l'équilibrage de charge, etc.) impliqués dans la récupération des informations demandées
  - Du code à la demande (facultatif), c'est-à-dire la possibilité d'envoyer du code exécutable depuis le serveur vers le client (lorsqu'il le demande) afin d'étendre les fonctionnalités d'un client 

Bien que l'API REST doive répondre à l'ensemble de ces critères, elle est considérée comme étant plus simple à utiliser qu'un protocole tel que SOAP (Simple Object Access Protocol), qui est soumis à des contraintes spécifiques, dont la messagerie XML, la sécurité intégrée et la conformité des transactions, ce qui le rend plus lourd et moins rapide. 

Puisque REST est un ensemble de directives mises en œuvre à la demande, les API REST sont plus rapides et légères, et offrent une évolutivité accrue. Elles sont donc idéales pour l'IoT (Internet des objets) et le développement d'applications mobiles. 

#**API SOAP ou REST**

Pour standardiser l'échange des informations entre les API toujours plus nombreuses, il a fallu développer un protocole : le « Simple Object Access Protocol », plus connu sous le nom de SOAP. Les API conçues d'après le protocole SOAP utilisent le format XML pour leurs messages et reçoivent des requêtes via HTTP ou SMTP. SOAP a pour objectif de simplifier l'échange des informations entre les applications qui s'exécutent dans des environnements différents ou qui ont été écrites dans des langages différents.

Le **« Representational State Transfer », ou REST,** est une autre tentative de normalisation. Les API web qui respectent les contraintes de l'architecture REST sont appelées API RESTful. Ces deux éléments diffèrent sur un point fondamental : SOAP est un protocole, alors que REST est un style d'architecture. Cela signifie qu'il n'existe aucune norme officielle qui régit les API web RESTful. Selon la définition proposée par Roy Fielding dans sa thèse « Architectural Styles and the Design of Network-based Software Architectures », les API sont RESTful tant qu'elles respectent les six contraintes de conception d'un système RESTful :
  - Architecture client-serveur : une architecture REST est composée de clients, de serveurs et de ressources et elle traite les requêtes via le protocole HTTP.
  - Serveur stateless : le contenu du client n'est jamais stocké sur le serveur entre les requêtes. Les informations sur l'état de la session sont, quant à elles, stockées sur le client.
  - Mémoire cache : la mise en mémoire cache permet de se passer de certaines interactions entre le client et le serveur.
  - Système à couches : des couches supplémentaires peuvent assurer la médiation dans les interactions entre le client et le serveur. Ces couches peuvent remplir des fonctions supplémentaires, telles que l'équilibrage de charge, le partage des caches ou la sécurité.
  - Code à la demande (facultatif) : un serveur peut étendre les fonctionnalités d'un client en lui transférant du code exécutable.
  - Interface uniforme : cette contrainte est capitale pour la conception des API RESTful et couvre quatre aspects différents :
    - Identification des ressources dans les requêtes : les ressources sont identifiées dans les requêtes et sont séparées des représentations retournées au client.
    - Manipulation des ressources par des représentations : les clients reçoivent des fichiers qui représentent les ressources. Ces représentations doivent contenir suffisamment d'informations pour être modifiées ou supprimées.
    - Messages autodescriptifs : tous les messages renvoyés au client contiennent assez d'informations pour décrire la manière dont celui-ci doit traiter les informations.
    - Hypermédia comme moteur du changement des états applicatifs : après avoir accédé à une ressource, le client REST doit être en mesure de découvrir toutes les autres actions disponibles par des hyperliens.

Ces contraintes peuvent sembler difficiles à appliquer, mais dans les faits, elles le sont moins qu'un protocole. C'est pour cette raison que les API RESTful prennent progressivement le pas sur les API SOAP.
Ces dernières années, la spécification OpenAPI s'est imposée comme la norme commune pour définir les API REST. La norme OpenAPI permet aux développeurs de créer des interfaces d'API REST indépendantes du langage de manière à ce que les utilisateurs puissent les comprendre avec un minimum d'approximation.
0
Une autre norme d'API est en train d'émerger : GraphQL, un langage de requête et un environnement d'exécution côté serveur qui se propose de remplacer l'architecture REST. GraphQL s'attache à fournir aux clients uniquement les données qu'ils ont demandées, et rien de plus. Utilisé à la place de REST, GraphQL permet aux développeurs de créer des requêtes qui extraient les données de plusieurs sources à l'aide d'un seul appel d'API.


##**Capacité de mise à l'échelle**

**Mise à l'échelle (scalabilité)** signifie qu'un système peut grandir et gérer plus de demandes sans perdre en performance.
  - Interaction client-serveur optimisée : Les API RESTful permettent une communication efficace entre le client (celui qui demande) et le serveur (celui qui répond).
  - Apatride (stateless) : Chaque demande du client contient toutes les informations nécessaires. Le serveur ne garde pas de mémoire des demandes précédentes. Cela allège le serveur, le rendant plus rapide et capable de gérer plus de demandes.
  - Mise en cache : Les réponses peuvent être mémorisées temporairement. Cela réduit la fréquence des demandes au serveur, améliorant encore la performance.
**Résumé simple :** Les API RESTful sont conçues pour être rapides et efficaces, ce qui leur permet de grandir sans devenir lentes ou surchargées.

####**Flexibilité**

**Flexibilité** signifie que les différentes parties du système peuvent changer ou évoluer sans causer de problèmes aux autres parties.
  - Séparation client-serveur : Le client et le serveur sont indépendants. Vous pouvez modifier le serveur sans affecter le client, et vice versa.
  - Découplage des composants : Les différentes parties du serveur peuvent être changées ou mises à jour indépendamment. Par exemple, vous pouvez améliorer la base de données sans toucher à la logique de l'application.
  - Superposition des fonctions : Vous pouvez ajouter des fonctionnalités ou faire des modifications à différentes couches de l'application sans devoir tout réécrire.
**Résumé simple :** Les API RESTful permettent de changer et d'améliorer les différentes parties du système sans tout casser.

####**Indépendance**

**Indépendance** signifie que les API RESTful ne dépendent pas de la technologie spécifique utilisée par le client ou le serveur.
  - Technologie indépendante : Vous pouvez utiliser différents langages de programmation pour le client et le serveur sans que cela affecte le fonctionnement de l'API.
  - Flexibilité technologique : Vous pouvez changer la technologie sous-jacente du serveur ou du client sans affecter la communication entre eux.
**Résumé simple :** Les API RESTful fonctionnent avec n'importe quelle technologie, ce qui les rend très flexibles et adaptables.




#**Les méthodes HTTP**

Les méthodes HTTP sont des actions que tu peux effectuer sur les ressources d'une API RESTful. Voici une explication simple des principales méthodes HTTP utilisées :

1. **GET :**
  - But : Récupérer des informations.
  - Exemple : Récupérer la liste des utilisateurs.
  - Utilisation : GET /utilisateurs
2. **POST :**
  - **But**: Créer une nouvelle ressource.
  - **Exemple** : Ajouter un nouvel utilisateur.
  - **Utilisation** : POST /utilisateurs
  - **Détails envoyés** : Les informations du nouvel utilisateur (nom, email, etc.).
3. **PUT :**
  - **But** : Mettre à jour une ressource existante (remplacement complet).
  - **Exemple** : Modifier les informations d'un utilisateur.
  - **Utilisation** : PUT /utilisateurs/123
  - **Détails envoyés** : Les nouvelles informations de l'utilisateur.
4. **PATCH** :
  - **But** : Mettre à jour partiellement une ressource.
  - **Exemple** : Modifier uniquement l'email d'un utilisateur.
  - **Utilisation** : PATCH /utilisateurs/123
  - **Détails envoyés** : L'information à modifier (nouvel email).
5. **DELETE** :
  - **But** : Supprimer une ressource.
  - **Exemple** : Supprimer un utilisateur.
  - **Utilisation** : DELETE /utilisateurs/123

Pour te donner une analogie simple, imagine une bibliothèque :
  - **GET** : Regarder la liste des livres disponibles.
  - **POST** : Ajouter un nouveau livre à la bibliothèque.
  - **PUT** : Remplacer complètement un livre existant (nouvelle édition).
  - **PATCH** : Modifier quelques pages d'un livre existant.
  - **DELETE** : Retirer un livre de la bibliothèque.
Chaque méthode HTTP correspond à une action spécifique à faire avec les données de ton API RESTful. C'est tout simple !

L'intérêt des méthodes HTTP dans le contexte d'une API RESTful réside dans leur capacité à fournir un moyen standardisé, efficace et compréhensible de gérer les ressources d'un système. Voici quelques points clés qui illustrent leur importance :
1. **Standardisation :**
  - **Interopérabilité** : Les méthodes HTTP sont des standards reconnus internationalement. Cela signifie que les développeurs du monde entier comprennent et utilisent les mêmes conventions, facilitant ainsi la collaboration et l'intégration de systèmes différents.
  - **Clarté** : Chaque méthode a une signification précise, ce qui rend l'API plus lisible et compréhensible.
2. **Simplicité et efficacité :**
  - **CRUD simplifié** : Les méthodes HTTP correspondent aux opérations CRUD (Create, Read, Update, Delete) courantes dans la gestion des données. Cela simplifie la conception et l'utilisation des API.
  - **Réduction de la complexité** : En utilisant des méthodes bien définies, on évite de créer des actions personnalisées complexes, ce qui simplifie le développement et la maintenance de l'API.
3. **Flexibilité :**
  - **Adaptabilité** : Les API RESTful peuvent évoluer facilement en ajoutant de nouvelles ressources ou en modifiant les existantes sans nécessiter de changements majeurs dans la structure de l'API.
  - **Partiellement mises à jour** : Avec PATCH, par exemple, on peut mettre à jour partiellement une ressource, ce qui peut être plus efficace et rapide que de remplacer entièrement une ressource avec PUT.
4. **Scalabilité :**
  - **Performance** : Les méthodes HTTP permettent une gestion efficace des ressources. Par exemple, GET est souvent optimisé pour être rapide et consommer peu de ressources.
  - **Cachabilité** : Les réponses aux requêtes GET peuvent être mises en cache, améliorant ainsi les performances et réduisant la charge sur le serveur.
5. **Sécurité et contrôle :**
  - **Permissions claires** : En utilisant différentes méthodes HTTP, on peut facilement définir et gérer les permissions et les autorisations sur les ressources. Par exemple, un utilisateur pourrait avoir le droit de lire des données (GET) mais pas de les modifier (PUT, PATCH) ou de les supprimer (DELETE).
  - **Traceabilité** : Les actions effectuées via différentes méthodes peuvent être loguées et suivies plus facilement, aidant à la surveillance et à l'audit.

**Exemple Pratique**

Imaginons que tu développes une application de gestion de bibliothèque avec une API RESTful :
  - **GET /livres** : Récupérer la liste de tous les livres.
  - **POST /livres** : Ajouter un nouveau livre.
  - **PUT /livres/123** : Remplacer les informations du livre avec l'ID 123.
  - **PATCH /livres/123** : Mettre à jour partiellement les informations du livre avec l'ID 123 (par exemple, changer seulement le titre).
  - **DELETE /livres/123** : Supprimer le livre avec l'ID 123.




#**Authentification et Sécurisation des API**

Imaginez que vous avez une maison (votre API) remplie de trésors (vos données). Vous voulez que seules certaines personnes puissent y entrer, et vous voulez contrôler ce qu'elles peuvent faire une fois à l'intérieur.

##**OAuth**

OAuth est comme un système de clés spéciales pour votre maison. Au lieu de donner votre clé principale (mot de passe) à quelqu'un, vous lui donnez une clé temporaire qui ne fonctionne que pour certaines pièces et pendant une durée limitée. Par exemple, vous pourriez donner à votre ami une clé qui lui permet d'accéder uniquement à la cuisine pendant une journée.

**OAuth 2.0** est donc un protocole d'autorisation standardisé qui permet à une application d'accéder à des ressources au nom d'un utilisateur sans avoir besoin de ses identifiants.

###**Fonctionnement simplifié :**

  - L'utilisateur veut utiliser une application tierce avec son compte Google.
  - L'application demande l'autorisation à Google.
  - Google demande à l'utilisateur s'il accepte de partager certaines informations.
  - Si l'utilisateur accepte, Google donne un "jeton d'accès" à l'application.
  - L'application utilise ce jeton pour accéder aux informations autorisées.

###**Avantages :**

  - **Sécurité accrue** : l'application tierce n'a jamais accès au mot de passe de l'utilisateur.
  - **Contrôle granulaire** : l'utilisateur peut choisir quelles informations il partage.
  - **Révocation facile** : l'accès peut être retiré à tout moment sans changer de mot de passe.

##**JWT (JSON Web Token)**

JWT est comme un badge d'identification sécurisé. Quand quelqu'un entre dans votre maison avec une clé OAuth, vous lui donnez ce badge. Le badge contient des informations sur qui ils sont et ce qu'ils sont autorisés à faire. Chaque fois qu'ils veulent faire quelque chose dans la maison, ils montrent ce badge, et vous pouvez vérifier rapidement s'ils sont autorisés.

JWT est un standard ouvert (RFC 7519) qui définit une manière compacte et autonome de transmettre des informations de manière sécurisée entre les parties sous forme d'objet JSON.

**Structure d'un JWT :**
  - Header : Type de token et algorithme de hachage
  - Payload : Contient les revendications (claims). Ce sont des déclarations sur l'entité (généralement l'utilisateur) et des métadonnées additionnelles.
  - Signature : Assure que le token n'a pas été altéré.
**Fonctionnement :**
  - L'utilisateur s'authentifie et reçoit un JWT.
  - Pour chaque requête suivante, l'utilisateur envoie ce JWT.
  - Le serveur vérifie la signature du JWT pour s'assurer de sa validité.
**Avantages :**
  - Stateless : Le serveur n'a pas besoin de stocker les sessions.
  - Portable : Peut être utilisé à travers différents domaines.
  - Sécurisé : La signature empêche la falsification.

##Gestion des Erreurs et Statuts HTTP

Les codes de statuts HTTP sont standardisés et divisés en cinq classes. 
  - **1xx (Informationnel)** : Rarement utilisés directement par les développeurs.
  - **2xx (Succès)** : La requête a été reçue, comprise et acceptée.
  - **3xx (Redirection)** : Une action supplémentaire est nécessaire pour compléter la requête.
  - **4xx (Erreur du client)** : La requête contient une erreur ou ne peut pas être traitée.
  - **5xx (Erreur du serveur)** : Le serveur a échoué à traiter une requête apparemment valide.

Ils peuvent être représentés comme des messages que votre maison (API) envoie aux visiteurs pour leur dire ce qui se passe. Voici quelques exemples :
  - 200 OK : "Bienvenue ! Tout va bien, entrez !", soit il indique que la requête a réussi. C'est la réponse standard pour les requêtes HTTP réussies.
  - 201 Created : "Super ! J'ai créé ce que vous m'avez demandé.", soit il indique que la requête a réussi et qu'une nouvelle ressource a été créée en conséquence. Typiquement utilisé avec les requêtes POST.
  - 400 Bad Request : "Désolé, je ne comprends pas ce que vous demandez.", soit le serveur ne peut pas ou ne veut pas traiter la requête en raison d'une erreur apparente du client (syntaxe mal formée, taille trop importante, etc.).
  - 401 Unauthorized : "Hé ! Vous devez vous identifier avant d'entrer.", qui est similaire à 403 Forbidden, mais spécifiquement pour une utilisation lorsque l'authentification est requise et a échoué ou n'a pas encore été fournie.
  - 403 Forbidden : "Je vous connais, mais vous n'avez pas le droit d'aller là." Le client n'a pas les droits d'accès au contenu, donc le serveur refuse de donner la réponse appropriée.
  - 404 Not Found : "Oups ! Ce que vous cherchez n'existe pas ici.", l’une des plus connues : Le serveur n'a pas trouvé la ressource demandée. Souvent utilisé lorsque l'URL demandée n'existe pas sur le serveur.
  - 500 Internal Server Error : "Oh non ! J'ai un problème interne, ce n'est pas de votre faute." Une erreur générique, donnée quand une condition inattendue a été rencontrée et qu'aucune autre réponse spécifique ne convient.

Ces statuts aident les développeurs à comprendre ce qui se passe quand ils interagissent avec votre API, un peu comme des panneaux indicateurs dans votre maison. 


##**Les bonnes pratiques pour la gestion des erreurs :**

  - Utilisez les codes de statut appropriés.
  - Fournissez des messages d'erreur clairs et utiles.
  - Incluez des détails supplémentaires comme un code d'erreur unique pour faciliter le débogage.
  - Loggez les erreurs côté serveur pour le suivi et l'analyse.

En résumé, l'authentification et la sécurisation des API sont des moyens de contrôler qui peut accéder à nos données et ce qu'ils peuvent en faire. Les statuts HTTP sont des messages qui indiquent comment se déroule l'interaction avec l’API. En implémentant ces concepts correctement, on crée une API plus robuste, sécurisée et facile à utiliser pour les développeurs qui l'intégreront dans leurs applications.






##**Sources sites**

[image](https://www.redhat.com/fr/topics/api/what-are-application-programming-interfaces)

[image](https://aws.amazon.com/fr/what-is/restful-api/)

[image](https://blog.hubspot.fr/website/api-rest)

[image](https://restfulapi.net/)


