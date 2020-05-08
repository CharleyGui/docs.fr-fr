---
title: Définition du Cloud Native
description: En savoir plus sur les piliers fondamentaux qui fournissent le socle pour les systèmes natifs du Cloud
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 33977ff736fc5cbfcf86ed6479e8d0b927b87a63
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895614"
---
# <a name="defining-cloud-native"></a>Définition du Cloud Native

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Arrêtez ce que vous êtes en train de faire et du texte dix de vos collègues. Demandez-lui de définir le terme « cloud native ». Bonne chance, vous obtiendrez huit réponses différentes.

Cloud Native concerne la modification de la façon dont nous pensons à la construction de systèmes d’entreprise essentiels.

Les systèmes Cloud natifs sont conçus pour adopter un changement rapide, une grande échelle et une résilience.

La Fondation Cloud Native Computing fournit une [définition officielle](https://github.com/cncf/foundation/blob/master/charter.md):

> *Les technologies Cloud-natives permettent aux organisations de créer et d’exécuter des applications évolutives dans des environnements dynamiques et modernes, tels que des clouds publics, privés et hybrides. Les conteneurs, les maillages de service, les microservices, l’infrastructure immuable et les API déclaratives illustrent cette approche.*

> *Ces techniques permettent aux systèmes faiblement couplés qui sont résilients, gérables et observables. Combinée à une automatisation robuste, elle permet aux ingénieurs d’apporter des modifications très importantes et prévisibles avec un acharnement minimal.*

Les applications sont devenues de plus en plus complexes avec les utilisateurs qui demandent de plus en plus. Les utilisateurs attendent une réactivité rapide, des fonctionnalités novatrices et des temps d’arrêt nuls. Les problèmes de performances, les erreurs récurrentes et l’incapacité à se déplacer rapidement ne sont plus acceptables. Ils seront facilement déplacés vers votre concurrent.

Cloud native est une grande partie de la *Vitesse* et de l' *agilité*. Les systèmes d’entreprise évoluent de l’activation des fonctionnalités métier aux armes de transformation stratégique, accélérant ainsi la rapidité et la croissance de l’entreprise. Il est impératif de mettre les idées sur le marché immédiatement.

Voici quelques sociétés qui ont implémenté ces techniques. Réfléchissez à la vitesse, à l’agilité et à l’évolutivité qu’ils ont atteints.

| Company | Expérience |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | A plus de 600 services en production. Déploie cent fois par jour. |
| [Uber](https://eng.uber.com/micro-deploy/) | A plus de 1 000 services en production. Déploie plusieurs milliers de fois par semaine. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Compte plus de 300 services en production. Déploie 1 000 fois par jour. |

Comme vous pouvez le voir, Netflix, uber et WeChat exposent des systèmes qui se composent de centaines de microservices indépendants. Ce style architectural leur permet de répondre rapidement aux conditions du marché. Ils peuvent mettre à jour instantanément de petites zones d’une application en temps réel et complexes, et mettre à l’échelle individuellement ces zones en fonction des besoins.

La vitesse et l’agilité du Cloud Native proviennent d’un certain nombre de facteurs. Le plus important est l’infrastructure cloud. Cinq piliers fondamentaux supplémentaires, illustrés à la figure 1-3, fournissent également socle pour les systèmes natifs du Cloud.

![Piliers natifs du Cloud](./media/cloud-native-foundational-pillars.png)

**Figure 1-3**. Piliers natifs du Cloud

Prenons un certain temps pour mieux comprendre l’importance de chaque pilier.

## <a name="the-cloud"></a>Le Cloud...

Les systèmes Cloud natifs tirent pleinement parti du modèle de service Cloud.

Conçu pour prospérer dans un environnement Cloud dynamique et virtualisé, ces systèmes font largement appel à l’infrastructure de calcul [PaaS (Platform as a service)](https://azure.microsoft.com/overview/what-is-paas/) et aux services gérés. Ils considèrent l’infrastructure *sous-jacente comme étant* approvisionnée en quelques minutes et redimensionnée, mise à l’échelle, déplacée ou détruite à la demande, via l’automatisation.

Considérez le concept DevOps largement accepté des [animaux et des bovins](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313). Dans un centre de données traditionnel, les serveurs sont traités comme des *animaux familiers*: un ordinateur physique, avec un nom explicite et un soignent pour. Vous mettez à l’échelle en ajoutant des ressources supplémentaires sur le même ordinateur (montée en puissance). Si le serveur devient malade, vous devez le remettre en état d’intégrité. Si le serveur devient indisponible, tout le monde le remarque.

Le modèle de service des *bovins* est différent. Vous configurez chaque instance comme un ordinateur virtuel ou un conteneur. Ils sont identiques et reçoivent un identificateur système tel que service-01, service-02, etc. Vous pouvez mettre à l’échelle en créant davantage d’entre elles (montée en charge). Lorsque l’un d’eux devient indisponible, personne ne le remarque.

Le modèle bovins intègre l' *infrastructure immuable*. Les serveurs ne sont pas réparés ni modifiés. En cas de défaillance ou de mise à jour, il est détruit et un nouveau est approvisionné, le tout à l’aide de l’automatisation.

Les systèmes Cloud natifs adoptent le modèle de service des bovins. Ils continuent à s’exécuter au fur et à mesure que l’infrastructure est mise à l’échelle, sans tenir compte des machines sur lesquelles elles sont exécutées.

La plateforme Cloud Azure prend en charge ce type d’infrastructure hautement élastique avec des fonctionnalités de mise à l’échelle automatique, de réparation automatique et de surveillance.

## <a name="modern-design"></a>Conception moderne

Comment conceviez-vous une application Cloud Native ? À quoi ressemble votre architecture ? Quels sont les principes, les modèles et les meilleures pratiques que vous respectez ? Quelles sont les préoccupations en matière d’infrastructure et de fonctionnement ?

### <a name="the-twelve-factor-application"></a>Application à 12 facteurs

L' [application à 12 facteurs](https://12factor.net/)est une méthodologie largement acceptée pour la construction d’applications basées sur le Cloud. Il décrit un ensemble de principes et de pratiques que les développeurs suivent pour créer des applications optimisées pour les environnements Cloud modernes. Une attention particulière est accordée à la portabilité entre les environnements et l’automatisation déclarative.

Bien qu’applicables à n’importe quelle application Web, de nombreux praticiens la considèrent comme une base solide pour la création d’applications Cloud natives. Les systèmes basés sur ces principes peuvent être déployés et mis à l’échelle rapidement et ajouter des fonctionnalités pour réagir rapidement aux changements de marché.

Le tableau suivant met en évidence la méthodologie à douze facteurs :

|    |  Factor | Explication  |
| :-------- | :-------- | :-------- |
| 1 | Base de code | Une seule base de code pour chaque microservice, stockée dans son propre référentiel. Suivi avec le contrôle de version, il peut être déployé dans plusieurs environnements (AQ, intermédiaire, production). |
| 2 | Dépendances | Chaque microservice isole et conditionne ses propres dépendances, en adoptant des modifications sans affecter l’ensemble du système. |
| 3 | Configurations  | Les informations de configuration sont déplacées hors du microservice et sont externalisées à l’aide d’un outil de gestion de la configuration en dehors du code. Le même déploiement peut se propager dans les environnements avec la configuration correcte appliquée.  |
| 4 | Services de stockage | Les ressources auxiliaires (magasins de données, caches, courtiers de messages) doivent être exposées via une URL adressable. Cela découple la ressource de l’application, ce qui lui permet d’être interchangeable.  |
| 5 | Build, Release, exécuter | Chaque version doit appliquer une séparation stricte entre les étapes de génération, de mise en œuvre et d’exécution. Chaque doit être marqué d’un ID unique et prendre en charge la possibilité d’effectuer une restauration. Les systèmes d’intégration continue et de CD modernes aident à respecter ce principe. |
| 6 | Processus | Chaque microservice doit s’exécuter dans son propre processus, isolé des autres services en cours d’exécution. Externaliser l’État requis sur un service de sauvegarde, tel qu’un cache distribué ou un magasin de données. |
| 7 | Liaison de port | Chaque microservice doit être autonome avec ses interfaces et fonctionnalités exposées sur son propre port. Cela permet d’isoler les autres microservices. |
| 8 | Accès concurrentiel | Les services sont mis à l’échelle sur un grand nombre de petits processus identiques (copies) au lieu de mettre à l’échelle une seule grande instance sur la machine la plus puissante disponible. |
| 9 | Disposability | Les instances de service doivent être jetables, favorisant des Démarrages rapides pour augmenter les possibilités d’évolutivité et les arrêts progressifs pour que le système reste dans un état correct. Les conteneurs de l’arrimeur avec un orchestrateur répondent fondamentalement à cette exigence. |
| 10 | Parité dev/prod | Conservez les environnements tout au long du cycle de vie des applications comme possible, en évitant les raccourcis coûteux. Ici, l’adoption de conteneurs peut contribuer de façon considérable en promouvant le même environnement d’exécution. |
| 11 | Journalisation | Traitez les journaux générés par les microservices en tant que flux d’événements. Traitez-les avec une agrégation d’événements et Propagez les données aux outils de gestion des journaux et de l’exploration de données, comme Azure Monitor ou Splunk, et enfin un archivage à long terme. |
| 12 | Processus d’administration | Exécuter des tâches d’administration/de gestion en tant que processus unique. Les tâches peuvent inclure le nettoyage des données et l’extraction des analytiques pour un rapport. Les outils qui exécutent ces tâches doivent être appelés à partir de l’environnement de production, mais séparément de l’application. |

Dans le livre, [au-delà de l’application à douze facteurs](https://content.pivotal.io/blog/beyond-the-twelve-factor-app), l’auteur Kevin Hoffman détaille chacun des 12 facteurs originaux (écrit en 2011). En outre, le livre fournit trois facteurs supplémentaires qui reflètent la conception d’applications Cloud modernes du jour.

|    |  Nouveau facteur | Explication  |
| :-------- | :-------- | :-------- |
| 13 | API en premier | Faites de tout un service. Supposons que votre code sera consommé par un client frontal, une passerelle ou un autre service. |
| 14 | Télémétrie | Sur une station de travail, vous bénéficiez d’une visibilité détaillée de votre application et de son comportement. Dans le Cloud, vous ne le pouvez pas. Assurez-vous que votre conception comprend la collecte des données de surveillance, spécifiques à un domaine et à l’intégrité/au système. |
| 15 | Authentification/autorisation  | Implémentez l’identité à partir du début. Envisagez [les fonctionnalités RBAC (contrôle d’accès en fonction du rôle)](https://docs.microsoft.com/azure/role-based-access-control/overview) disponibles dans les clouds publics.  |

Nous allons nous référer à la plupart des plus de 12 facteurs dans ce chapitre et dans le livre.

### <a name="critical-design-considerations"></a>Considérations relatives à la conception critique

Outre les conseils fournis dans le cadre de la méthodologie de douze facteurs, vous devez prendre plusieurs décisions de conception critiques lors de la construction de systèmes distribués.

*Communication*

Comment les applications clientes frontales communiquent-elles avec les services principaux back-end ? Autorisez-vous la communication directe ? Ou pouvez-vous faire abstraction des services principaux avec une façade de passerelle qui assure la flexibilité, le contrôle et la sécurité ?

Comment les services centraux principaux communiquent-ils entre eux ? Autorisez-vous les appels HTTP directs qui mènent au couplage et à l’impact sur les performances et l’agilité ? Ou peut-être envisagez-vous une messagerie découplée avec des technologies de file d’attente et de rubrique ?

La communication est traitée en détail dans le chapitre 4, *modèles de communication natifs du Cloud*.

*Résilience*

Une architecture de microservices déplace votre système du processus in-process vers la communication réseau hors processus. Dans une architecture distribuée, que se passe-t-il quand le service B ne répond pas à un appel réseau du service A ? Ou bien, que se passe-t-il lorsque le service C devient temporairement indisponible et que les autres services qui l’appellent sont bloqués ?

La résilience est traitée en détail dans le chapitre 6, *résilience Cloud-Native*.

*Données distribuées*

Par défaut, chaque microservice encapsule ses propres données, exposant les opérations via son interface publique. Si c’est le cas, comment interroger les données ou implémenter une transaction sur plusieurs services ?

Les données distribuées sont traitées en détail dans le chapitre 5, *modèles de données natifs du Cloud*.

*Identité*

Comment votre service identifie-t-il les personnes qui y accèdent et les autorisations dont il dispose ?

L’identité est traitée en détail dans le chapitre 8, *identité*.

## <a name="microservices"></a>Microservices

Les systèmes Cloud natifs intègrent des microservices, un style architectural populaire pour la construction d’applications modernes.

Créé comme un ensemble distribué de petits services indépendants qui interagissent via une infrastructure partagée, les microservices partagent les caractéristiques suivantes :

- Chaque implémente une fonctionnalité métier spécifique dans un contexte de domaine plus large.

- Chaque est développé de façon autonome et peut être déployé indépendamment.

- Chaque est autonome et incorpore sa propre technologie de stockage de données (SQL, NoSQL) et la plateforme de programmation.

- Chaque s’exécute dans son propre processus et communique avec d’autres personnes à l’aide de protocoles de communication standard tels que HTTP/HTTPs, WebSockets ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).

- Elles se composent ensemble pour former une application.

La figure 1-4 compare une approche d’application monolithique avec une approche de microservices. Notez comment le monolithe se compose d’une architecture en couches, qui s’exécute dans un processus unique. Il utilise généralement une base de données relationnelle. Toutefois, l’approche de microservices sépare les fonctionnalités en services indépendants qui incluent la logique et les données. Chaque microservice héberge son propre magasin de banques.

![Déploiement monolithique et microservices](./media/monolithic-vs-microservices.png)

**Figure 1-4.** Déploiement monolithique et microservices

Notez comment les microservices favorisent le principe « une base de code, une application » de l' [application à 12 facteurs](https://12factor.net/), abordé plus haut dans le chapitre.

> *Le \#facteur 1 spécifie «un code base unique pour chaque microservice, stocké dans son propre référentiel. Suivi avec le contrôle de version, il peut être déployé dans plusieurs environnements.*

### <a name="why-microservices"></a>Intérêt des microservices

Les microservices offrent de l’agilité.

Plus haut dans ce chapitre, nous avons comparé une application de commerce électronique créée comme un monolithe à celle-ci avec des microservices. Dans l’exemple, nous avons vu des avantages clairs :

- Chaque microservice a un cycle de vie autonome et peut évoluer indépendamment et le déployer fréquemment. Vous n’avez pas besoin d’attendre une version trimestrielle pour déployer une nouvelle fonctionnalité ou une mise à jour. Vous pouvez mettre à jour une petite zone d’une application complexe avec moins de risques de perturber l’ensemble du système.

- Chaque microservice peut être mis à l’échelle indépendamment. Au lieu de mettre à l’échelle l’application entière en tant qu’unité unique, vous augmentez la charge des services qui requièrent davantage de puissance de traitement ou de bande passante réseau. Cette approche fine de la mise à l’échelle offre un meilleur contrôle de votre système et permet de réduire les coûts globaux lorsque vous mettez à l’échelle des parties de votre système, et non pas de tout.

Les microservices .net sont un excellent guide de référence pour comprendre les microservices [: architecture pour les applications .net en conteneur](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook). Le livre explore en profondeur la conception et l’architecture de microservices. Il s’agit d’un complément pour une [architecture de référence de microservice à pile complète](https://github.com/dotnet-architecture/eShopOnContainers) , disponible en téléchargement gratuit à partir de Microsoft.

### <a name="developing-microservices"></a>Développement de microservices

Les microservices peuvent être créés avec n’importe quelle plateforme de développement moderne.

La plateforme Microsoft .NET Core est un excellent choix. Gratuit et open source, il dispose de nombreuses fonctionnalités intégrées pour simplifier le développement de microservices. .NET Core est multiplateforme. Les applications peuvent être générées et exécutées sur Windows, macOS et la plupart des versions de Linux.

.NET Core est très performant et a bien été évalué par rapport à node. js et à d’autres plateformes concurrentes. Il est intéressant de faire en sorte que [TechEmpower](https://www.techempower.com/) ait mené un ensemble complet de [tests de performances](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) sur de nombreuses plateformes et infrastructures d’application Web. .NET Core est évalué dans le Top 10, bien au-dessus de node. js et d’autres plates-formes concurrentes.

.NET Core est géré par Microsoft et la communauté .NET sur GitHub.

## <a name="containers"></a>Containers

De nos jours, il est naturel d’entendre le terme *conteneur* mentionné dans toute conversation concernant le *Cloud Native*. Dans le livre, le [Cloud Native patterns](https://www.manning.com/books/cloud-native-patterns), auteur Cornelia Davis observe cela, « les conteneurs sont un excellent activateur des logiciels natifs du Cloud ». Le Cloud Native Computing Foundation place le conteneur de microservices en tant que première étape de leur [carte de piste Cloud Native](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) pour les entreprises qui commencent leur parcours Cloud-native.

Le conteneur d’un microservice est simple et simple. Le code, ses dépendances et le runtime sont empaquetés dans un fichier binaire appelé [image de conteneur](https://docs.docker.com/glossary/?term=image). Les images sont stockées dans un [Registre de conteneurs](https://caylent.com/container-registries/), qui agit en tant que référentiel ou bibliothèque pour les images. Un registre peut être situé sur votre ordinateur de développement, dans votre centre de données ou dans un cloud public. L’arrimeur gère lui-même un registre public par le biais de l' [ancrage Hub](https://hub.docker.com/). Le Cloud Azure dispose d’un [Registre de conteneurs](https://azure.microsoft.com/services/container-registry/) pour stocker des images de conteneur à proximité des applications Cloud qui les exécuteront.

Si nécessaire, vous transformez l’image en instance de conteneur en cours d’exécution. L’instance s’exécute sur tout ordinateur sur lequel est installé un moteur d' [exécution de conteneur](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) . Vous pouvez avoir autant d’instances du service en conteneur que nécessaire.

La figure 1-5 montre trois microservices différents, chacun dans son propre conteneur, s’exécutant sur un seul hôte.

![plusieurs conteneurs s’exécutant sur un hôte de conteneurs](./media/hosting-mulitple-containers.png)

**Figure 1-5**. plusieurs conteneurs s’exécutant sur un hôte de conteneurs

Notez que chaque conteneur gère son propre ensemble de dépendances et d’exécution, ce qui peut être différent. Ici, nous voyons différentes versions du microservice du produit qui s’exécutent sur le même hôte. Chaque conteneur partage une partie du système d’exploitation, de la mémoire et du processeur de l’hôte sous-jacent, mais est isolée les unes des autres.

Notez la manière dont le modèle de conteneur adopte le principe de « dépendances » de l' [application à douze facteurs](https://12factor.net/).

> *Le \#facteur 2 spécifie que chaque microservice isole et conditionne ses propres dépendances, en adoptant des modifications sans affecter l’ensemble du système.»*

Les conteneurs prennent en charge les charges de travail Linux et Windows. Azure Cloud adopte les deux. Ce qui est intéressant, c’est qu’il s’agit de Linux, et non de Windows Server, qui est devenu le système d’exploitation le plus populaire dans Azure.

Bien qu’il existe plusieurs fournisseurs de conteneurs, l’arrimeur a capturé la part du marché de lion. L’entreprise a mis en place le déplacement du conteneur logiciel. Elle est devenue la norme de facto pour l’empaquetage, le déploiement et l’exécution d’applications Cloud natives.

### <a name="why-containers"></a>Pourquoi les conteneurs ?

Les conteneurs assurent la portabilité et garantissent la cohérence entre les environnements. En encapsulant tout dans un package unique, vous *isolez* le microservice et ses dépendances de l’infrastructure sous-jacente.

Vous pouvez déployer ce même conteneur dans n’importe quel environnement ayant le moteur d’exécution de l’ancrage. Les charges de travail en conteneur éliminent également les dépenses liées à la préconfiguration de chaque environnement avec des infrastructures, des bibliothèques logicielles et des moteurs d’exécution.

En partageant le système d’exploitation sous-jacent et les ressources de l’hôte, les conteneurs ont un encombrement bien plus faible qu’une machine virtuelle complète. La taille plus petite augmente la *densité*, ou le nombre de microservices, qu’un hôte donné peut exécuter en même temps.

### <a name="container-orchestration"></a>Orchestration de conteneurs

Tandis que les outils tels que l’amarrage créent des images et exécutent des conteneurs, vous avez également besoin d’outils pour les gérer. La gestion des conteneurs s’effectue à l’aide d’un programme logiciel spécial appelé Orchestrator de conteneur. En cas de fonctionnement à l’échelle, l’orchestration de conteneur est essentielle.

La figure 1-6 montre les tâches de gestion fournies par les orchestrateurs de conteneurs.

![Ce que font les orchestrateurs de conteneurs](./media/what-container-orchestrators-do.png)

**Figure 1-6**. Ce que font les orchestrateurs de conteneurs

Le tableau suivant décrit les tâches d’orchestration courantes.

|  Tâches | Explication  |
| :-------- | :-------- |
| Planification | Approvisionner automatiquement des instances de conteneur.|
| Affinité/anti-affinité | Approvisionner des conteneurs à proximité ou éloignés les uns des autres, ce qui contribue à la disponibilité et aux performances. |
| Surveillance de l’intégrité | Détectez et corrigez automatiquement les défaillances.|
| Basculement | Reconfigurer automatiquement l’instance défaillante sur des machines saines.|
| Mise à l'échelle | Ajoutez ou supprimez automatiquement l’instance de conteneur pour répondre à la demande.|
| Mise en réseau | Gérez une superposition de mise en réseau pour la communication de conteneur.|
| Découverte de service | Activez les conteneurs pour les localiser.|
| Mises à niveau propagées | Coordonner les mises à niveau incrémentielles avec un déploiement sans temps d’arrêt. Annule automatiquement les modifications problématiques.|

Notez comment les orchestrateurs adoptent les principes de disposability et d’accès concurrentiel de l' [application à 12 facteurs](https://12factor.net/), abordés plus haut dans ce chapitre.

> *Le \#facteur 9 spécifie que les instances de service doivent être jetables, favorisant ainsi les Démarrages rapides afin d’augmenter les possibilités d’évolutivité et les arrêts progressifs pour que le système reste dans un état correct. Les conteneurs de l’arrimeur avec un orchestrateur répondent fondamentalement à cette exigence.»*

> *Factor \#8 spécifie que les services sont mis à l’échelle sur un grand nombre de petits processus identiques (copies) au lieu de mettre à l’échelle une seule grande instance sur la machine la plus puissante disponible.»*

Bien que plusieurs orchestrateurs de conteneurs existent, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) est devenu la norme de facto pour le monde Cloud-native. Il s’agit d’une plate-forme portable, extensible et open source pour la gestion des charges de travail en conteneur.

Vous pouvez héberger votre propre instance de Kubernetes, mais vous serez alors responsable de l’approvisionnement et de la gestion de ses ressources, ce qui peut être complexe. Le Cloud Azure offre Kubernetes en tant que service managé, [service Kubernetes Azure (AKS)](https://azure.microsoft.com/services/kubernetes-service/). Un service géré vous permet de tirer pleinement parti de ses fonctionnalités, sans avoir à l’installer ni à le maintenir à jour.

Azure Kubernetes services est abordé en détail dans le chapitre 2, *mise à l’échelle des applications Cloud natives*.

## <a name="backing-services"></a>Services de stockage

Les systèmes Cloud natifs dépendent de nombreuses ressources accessoires différentes, telles que les magasins de données, les courtiers de messages, la surveillance et les services d’identité. Ces services sont appelés [services de stockage](https://12factor.net/backing-services).

 La figure 1-7 illustre de nombreux services de stockage courants consommés par les systèmes Cloud natifs.

![Services de stockage courants](./media/common-backing-services.png)

**Figure 1-7**. Services de stockage courants

Les services de sauvegarde promeuvent le principe « abandon » de l' [application à 12 facteurs](https://12factor.net/), décrite plus haut dans le chapitre.

>*Le \#facteur 6* spécifie que chaque microservice doit s’exécuter dans son propre processus, isolé des autres services en cours d’exécution. Externaliser l’État requis sur un service de sauvegarde, tel qu’un cache distribué ou un magasin de données.»

Vous pouvez héberger vos propres services de stockage, mais vous serez alors responsable de la gestion des licences, de l’approvisionnement et de la gestion de ces ressources.

Les fournisseurs de Cloud offrent un large éventail de *services de stockage gérés.* Au lieu de détenir le service, il vous suffit de l’utiliser. Le fournisseur opère la ressource à l’échelle et assume la responsabilité des performances, de la sécurité et de la maintenance. La surveillance, la redondance et la disponibilité sont intégrées au service. Les fournisseurs prennent entièrement en charge leurs services gérés : ouvrez un ticket pour résoudre votre problème.

Les systèmes Cloud natifs favorisent les services de stockage gérés des fournisseurs de Cloud. Les économies en temps et en main-d’œuvre sont très intéressantes. Le risque opérationnel lié à l’hébergement de vos propres problèmes peut être rapidement coûteux.

Une meilleure pratique consiste à traiter un service de sauvegarde en tant que *ressource attachée*, liée de manière dynamique à un microservice avec des informations (URL et informations d’identification) stockées dans une configuration externe. Ce guide est écrit dans l’application à [12 facteurs](https://12factor.net/), décrite plus haut dans le chapitre.

>*Factor \#4* spécifie que les services de stockage doivent être exposés via une URL adressable. Cela découple la ressource de l’application, ce qui lui permet d’être interchangeable.»

>*Factor \#3* spécifie que les informations de configuration sont déplacées hors du microservice et externalisées via un outil de gestion de la configuration en dehors du code.»

Avec ce modèle, un service de sauvegarde peut être attaché et détaché sans modification du code. Vous pouvez promouvoir un microservice de l’AQ en un environnement intermédiaire. Vous mettez à jour la configuration du microservice pour pointer vers les services de stockage dans un environnement intermédiaire et injectez les paramètres dans votre conteneur par le biais d’une variable d’environnement.

Les fournisseurs de Cloud fournissent des API qui vous permettent de communiquer avec leurs services de stockage propriétaires. Ces bibliothèques encapsulent la plomberie et la complexité. En communiquant directement avec ces API, vous associez étroitement votre code au service de sauvegarde. Il est recommandé d’isoler les détails d’implémentation de l’API du fournisseur. Introduisez une couche d’intermédiation ou une API intermédiaire qui expose des opérations génériques à votre code de service. Ce couplage faible vous permet de permuter un service de sauvegarde pour un autre ou de déplacer votre code vers un cloud public différent sans avoir à apporter de modifications au code du service principal.

Les services de stockage sont présentés en détail dans le chapitre 5, les *modèles de données natifs du Cloud*et le chapitre 4, *modèles de communication natifs dans le Cloud*.

## <a name="automation"></a>Automatisation

Comme vous l’avez vu, les systèmes Cloud natifs intègrent des microservices, des conteneurs et une conception de système moderne pour obtenir une vitesse et une agilité. Mais ce n’est qu’une partie de l’histoire. Comment approvisionner les environnements Cloud sur lesquels ces systèmes s’exécutent ? Comment déployez-vous rapidement des fonctionnalités et des mises à jour d’application ? Comment faire pour arrondir l’image complète ?

Entrez la pratique d' [infrastructure en tant que code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)ou IaC.

Avec IaC, vous automatisez l’approvisionnement de la plateforme et le déploiement d’applications. Vous appliquez essentiellement des pratiques de conception de logiciels, telles que le test et la gestion des versions, à vos pratiques DevOps. Votre infrastructure et vos déploiements sont automatisés, cohérents et reproductibles.

### <a name="automating-infrastructure"></a>Automatisation de l’infrastructure

Des outils comme [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/), Terraform et [Azure CLI](https://docs.microsoft.com/cli/azure/), vous permettent de générer un script de façon déclarative de l’infrastructure cloud dont vous avez besoin. Les noms de ressources, les emplacements, les capacités et les secrets sont paramétrables et dynamiques. Le script est géré et archivé dans le contrôle de code source en tant qu’artefact de votre projet. Vous appelez le script pour approvisionner une infrastructure cohérente et reproductible dans des environnements système, comme l’assurance qualité, la mise en lots et la production.

En coulisses, IaC est idempotent, ce qui signifie que vous pouvez exécuter le même script sur et sans effets secondaires. Si l’équipe doit apporter une modification, elle modifie et réexécute le script. Seules les ressources mises à jour sont affectées.

Dans l’article [qu’est-ce que l’infrastructure en tant que code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), l’auteur Sam Guckenheimer décrit comment, les équipes qui implémentent IaC peuvent fournir rapidement et à grande échelle des environnements stables. Les équipes évitent la configuration manuelle des environnements et appliquent la cohérence en représentant l’état souhaité de leurs environnements via du code. Les déploiements d’infrastructure avec IaC sont reproductibles et évitent les problèmes d’exécution dus à une dérive de la configuration ou à des dépendances manquantes. Les équipes DevOps peuvent collaborer avec un ensemble unifié de pratiques et d’outils pour fournir des applications et leur infrastructure de prise en charge rapidement, de manière fiable et à grande échelle.»

### <a name="automating-deployments"></a>Automatisation des déploiements

L' [application à 12 facteurs](https://12factor.net/), abordée précédemment, appelle des étapes distinctes lors de la transformation du code complet en une application en cours d’exécution.

> *Facteur \#5* spécifie que chaque version doit appliquer une séparation stricte entre les étapes de la build, de la mise en œuvre et de l’exécution. Chaque doit être marqué d’un ID unique et prendre en charge la possibilité d’effectuer une restauration.»

Les systèmes d’intégration continue et de CD modernes aident à respecter ce principe. Ils fournissent des étapes de déploiement distinctes et permettent de garantir un code cohérent et de qualité accessible aux utilisateurs.

La figure 1-8 illustre la séparation au sein du processus de déploiement.

![Étapes de déploiement dans un pipeline CI/CD](./media/build-release-run-pipeline.png)

**Figure 1-8**. Étapes de déploiement dans un pipeline CI/CD

Dans l’illustration précédente, portez une attention particulière à la séparation des tâches.

Le développeur construit une fonctionnalité dans son environnement de développement, en itérant au sein de ce que l’on appelle la « boucle interne » de code, d’exécution et de débogage. Une fois terminé, ce code fait l’objet d’un *Push* dans un référentiel de code, tel que GitHub, Azure DevOps ou bitbucket.

L’envoi (push) déclenche une étape de génération qui transforme le code en artefact binaire. Le travail est implémenté avec un pipeline d' [intégration continue (ci)](https://martinfowler.com/articles/continuousIntegration.html) . Il génère, teste et empaquette automatiquement l’application.

L’étape de mise en production récupère l’artefact binaire, applique les informations de configuration de l’environnement et de l’application externes et produit une version immuable. La version est déployée dans un environnement spécifié. Le travail est implémenté avec un pipeline de [livraison continue (CD)](https://martinfowler.com/bliki/ContinuousDelivery.html) . Chaque version doit être identifiable. Vous pouvez indiquer « ce déploiement exécute la version 2.1.1 de l’application ».

Enfin, la fonctionnalité publiée est exécutée dans l’environnement d’exécution cible. Les mises en production sont immuables, ce qui signifie que toute modification doit créer une nouvelle mise en production.

En appliquant ces pratiques, les organisations ont radicalement évolué la manière dont elles accompagnent les logiciels. De nombreuses versions trimestrielles ont été déplacées vers des mises à jour à la demande. L’objectif est de détecter les problèmes au début du cycle de développement lorsqu’ils sont moins coûteux à résoudre. Plus la durée entre les intégrations est longue, plus les problèmes de résolution sont élevés.  Avec la cohérence dans le processus d’intégration, les équipes peuvent valider les modifications de code plus fréquemment, ce qui permet une meilleure collaboration et une meilleure qualité des logiciels.

### <a name="azure-pipelines"></a>Azure Pipelines

Le Cloud Azure comprend un nouveau service CI/CD, intitulé [Azure pipelines](https://azure.microsoft.com/services/devops/pipelines/), qui fait partie de l’offre [Azure DevOps](https://azure.microsoft.com/services/devops/) présentée dans la figure 1-9.

![Azure Pipelines dans DevOps](./media/devops-components.png)

**Figure 1-9**. Offres Azure DevOps

Azure Pipelines est un service Cloud qui combine l’intégration continue (CI) et la livraison continue (CD). Vous pouvez tester, générer et envoyer automatiquement votre code à n’importe quelle cible.

Vous définissez votre pipeline dans le code d’un fichier YAML avec le reste du code de votre application.

- La version du pipeline est gérée avec votre code et suit la même structure de branchement.
- Vous pouvez valider vos modifications à l’aide de révisions de code dans les requêtes de tirage et les stratégies de build de branche.
- Chaque branche que vous utilisez peut personnaliser la stratégie de génération en modifiant le fichier Azure-pipelines. yml.
- Le fichier de pipeline est archivé dans le contrôle de version et peut être examiné en cas de problème.

Le service Azure Pipelines prend en charge la plupart des fournisseurs GIT et peut générer des pipelines de déploiement pour les applications écrites sur les plateformes Linux, macOS ou Windows. Il prend en charge Java, .NET, JavaScript, Python, PHP, Go, XCode et C++.

>[!div class="step-by-step"]
>[Précédent](introduction.md)
>[suivant](candidate-apps.md)
