---
title: DevOps
description: Considérations relatives à DevOps pour les applications Cloud natives
ms.date: 05/13/2020
ms.openlocfilehash: ce814595245d49e409e780cb0f63c436299c2e4e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614113"
---
# <a name="devops"></a>DevOps

Le mantra préféré des conseillers en logiciels est de répondre à la question « cela dépend » de toute question posée. Ce n’est pas parce que les consultants logiciels ne prennent pas de position. C’est parce qu’il n’y a pas une vraie réponse aux questions dans les logiciels. Il n’y a pas de droit absolu, mais plutôt un équilibre entre les opposés.

Prenez, par exemple, les deux écoles principales du développement d’applications Web : les applications à page unique (SPAs) et les applications côté serveur. D’un côté, l’expérience utilisateur a tendance à être meilleure avec la fonction de déchiffrement et le volume de trafic vers le serveur Web peut être réduit, ce qui permet de les héberger aussi simplement qu’un hébergement statique. En revanche, la création de la création de conflit est plus lente et plus difficile à tester. Lequel est le bon choix ? Cela dépend de votre situation.

Les applications Cloud natives ne sont pas immunisées contre ce même dichotomie. Ils présentent des avantages clairs en termes de vitesse de développement, de stabilité et d’évolutivité, mais leur gestion peut être un peu plus difficile.

Il y a des années, il n’était pas rare pour le processus de migration d’une application du développement à la production pour prendre un mois, voire plus. Les entreprises ont publié des logiciels sur une cadence de 6 mois, voire tous les ans. Il n’est pas nécessaire de regarder plus loin que Microsoft Windows pour avoir une idée de la cadence des mises en production qui étaient acceptables avant les jours jamais verts de Windows 10. Cinq ans passés entre Windows XP et Vista, 3 autres entre Vista et Windows 7.

Il est maintenant assez bien établi que le fait de pouvoir libérer rapidement des logiciels offre aux entreprises qui évoluent rapidement un énorme avantage sur le marché de leurs concurrents Sloth. C’est pour cette raison que les mises à jour majeures de Windows 10 sont à présent environ tous les six mois.

Les modèles et pratiques qui permettent d’obtenir des versions plus rapides et plus fiables pour fournir de la valeur à l’entreprise sont collectivement appelés DevOps. Ils se composent d’un large éventail d’idées couvrant l’ensemble du cycle de vie du développement de logiciels, de la spécification d’une application jusqu’à la mise en œuvre et au fonctionnement de cette application.

Les DevOps sont apparus avant les microservices et il est probable que le mouvement vers le plus petit, plus adapté aux services à but n’aurait pas été possible sans DevOps pour rendre la libération et le fonctionnement non seulement une, mais plusieurs applications en production plus simples.

![La figure 10-1 les tendances de recherche montrent que la croissance dans les microservices ne démarre pas tant que DevOps n’est pas une idée bien établie.](./media/microservices-vs-devops.png)

**Figure 10-1** : DevOps et microservices.

Grâce aux bonnes pratiques en matière de DevOps, il est possible de tirer parti des avantages des applications Cloud natives sans Suffocating sous une montagne de travail qui exécute réellement les applications.

Il n’y a aucun marteau doré lorsqu’il s’agit de DevOps. Personne ne peut vendre une solution complète et complète pour la publication et l’exploitation d’applications de haute qualité. Cela est dû au fait que chaque application est tout à fait différente de toutes les autres. Toutefois, il existe des outils qui peuvent faire de DevOps une proposition beaucoup moins fastidieuse. L’un de ces outils est appelé Azure DevOps.

## <a name="azure-devops"></a>Azure DevOps

Azure DevOps a une longue généalogie. Il peut remonter ses racines jusqu’au moment où Team Foundation Server déplacés en ligne pour la première fois et par le biais des différentes modifications de nom : Visual Studio Online et Visual Studio Team Services. Au cours des années, cependant, il est devenu beaucoup plus que ses prédécesseurs.

Azure DevOps est divisé en cinq composants principaux :

![Figure 10-2 les cinq principales zones d’Azure DevOps](./media/devops-components.png)

**Figure 10-2** : Azure DevOps.

**Azure repos** -gestion du code source qui prend en charge vénérable Team Foundation version Control (TFVC) et le [git](https://en.wikipedia.org/wiki/Git)préféré du secteur. Les demandes de tirage (pull requests) offrent un moyen d’activer le codage social en encourageant la discussion des modifications à mesure qu’elles sont effectuées.

**Azure Boards** : fournit un outil de suivi des problèmes et des éléments de travail qui s’efforce d’autoriser les utilisateurs à choisir les workflows qui leur conviennent le mieux. Il est fourni avec un certain nombre de modèles préconfigurés, notamment ceux pour prendre en charge SCRUM et les styles de kanban de développement.

**Azure pipelines** : un système de gestion de builds et de versions qui prend en charge une intégration étroite avec Azure. Les builds peuvent être exécutées sur diverses plateformes, de Windows à Linux à MacOS. Les agents de build peuvent être approvisionnés dans le Cloud ou localement.

**Azure test plans** -aucune personne ne pourra rester en contact avec la prise en charge de la gestion des tests et des tests exploratoires offerte par la fonctionnalité de test plans.

**Azure artifacts** : flux d’artefact qui permet aux entreprises de créer leurs propres versions de NuGet, NPM et autres. Il a un double objectif d’agir comme un cache de packages en amont en cas de défaillance d’un référentiel centralisé.

L’unité d’organisation de niveau supérieur dans Azure DevOps est appelée projet. Dans chaque projet, les différents composants, tels que les Azure Artifacts, peuvent être activés et désactivés. Chacun de ces composants offre des avantages différents pour les applications Cloud natives. Les trois plus utiles sont les référentiels, les tableaux et les pipelines. Si les utilisateurs souhaitent gérer leur code source dans une autre pile de référentiels, telle que GitHub, tout en tirant parti de Azure Pipelines et d’autres composants, ce qui est parfaitement possible.

Heureusement, les équipes de développement ont de nombreuses options lors de la sélection d’un référentiel. L’un d’eux est GitHub.

## <a name="github-actions"></a>GitHub Actions

Créé dans 2009, GitHub est un référentiel Web largement populaire pour l’hébergement des projets, de la documentation et du code. De nombreuses grandes entreprises technologiques, telles que Apple, Amazon, Google et les entreprises grand public, utilisent GitHub. GitHub utilise le système de gestion de version distribué Open source nommé git comme base. En premier, il ajoute ensuite son propre ensemble de fonctionnalités, notamment le suivi des défauts, les demandes de fonctionnalités et d’extraction, la gestion des tâches et les wikis pour chaque base de code.

Comme GitHub évolue, il ajoute également des fonctionnalités DevOps. Par exemple, GitHub a son propre pipeline d’intégration continue/de livraison continue (CI/CD), appelé `GitHub Actions` . GitHub actions est un outil d’automatisation de flux de travail basé sur la communauté. Il permet aux équipes DevOps de s’intégrer à leurs outils existants, de combiner et de faire correspondre de nouveaux produits et de se connecter à leur cycle de vie de logiciels, y compris les partenaires CI/CD existants.»

GitHub compte plus de 40 millions utilisateurs, ce qui en fait le plus grand hôte de code source dans le monde. En octobre 2018, Microsoft a acheté GitHub. Microsoft a promis que GitHub reste une [plateforme ouverte](https://techcrunch.com/2018/06/04/microsoft-promises-to-keep-github-independent-and-open/) que tous les développeurs peuvent connecter et étendre. Il continue à fonctionner en tant que société indépendante. GitHub propose des plans pour les comptes d’entreprise, d’équipe, professionnels et gratuits.

## <a name="source-control"></a>Contrôle de code source

L’organisation du code pour une application Cloud Native peut être difficile. Au lieu d’une seule application Giant, les applications Cloud natives ont tendance à être composées d’un Web d’applications de petite taille qui communiquent les unes avec les autres. Comme pour tout le monde informatique, la meilleure organisation du code reste une question ouverte. Il existe des exemples d’applications ayant réussi à utiliser différents types de dispositions, mais deux variantes semblent avoir la plus grande popularité.

Avant d’accéder au contrôle de code source proprement dit, il est probablement judicieux de décider du nombre de projets appropriés. Au sein d’un même projet, il existe une prise en charge de plusieurs dépôts et des pipelines de génération. Les tableaux sont un peu plus compliqués, mais dans certains cas, les tâches peuvent être facilement affectées à plusieurs équipes au sein d’un même projet. Il est possible de prendre en charge des centaines, voire des milliers de développeurs, en dehors d’un seul projet Azure DevOps. Il s’agit probablement de la meilleure approche, car elle fournit un emplacement unique où tous les développeurs peuvent travailler et réduit la confusion liée à la recherche d’une application lorsque les développeurs ne sont pas sûrs dans le projet dans lequel elle réside.

Le fractionnement du code pour les microservices dans le projet Azure DevOps peut être un peu plus complexe.

![Figure 10-3 référentiels simples ou multiples](./media/single-repository-vs-multiple.png)

**Figure 10-3** : un et plusieurs référentiels.

### <a name="repository-per-microservice"></a>Référentiel par Microservice

À première vue, cela semble être l’approche la plus logique pour fractionner le code source pour les microservices. Chaque référentiel peut contenir le code nécessaire à la création d’un microservice. Les avantages de cette approche sont facilement visibles :

1. Les instructions relatives à la création et à la maintenance de l’application peuvent être ajoutées à un fichier Lisez-moi à la racine de chaque référentiel. Lors du basculement dans les référentiels, il est facile de trouver ces instructions, ce qui réduit le temps de rotation pour les développeurs.
2. Chaque service se trouve dans un emplacement logique, facilement accessible en connaissant le nom du service.
3. Les builds peuvent facilement être configurées de telle sorte qu’elles ne sont déclenchées que lorsqu’une modification est apportée au référentiel propriétaire.
4. Le nombre de modifications arrivant dans un référentiel est limité au petit nombre de développeurs qui travaillent sur le projet.
5. La sécurité est facile à configurer en restreignant les dépôts auxquels les développeurs ont des autorisations de lecture et d’écriture.
6. Les paramètres de niveau de référentiel peuvent être modifiés par l’équipe propriétaire, avec un minimum de discussion avec d’autres.

L’une des idées clés derrière les microservices est que les services doivent être siloés et séparés les uns des autres. Lorsque vous utilisez la conception pilotée par domaine pour décider des limites des services, les services jouent le rôle de limites transactionnelles. Les mises à jour de base de données ne doivent pas s’étendre sur plusieurs services. Cette collection de données associées est appelée contexte limité.  Cette idée est reflétée par l’isolation des données de microservice dans une base de données séparée et autonome des autres services. L’objectif est de vous faire un grand sens pour suivre cette idée jusqu’au code source.

Toutefois, cette approche ne présente aucun problème. L’un des problèmes de développement gnarlys de notre temps est la gestion des dépendances. Tenez compte du nombre de fichiers qui composent le `node_modules` répertoire moyen. Une nouvelle installation de tout `create-react-app` ce qui est susceptible de vous apporter des milliers de packages. La question de la gestion de ces dépendances est difficile.

Si une dépendance est mise à jour, les packages en aval doivent également mettre à jour cette dépendance. Malheureusement, cela prend du travail de développement, de manière invariable, le `node_modules` répertoire finit par plusieurs versions d’un package unique, chacune d’entre elles étant une dépendance d’un autre package dont la version est différente selon une cadence légèrement différente. Lors du déploiement d’une application, quelle version d’une dépendance doit être utilisée ? La version actuellement en production ? La version qui est actuellement en version bêta, mais qui est susceptible d’être en production au moment où le consommateur la met en production ? Problèmes difficiles qui ne sont pas résolus en utilisant uniquement des microservices.

Il existe des bibliothèques qui dépendent d’un large éventail de projets. En répartissant les microservices avec un dans chaque référentiel, les dépendances internes peuvent être résolues le mieux à l’aide du référentiel interne, Azure Artifacts. Les builds pour les bibliothèques poussent leurs versions les plus récentes dans Azure Artifacts à des fins de consommation interne. Le projet en aval doit toujours être mis à jour manuellement pour dépendre des packages récemment mis à jour.

Un autre inconvénient se présente pour le déplacement du code entre les services. Bien qu’il soit intéressant de croire que la première division d’une application en microservices est correcte à 100%, la réalité est que rarement, nous sommes prescients pour ne pas faire d’erreur de division de service. Ainsi, les fonctionnalités et le code qui les pilote doivent passer de service à service : référentiel au référentiel. En cas de Bond d’un référentiel à un autre, le code perd son historique. Il y a de nombreux cas, en particulier dans le cas d’un audit, où l’historique complet sur une partie du code est inestimable.

L’inconvénient final et le plus important est la coordination des modifications. Dans une application true microservices, il ne doit y avoir aucune dépendance de déploiement entre les services. Il doit être possible de déployer les services A, B et C dans n’importe quel ordre, car ils ont un couplage faible. En réalité, cependant, il est parfois souhaitable d’effectuer une modification qui traverse plusieurs dépôts en même temps. Certains exemples incluent la mise à jour d’une bibliothèque pour fermer une brèche de sécurité ou la modification d’un protocole de communication utilisé par tous les services.

Pour effectuer une modification inter-référentiel, vous devez effectuer une validation sur chaque dépôt à la suite. Chaque modification de chaque dépôt doit être demandée et examinée séparément. Cela peut être difficile à coordonner.

Une alternative à l’utilisation de nombreux référentiels consiste à placer tout le code source dans un géant, tout en sachant qu’un référentiel unique.

### <a name="single-repository"></a>Référentiel unique

Dans cette approche, parfois appelée [monorepository](https://danluu.com/monorepo/), tout le code source de chaque service est placé dans le même référentiel. Dans un premier temps, cela semble être une idée terrible qui est susceptible de compliquer le traitement du code source. Il existe toutefois des avantages marqués pour fonctionner de cette façon.

Le premier avantage est qu’il est plus facile de gérer les dépendances entre les projets. Au lieu de s’appuyer sur un flux d’artefact externe, les projets peuvent être importés directement. Cela signifie que les mises à jour sont instantanées et que les versions conflictuelles sont susceptibles d’être détectées au moment de la compilation sur la station de travail du développeur. En effet, le décalage de la partie gauche du test d’intégration.

Lorsque vous déplacez du code entre des projets, il est désormais plus facile de conserver l’historique, car les fichiers sont détectés comme ayant été déplacés au lieu d’être réécrits.

Un autre avantage est qu’il y a un grand nombre de modifications qui peuvent être effectuées dans une seule validation. Cela réduit le temps de traitement des dizaines de modifications à examiner individuellement.

De nombreux outils peuvent effectuer une analyse statique du code pour détecter les pratiques de programmation non sécurisées ou l’utilisation problématique des API. Dans un monde à plusieurs référentiels, chaque dépôt doit être itéré pour rechercher les problèmes qu’il rencontre. Le référentiel unique permet d’exécuter l’analyse en un seul endroit.

L’approche de référentiel unique présente également de nombreux inconvénients. L’une des plus inquiétantes est que la présence d’un référentiel unique soulève des problèmes de sécurité. Si le contenu d’un référentiel est divulgué dans un référentiel par modèle de service, la quantité de code perdue est minime. Avec un référentiel unique, tout ce que l’entreprise possède peut être perdu. Il y a eu de nombreux exemples par le passé et nous avons mis au point les efforts de développement de jeux. Le fait de disposer de plusieurs référentiels réduit la surface d’exposition, ce qui est une caractéristique souhaitable dans la plupart des pratiques de sécurité.

La taille du dépôt unique est susceptible d’être ingérable rapidement. Cela présente des implications intéressantes sur les performances. Il peut s’avérer nécessaire d’utiliser des outils spécialisés tels que le [système de fichiers virtuel pour git](https://vfsforgit.org/), qui a été conçu à l’origine pour améliorer l’expérience des développeurs de l’équipe Windows.

Souvent, l’argument pour l’utilisation d’un référentiel unique se résume à un argument que Facebook ou Google utilisent cette méthode pour la disposition du code source. Si l’approche est suffisante pour ces entreprises, il s’agit certainement de la bonne approche pour toutes les entreprises. La vérité est que peu d’entreprises opèrent sur n’importe quel type de mise à l’échelle de Facebook ou Google. Les problèmes qui se produisent à ces échelles sont différents de ceux auxquels la plupart des développeurs seront confrontés. Ce qui est parfait pour l’OIE peut ne pas être adapté au examinons.

À la fin, l’une ou l’autre solution peut être utilisée pour héberger le code source pour les microservices. Toutefois, dans la plupart des cas, la gestion et la surcharge d’ingénierie du fonctionnement dans un référentiel unique ne valent pas les avantages de Meager. Le fractionnement du code sur plusieurs référentiels favorise une meilleure séparation des préoccupations et encourage l’autonomie entre les équipes de développement.  

### <a name="standard-directory-structure"></a>Structure de répertoires standard

Quel que soit le débat entre les référentiels unique et multiple, chaque service dispose de son propre annuaire. L’une des meilleures optimisations pour permettre aux développeurs de traverser rapidement les projets consiste à conserver une structure de répertoires standard.

![Figure 10-4 structure de répertoire standard pour les services de messagerie et de connexion](./media/dir-struct.png)

**Figure 10-4** : structure de répertoires standard.

Chaque fois qu’un nouveau projet est créé, un modèle qui met en place la structure correcte doit être utilisé. Ce modèle peut également inclure des éléments utiles comme un fichier Lisez-moi squelette et un `azure-pipelines.yml` . Dans toutes les architectures de microservices, un degré élevé d’écart entre les projets rend les opérations en bloc sur les services plus difficiles.

De nombreux outils peuvent fournir la création de modèles pour un répertoire entier, contenant plusieurs répertoires de code source. [Yeoman](https://yeoman.io/) est populaire dans le monde JavaScript et GitHub a récemment publié des [modèles de référentiel](https://github.blog/2019-06-06-generate-new-repositories-with-repository-templates/), qui fournissent la plupart des fonctionnalités.

## <a name="task-management"></a>Gestion des tâches

La gestion des tâches dans un projet peut être difficile. Au départ, il existe des questions innombrables à répondre sur le type de flux de travail à configurer afin de garantir une productivité optimale pour les développeurs.

Les applications Cloud natives ont tendance à être plus petites que les logiciels traditionnels ou, au moins, elles sont divisées en services plus petits. Le suivi des problèmes ou des tâches liées à ces services reste aussi important que pour tout autre projet de logiciel. Personne ne souhaite perdre le suivi d’un élément de travail ou expliquer à un client que son problème n’a pas été correctement enregistré. Les tableaux sont configurés au niveau du projet, mais dans chaque projet, les zones peuvent être définies. Ils permettent de décomposer les problèmes entre plusieurs composants. L’avantage de conserver tout le travail pour l’application entière dans un même emplacement est qu’il est facile de déplacer des éléments de travail d’une équipe à l’autre, car ils sont plus compréhensibles.

Azure DevOps est fourni avec un certain nombre de modèles populaires préconfigurés. Dans la configuration la plus simple, il suffit de savoir ce qui se trouve dans le backlog, les personnes qui travaillent et ce qui est fait. Il est important d’avoir cette visibilité sur le processus de création de logiciels, afin que le travail puisse être classé par ordre de priorité et terminer les tâches signalées au client. Bien sûr, peu de projets logiciels se compensent à un processus aussi simple que `to do` , `doing` et `done` . Il n’est pas certain que les gens commencent à ajouter des étapes comme `QA` ou `Detailed Specification` au processus.

L’une des parties les plus importantes des méthodologies agiles est l’auto-inversion à intervalles réguliers. Ces révisions sont destinées à fournir des informations sur les problèmes auxquels l’équipe est confrontée et sur la façon dont ils peuvent être améliorés. Il s’agit souvent de modifier le déroulement des problèmes et des fonctionnalités par le biais du processus de développement. Ainsi, il est tout à fait sain d’étendre les dispositions des tableaux avec des étapes supplémentaires.

Les étapes dans les tableaux ne sont pas le seul outil organisationnel. En fonction de la configuration du tableau, il existe une hiérarchie d’éléments de travail. L’élément le plus granulaire qui peut apparaître dans un tableau est une tâche. Une tâche prête à l’emploi contient des champs pour un titre, une description, une priorité, une estimation de la quantité de travail restante et la possibilité de créer un lien vers d’autres éléments de travail ou éléments de développement (branches, validations, requêtes de tirage, builds, etc.). Les éléments de travail peuvent être classés dans différentes zones de l’application et des itérations différentes (sprints) pour faciliter leur recherche.

![Figure 10-5 exemple de tâche dans Azure DevOps](./media/task-details.png)

**Figure 10-5** -tâche dans Azure DevOps.

Le champ Description prend en charge les styles normaux attendus (gras, trait de soulignement italique et barré) et la possibilité d’insérer des images. Cela en fait un outil puissant à utiliser lors de la spécification du travail ou des bogues.

Les tâches peuvent être regroupées en fonctionnalités, qui définissent une plus grande unité de travail. Les fonctionnalités, à leur tour, peuvent être [reportées dans des Epics](https://docs.microsoft.com/azure/devops/boards/backlogs/define-features-epics?view=azure-devops). La classification des tâches de cette hiérarchie facilite grandement la compréhension de la fermeture d’une grande fonctionnalité.

![Figure 10-6 types d’éléments de travail configurés par défaut dans le modèle de processus de base](./media/board-issue-types.png)

**Figure 10-6** -élément de travail dans Azure DevOps.

Il existe différents types de vues dans les problèmes de Azure Boards. Les éléments qui ne sont pas encore planifiés s’affichent dans le Backlog. À partir de là, elles peuvent être assignées à un sprint. Un sprint est une zone horaire pendant laquelle une quantité de travail est attendue. Ce travail peut inclure des tâches, mais également la résolution des tickets. Dans ce cas, le sprint entier peut être géré à partir de la section de la carte du sprint. Cet affichage montre comment le travail progresse et comprend un graphique d’avancement pour permettre une estimation en perpétuelle mise à jour de si le sprint est réussi.

![Figure 10-7 un tableau avec un sprint défini](./media/sprint-board.png)

**Figure 10-7** -carte dans Azure DevOps.

À l’heure actuelle, il est évident qu’il y a une grande quantité d’énergie dans les tableaux dans Azure DevOps. Pour les développeurs, il existe des vues faciles sur ce qui est utilisé. Pour les chefs de projet dans le cadre du travail à venir, ainsi qu’une vue d’ensemble du travail existant. Pour les responsables, il y a beaucoup de rapports sur la réapprovisionnement et la capacité. Malheureusement, il n’y a rien de magique concernant les applications Cloud natives qui éliminent le besoin de suivre le travail. Toutefois, si vous devez effectuer le suivi du travail, il existe quelques endroits où l’expérience est meilleure que dans Azure DevOps.

## <a name="cicd-pipelines"></a>Pipelines CI/CD

Presque aucun changement dans le cycle de vie du développement de logiciels n’a été si révolutionnaire en ce qui concerne l’avènement de l’intégration continue (CI) et de la livraison continue (CD). La génération et l’exécution de tests automatisés sur le code source d’un projet dès qu’une modification est archivée dans intercepte les erreurs rapidement. Avant l’avènement des builds d’intégration continue, il ne serait pas rare d’extraire du code du référentiel et de déterminer qu’il n’a pas réussi les tests ou qu’ils n’ont pas pu être générés. Cela a entraîné le suivi de la source de la rupture.

Traditionnellement, l’expédition de logiciels vers l’environnement de production nécessitait une documentation complète et une liste d’étapes. Chacune de ces étapes devait être effectuée manuellement dans un processus très sujet aux erreurs.

![Figure 10-8 liste de contrôle](./media/checklist.png)

**Figure 10-8** -liste de vérification.

La sœur de l’intégration continue est la livraison continue dans laquelle les packages créés récemment sont déployés dans un environnement. Le processus manuel ne peut pas être mis à l’échelle pour correspondre à la vitesse de développement, de sorte que l’automatisation devient plus importante. Les listes de vérification sont remplacées par des scripts qui peuvent exécuter les mêmes tâches plus rapidement et de manière plus précise que n’importe quel homme.

L’environnement de livraison continue peut être un environnement de test ou, comme c’est le cas de nombreuses grandes entreprises technologiques, il peut s’agir de l’environnement de production. Ce dernier requiert un investissement dans des tests de haute qualité qui peuvent donner la certitude qu’une modification ne va pas interrompre la production pour les utilisateurs. De la même façon que l’intégration continue a détecté des problèmes dans le code de livraison précoce en continu qui interceptent les problèmes au début du processus de déploiement.

L’importance de l’automatisation du processus de création et de distribution est accentuée par les applications Cloud natives. Les déploiements se produisent plus fréquemment et dans un plus grand nombre d’environnements, si bien qu’il est impossible de déployer manuellement les bordures.

### <a name="azure-builds"></a>Versions Azure

Azure DevOps fournit un ensemble d’outils permettant de rendre l’intégration et le déploiement continus plus faciles que jamais. Ces outils se trouvent sous Azure Pipelines. La première d’entre elles est Azure builds, qui est un outil permettant d’exécuter des définitions de build basées sur YAML à l’échelle. Les utilisateurs peuvent apporter leurs propres ordinateurs de build (idéal pour si la build requiert un environnement de configuration méticuleuse) ou utiliser un ordinateur à partir d’un pool actualisé en permanence de machines virtuelles hébergées sur Azure. Ces agents de build hébergés sont préinstallés avec un large éventail d’outils de développement pour non seulement le développement .NET, mais aussi tout du développement de Java à python vers iPhone.

DevOps comprend une large gamme de définitions de build prêtes à l’emploi qui peuvent être personnalisées pour n’importe quelle Build. Les définitions de build sont définies dans un fichier appelé `azure-pipelines.yml` et archivé dans le référentiel afin de pouvoir être gérées avec le code source. Il est ainsi beaucoup plus facile d’apporter des modifications au pipeline de build dans une branche, car les modifications peuvent être vérifiées uniquement dans cette branche. Un exemple `azure-pipelines.yml` de création d’une application web ASP.net sur l’ensemble de l’infrastructure est illustré à la Figure 10-9.

```yml
name: $(rev:r)

variables:
  version: 9.2.0.$(Build.BuildNumber)
  solution: Portals.sln
  artifactName: drop
  buildPlatform: any cpu
  buildConfiguration: release
  
pool:
  name: Hosted VS2017
  demands:
  - msbuild
  - visualstudio
  - vstest

steps:
- task: NuGetToolInstaller@0
  displayName: 'Use NuGet 4.4.1'
  inputs:
    versionSpec: 4.4.1

- task: NuGetCommand@2
  displayName: 'NuGet restore'
  inputs:
    restoreSolution: '$(solution)'

- task: VSBuild@1
  displayName: 'Build solution'
  inputs:
    solution: '$(solution)'
    msbuildArgs: '-p:DeployOnBuild=true -p:WebPublishMethod=Package -p:PackageAsSingleFile=true -p:SkipInvalidConfigurations=true -p:PackageLocation="$(build.artifactstagingdirectory)\\"'
    platform: '$(buildPlatform)'
    configuration: '$(buildConfiguration)'

- task: VSTest@2
  displayName: 'Test Assemblies'
  inputs:
    testAssemblyVer2: |
     **\$(buildConfiguration)\**\*test*.dll
     !**\obj\**
     !**\*testadapter.dll
    platform: '$(buildPlatform)'
    configuration: '$(buildConfiguration)'

- task: CopyFiles@2
  displayName: 'Copy UI Test Files to: $(build.artifactstagingdirectory)'
  inputs:
    SourceFolder: UITests
    TargetFolder: '$(build.artifactstagingdirectory)/uitests'

- task: PublishBuildArtifacts@1
  displayName: 'Publish Artifact'
  inputs:
    PathtoPublish: '$(build.artifactstagingdirectory)'
    ArtifactName: '$(artifactName)'
  condition: succeededOrFailed()
```

**Figure 10-9** : exemple Azure-pipelines. yml

Cette définition de build utilise un certain nombre de tâches intégrées qui rendent la création de builds aussi simple que la création d’un ensemble LEGO (plus simple que le géant Millennium Falcon). Par exemple, la tâche NuGet restaure les packages NuGet, tandis que la tâche VSBuild appelle les outils de génération Visual Studio pour effectuer la compilation réelle. Des centaines de tâches différentes sont disponibles dans Azure DevOps, avec des milliers d’autres qui sont gérés par la communauté. Il est probable que, quelle que soit la tâche de génération que vous souhaitez exécuter, quelqu’un en ait déjà créé un.

Les builds peuvent être déclenchées manuellement, par un archivage, selon une planification ou par l’achèvement d’une autre Build. Dans la plupart des cas, la création à chaque archivage est souhaitable. Les builds peuvent être filtrées de sorte que les différentes builds s’exécutent sur différentes parties du référentiel ou sur différentes branches. Cela permet des scénarios tels que l’exécution de builds rapides avec un test réduit sur les demandes de tirage et l’exécution d’une suite de régression complète sur le Trunk de nuit.

Le résultat final d’une build est une collection de fichiers connus sous le nom d’artefacts de Build. Ces artefacts peuvent être passés à l’étape suivante du processus de génération ou ajoutés à un flux d’artefact Azure, de sorte qu’ils peuvent être utilisés par d’autres builds.

### <a name="azure-devops-releases"></a>Versions d’Azure DevOps

Les builds s’occupent de la compilation du logiciel dans un package livrable, mais les artefacts doivent toujours être envoyés à un environnement de test pour effectuer une livraison continue. Pour ce faire, Azure DevOps utilise un outil distinct appelé releases. L’outil releases utilise la bibliothèque des tâches qui étaient disponibles pour la génération, mais introduit un concept de « étapes ». Une étape est un environnement isolé dans lequel le package est installé. Par exemple, un produit peut utiliser un environnement de développement, d’assurance qualité et de production. Le code est distribué en permanence dans l’environnement de développement dans lequel les tests automatisés peuvent être exécutés sur ce dernier. Une fois que ces tests réussissent, la publication passe dans l’environnement AQ pour les tests manuels. Enfin, le code est poussé vers la production où il est visible par tous.

![Figure 10-10 exemple de pipeline de mise en production avec phases de développement, d’assurance qualité et de production](./media/release-pipeline.png)

**Figure 10-10** -pipeline de mise en version

Chaque étape de la build peut être automatiquement déclenchée par la fin de la phase précédente. Toutefois, dans de nombreux cas, cela n’est pas souhaitable. Le déplacement du code en production peut nécessiter l’approbation d’une personne. L’outil releases prend en charge cette opération en autorisant les approbateurs à chaque étape du pipeline de mise en production. Des règles peuvent être définies de sorte qu’une personne spécifique ou un groupe de personnes doive se déconnecter d’une version avant de passer en production. Ces portes permettent d’effectuer des contrôles de qualité manuels et également de respecter les exigences réglementaires liées au contrôle des opérations de production.

### <a name="everybody-gets-a-build-pipeline"></a>Tout le monde obtient un pipeline de build

Il n’y a aucun coût à la configuration de plusieurs pipelines de génération. il est donc avantageux d’avoir au moins un pipeline de build par Microservice. Dans l’idéal, les microservices peuvent être déployés indépendamment dans n’importe quel environnement, de sorte que chacun d’eux puisse être libéré via son propre pipeline sans que la masse de code non lié soit parfaite. Chaque pipeline peut avoir son propre ensemble d’approbations autorisant des variations dans le processus de génération pour chaque service.

### <a name="versioning-releases"></a>Versions de versioning

L’un des inconvénients de l’utilisation de la fonctionnalité de versions est qu’elle ne peut pas être définie dans un `azure-pipelines.yml` fichier archivé. Il existe de nombreuses raisons pour lesquelles vous pouvez souhaiter utiliser des définitions de version par branche pour inclure un squelette de version dans votre modèle de projet. Heureusement, le travail est en cours de développement d’une partie de la prise en charge des étapes dans le composant Build. C’est ce qu’on appelle la version à plusieurs étapes et la [première version est désormais disponible](https://devblogs.microsoft.com/devops/whats-new-with-azure-pipelines/)!

>[!div class="step-by-step"]
>[Précédent](azure-security.md) 
> [Suivant](feature-flags.md)
