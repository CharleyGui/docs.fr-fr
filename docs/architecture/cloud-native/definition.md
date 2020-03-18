---
title: Définition du Cloud Native
description: Renseignez-vous sur les piliers fondamentaux qui fournissent le socle des systèmes cloud-indigènes
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 27191a67b2964ac2e1636a4d7dc55d5314b78439
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401570"
---
# <a name="defining-cloud-native"></a>Définir le nuage natif

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Arrêtez ce que vous faites et envoyez un texto à 10 de vos collègues. Demandez-leur de définir le terme « Cloud Native ». Bonne chance que vous obteniez huit réponses différentes. Fait intéressant, dans six mois, à mesure que les technologies et les pratiques du cloud évolueront, leur définition évoluera également.

Cloud natif est tout au sujet de changer la façon dont nous pensons à construire des systèmes d’affaires critiques.

Les systèmes cloud-indigènes sont conçus pour englober le changement rapide, à grande échelle et la résilience.

La Cloud Native Computing Foundation fournit une [définition officielle](https://github.com/cncf/foundation/blob/master/charter.md):

> *Les technologies cloud-natives permettent aux organisations de construire et d’exécuter des applications évolutives dans des environnements modernes et dynamiques tels que les nuages publics, privés et hybrides. Les conteneurs, les maillages de service, les microservices, les infrastructures immuables et les API déclaratives illustrent cette approche.*

> *Ces techniques permettent des systèmes vaguement couplés qui sont résilients, gérables et observables. Combinés à une automatisation robuste, ils permettent aux ingénieurs d’apporter des changements à fort impact fréquemment et de façon prévisible avec un minimum de labeur.*

Les applications sont devenues de plus en plus complexes avec des utilisateurs exigeant de plus en plus. Les utilisateurs s’attendent à une réactivité rapide, des fonctionnalités innovantes et à zéro temps d’arrêt. Les problèmes de performance, les erreurs récurrentes et l’incapacité de se déplacer rapidement ne sont plus acceptables. Ils se déplaceront facilement vers votre concurrent.

Cloud natif est beaucoup sur la *vitesse* et *l’agilité*. Les systèmes d’affaires évoluent de la capacité d’affaires de habilitation à des armes de transformation stratégique, en accélérant la vitesse et la croissance de l’entreprise. Il est impératif d’obtenir des idées sur le marché immédiatement.

Voici quelques entreprises qui ont mis en œuvre ces techniques. Pensez à la vitesse, l’agilité et l’évolutivité qu’ils ont atteint.

| Company | Expérience |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | A plus de 600 services en production. Déploiement cent fois par jour. |
| [Uber](https://eng.uber.com/micro-deploy/) | Plus de 1 000 services sont stockés en production. Déploie plusieurs milliers de builds chaque semaine. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | A plus de 300 services en production. Fait près de 1000 changements par jour. |

Comme vous pouvez le voir, Netflix, Uber et WeChat exposent des systèmes qui se composent de centaines de microservices indépendants. Ce style architectural leur permet de répondre rapidement aux conditions du marché. Ils peuvent instantanément mettre à jour de petites zones d’une application complexe et en direct, et les échelles individuellement au besoin.

La vitesse et l’agilité des nuages natifs proviennent d’un certain nombre de facteurs. L’infrastructure cloud est avant tout avant tout. Cinq autres piliers fondamentaux indiqués dans la figure 1-3 constituent également le socle des systèmes natifs du nuage.

![Piliers fondamentaux cloud-indigènes](./media/cloud-native-foundational-pillars.png)

**Figure 1-3**. Piliers fondamentaux cloud-indigènes

Prenons le temps de mieux comprendre l’importance de chaque pilier.

## <a name="the-cloud"></a>Le nuage...

Les systèmes cloud-natifs tirent pleinement parti du modèle de service cloud.

Conçus pour prospérer dans un environnement cloud dynamique et virtualisé, ces systèmes utilisent largement [Platform as a Service (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) d’infrastructure de calcul et de services gérés. Ils traitent l’infrastructure sous-jacente comme *jetable* - provisionnée en quelques minutes et redimensionnée, réduite, déplacée ou détruite à la demande - par l’automatisation.

Considérez le concept largement accepté DevOps de [Pets vs Cattle](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313). Dans un centre de données traditionnel, les serveurs sont traités comme *des animaux de compagnie*: une machine physique, un nom significatif, et soignés. Vous évoluez en ajoutant plus de ressources à la même machine (mise à l’échelle). Si le serveur tombe malade, vous l’allaitez de nouveau à la santé. Si le serveur devient indisponible, tout le monde s’en rend compte.

Le modèle de service *de bétail* est différent. Vous disposez chaque instance comme une machine ou un conteneur virtuel. Ils sont identiques et ont attribué un identifiant de système tel que Service-01, Service-02, et ainsi de suite. Vous évoluez en créant plus d’entre eux (mise à l’échelle). Quand on devient indisponible, personne ne s’en rend compte.

Le modèle du bétail englobe *l’infrastructure immuable.* Les serveurs ne sont pas réparés ou modifiés. Si l’on échoue ou nécessite une mise à jour, il est détruit et un nouveau est fourni - le tout fait via l’automatisation.

Les systèmes cloud-indigènes adoptent le modèle de service de bétail. Ils continuent à fonctionner à mesure que l’infrastructure s’insinuvait ou sortent sans égard aux machines sur lesquelles ils fonctionnent.

La plate-forme cloud Azure prend en charge ce type d’infrastructure très élastique avec des capacités automatiques d’échelle, d’auto-guérison et de surveillance.

## <a name="modern-design"></a>Conception moderne

Comment concevriez-vous une application cloud-native ? À quoi ressemblerait votre architecture ? À quels principes, modèles et pratiques exemplaires adhéreriez-vous? Quelles seraient les préoccupations en matière d’infrastructure et d’exploitation?

### <a name="the-twelve-factor-application"></a>L’application à douze facteurs

Une méthodologie largement acceptée pour la construction d’applications basées sur le cloud est [l’application Douze facteurs](https://12factor.net/). Il décrit un ensemble de principes et de pratiques que les développeurs suivent pour construire des applications optimisées pour les environnements cloud modernes. Une attention particulière est accordée à la portabilité entre les environnements et l’automatisation déclarative.

Bien qu’il soit applicable à toute application Web, de nombreux praticiens la considèrent comme une base solide pour la construction d’applications cloud-native. Les systèmes fondés sur ces principes peuvent se déployer et s’étendre rapidement et ajouter des fonctionnalités pour réagir rapidement aux changements du marché.

Le tableau suivant met en évidence la méthodologie des douze facteurs :

|    |  Factor | Explication  |
| :-------- | :-------- | :-------- |
| 1 | Code Base | Une base de code unique pour chaque microservice, stockée dans son propre référentiel. Suivi avec contrôle de version, il peut se déployer dans plusieurs environnements (QA, Mise en scène, production). |
| 2 | Les dépendances | Chaque microservice isole et emballe ses propres dépendances, embrassant les changements sans avoir d’impact sur l’ensemble du système. |
| 3 | Configurations  | Les informations de configuration sont déplacées hors du microservice et externalisées via un outil de gestion de configuration en dehors du code. Le même déploiement peut se propager à travers les environnements avec la configuration correcte appliquée.  |
| 4 | Services d’accompagnement | Les ressources auxiliaires (magasins de données, caches, courtiers de messages) doivent être exposées via une URL adressable. Cela découple la ressource de l’application, ce qui lui permet d’être interchangeable.  |
| 5 | Construire, Libérer, Exécuter | Chaque version doit appliquer une séparation stricte à travers la construction, la libération et les étapes d’exécution. Chacun doit être étiqueté avec une pièce d’identité unique et soutenir la possibilité de faire marche arrière. Les systèmes CI/CD modernes aident à remplir ce principe. |
| 6 | Processus | Chaque microservice doit s’exécuter dans son propre processus, isolé des autres services en cours d’exécution. Externes de l’état requis à un service d’accompagnement tel qu’un cache distribué ou un magasin de données. |
| 7 | Liaison de port | Chaque microservice doit être autonome avec ses interfaces et fonctionnalités exposées sur son propre port. Cela permet d’isoler les autres microservices. |
| 8 | Accès concurrentiel | Les services s’étendent sur un grand nombre de petits processus identiques (copies) par opposition à l’échelle d’une seule grande instance sur la machine la plus puissante disponible. |
| 9 | Disposition | Les instances de service devraient être jetables, favorisant les startups rapides pour augmenter les possibilités d’évolutivité et les arrêts gracieux de laisser le système dans un état correct. Les conteneurs Docker ainsi qu’un orchestrateur satisfont intrinsèquement à cette exigence. |
| 10 | Parité Dev/Prod | Gardez les environnements à travers le cycle de vie de l’application aussi semblables que possible, en évitant les raccourcis coûteux. Ici, l’adoption de conteneurs peut grandement contribuer en promouvant le même environnement d’exécution. |
| 11 | Journalisation | Traitez les journaux générés par les microservices sous forme de flux d’événements. Traitez-les avec un agrégateur d’événements et propagez les données à des outils de gestion des données et des journaux comme Azure Monitor ou Splunk et éventuellement archivage à long terme. |
| 12 | Processus d’administration | Exécuter des tâches administratives/gestion comme processus ponctuaux. Les tâches peuvent inclure le nettoyage des données et l’analyse de traction pour un rapport. Les outils exécutant ces tâches doivent être invoqués à partir de l’environnement de production, mais séparément de l’application. |

Dans le livre [Beyond the Twelve-Factor App](https://content.pivotal.io/blog/beyond-the-twelve-factor-app), l’auteur Kevin Hoffman détaille chacun des 12 facteurs originaux (écrits en 2011). En outre, le livre fournit trois facteurs supplémentaires qui reflètent la conception moderne de l’application cloud d’aujourd’hui.

|    |  Nouveau facteur | Explication  |
| :-------- | :-------- | :-------- |
| 13 | API d’abord | Faites de tout un service. Supposons que votre code sera consommé par un client front-end, passerelle, ou un autre service. |
| 14 | Télémétrie | Sur un poste de travail, vous avez une grande visibilité sur votre application et son comportement. Dans le nuage, vous n’avez pas. Assurez-vous que votre conception comprend la collecte de données de surveillance, spécifiques au domaine et de santé/système. |
| 15 | Authentification/ Autorisation  | Implémentez l’identité dès le début. Considérez les fonctionnalités [RBAC (contrôle d’accès basé sur les rôles)](https://docs.microsoft.com/azure/role-based-access-control/overview) disponibles dans les nuages publics.  |

Nous nous référerons à bon nombre des 12 facteurs de ce chapitre et tout au long du livre.

### <a name="critical-design-considerations"></a>Considérations de conception critiques

Au-delà des directives fournies à partir de la méthodologie à douze facteurs, il y a plusieurs décisions de conception critiques que vous devez prendre lors de la construction de systèmes distribués.

*Communication*

Comment les applications client frontales communiqueront-elles avec les services de base adossés ? Autoriserez-vous la communication directe? Ou, pourriez-vous abstraction des services back-end avec une façade passerelle qui offre de la flexibilité, le contrôle et la sécurité?

Comment les services de base back-end communiqueront-ils entre eux? Autoriserez-vous les appels HTTP directs qui mènent au couplage et à l’impact des performances et de l’agilité ? Ou pourriez-vous envisager la messagerie découplée avec les technologies de file d’attente et de sujet?

La communication est couverte en détail Chapitre 4, *Cloud-Native Communication Patterns*.

*Résilience*

Une architecture de microservices déplace votre système de la communication en cours à la communication en réseau. Dans un environnement distribué, que feriez-vous lorsque le service B ne répond pas à un appel du service A? Que se passe-t-il lorsque le service C devient temporairement indisponible et que d’autres services l’appellent empiler et dégrader les performances du système?

La résilience est couverte en détail Chapitre 6, *Cloud-Native Resiliency*.

*Données distribuées*

Par conception, chaque microservice encapsule ses propres données, exposant les opérations via son interface publique. Dans l’affirmative, comment interrogez-vous des données ou implémentez-vous une transaction sur plusieurs services ?

Les données distribuées sont couvertes en détail Chapitre 5, *Cloud-Native Data Patterns*.

*Identité*

Comment votre service identifiera-t-il qui y accède et quelles autorisations ils ont?

L’identité est couverte en détail Chapitre 8, *Identité*.

## <a name="microservices"></a>Microservices

Les systèmes cloud-indigènes embrassent les microservices, un style architectural populaire pour la construction d’applications modernes.

Construits comme un ensemble distribué de petits services indépendants qui interagissent à travers un tissu partagé, les microservices partagent les caractéristiques suivantes :

- Chacun met en œuvre une capacité d’entreprise spécifique dans un contexte de domaine plus large.

- Chacun est développé de manière autonome et peut être déployé indépendamment.

- Chacun est autonome encapsulant sa propre technologie de stockage de données (SQL, NoSQL) et la plate-forme de programmation.

- Chacun fonctionne dans son propre processus et communique avec d’autres en utilisant des protocoles de communication standard tels que HTTP/HTTPS, WebSockets, ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).

- Ils composent ensemble pour former une application.

La figure 1-4 oppose une approche d’application monolithique à une approche de microservices. Notez comment le monolithe est composé d’une architecture en couches, qui s’exécute en un seul processus. Il consomme généralement une base de données relationnelle. L’approche du microservice, cependant, sépare la fonctionnalité en services indépendants qui incluent la logique et les données. Chaque microservice héberge sa propre datastore.

![Déploiement monolithique par rapport aux microservices](./media/monolithic-vs-microservices.png)

**Figure 1-4.** Déploiement monolithique par rapport aux microservices

Notez comment les microservices font la promotion du principe « Une base de code, une application » de la [demande à douze facteurs](https://12factor.net/), dont il a été question plus tôt dans le chapitre.

> *Le \#facteur 1 spécifie « Une base de code unique pour chaque microservice, stockée dans son propre référentiel. Suivi avec le contrôle de version, il peut se déployer dans plusieurs environnements."*

### <a name="why-microservices"></a>Intérêt des microservices

Les microservices assurent l’agilité.

Plus tôt dans le chapitre, nous avons comparé une application de commerce électronique construite comme un monolithe à celle avec les microservices. Dans l’exemple, nous avons vu quelques avantages évidents :

- Chaque microservice a un cycle de vie autonome et peut évoluer de façon indépendante et se déployer fréquemment. Vous n’avez pas à attendre une version trimestrielle pour déployer une nouvelle fonctionnalité ou mise à jour. Vous pouvez mettre à jour une petite zone d’une application complexe avec moins de risque de perturber l’ensemble du système.

- Chaque microservice peut évoluer de façon indépendante. Au lieu d’étendre l’ensemble de l’application en tant qu’unité unique, vous n’az pas d’échelle uniquement les services qui nécessitent plus de puissance de traitement ou de bande passante réseau. Cette approche à haute graine à l’échelle fournit un meilleur contrôle de votre système et aide à réduire les coûts globaux que vous échelle des parties de votre système, pas tout.

Un excellent guide de référence pour comprendre les microservices est [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture/). Le livre plonge profondément dans le design et l’architecture des microservices. C’est un compagnon pour une [architecture de référence de microservice pleine pile](https://github.com/dotnet-architecture/eShopOnContainers) disponible en téléchargement gratuit de Microsoft.

### <a name="developing-microservices"></a>Développer des microservices

Les microservices peuvent être créés avec n’importe quelle plate-forme de développement moderne.

La plate-forme Microsoft .NET Core est un excellent choix. Libre et open source, il dispose de nombreuses fonctionnalités intégrées pour simplifier le développement des microservices. .NET Core est multi-plateforme. Les applications peuvent être construites et exécutées sur Windows, macOS, et la plupart des saveurs de Linux.

.NET Core est très performant et a obtenu de bons résultats par rapport à Node.js et d’autres plates-formes concurrentes. Fait intéressant, [TechEmpower](https://www.techempower.com/) a effectué un vaste ensemble de repères de performance sur de nombreuses [plateformes](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) et cadres d’applications Web. .NET Core a marqué dans le top 10 - bien au-dessus de Node.js et d’autres plates-formes concurrentes.

.NET Core est maintenu par Microsoft et la communauté .NET sur GitHub.

## <a name="containers"></a>Containers

Aujourd’hui, il est naturel d’entendre le *conteneur* terme mentionné dans toute conversation concernant *le nuage natif*. Dans le livre, [Cloud Native Patterns](https://www.manning.com/books/cloud-native-patterns), l’auteur Cornelia Davis observe que, "Les conteneurs sont un grand facilitateur de logiciels cloud-native." La Cloud Native Computing Foundation place la conteneurisation des microservices comme première étape de sa [carte Cloud-Native Trail](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) - des conseils pour les entreprises qui commencent leur voyage en nuage.

La conteneurisation d’un microservice est simple et simple. Le code, ses dépendances et le temps d’exécution sont emballés dans un binaire appelé une [image de conteneur](https://docs.docker.com/glossary/?term=image). Les images sont stockées dans un [registre de conteneurs,](https://caylent.com/container-registries/)qui agit comme un dépôt ou une bibliothèque pour les images. Un registre peut être situé sur votre ordinateur de développement, dans votre centre de données ou dans un nuage public. Docker lui-même tient un registre public via [Docker Hub](https://hub.docker.com/). Le cloud Azure dispose [d’un registre des conteneurs](https://azure.microsoft.com/services/container-registry/) pour stocker des images de conteneurs à proximité des applications cloud qui les exécuteront.

En cas de besoin, vous transformez l’image en une instance de conteneur en cours d’exécution. L’instance fonctionne sur n’importe quel ordinateur qui a un moteur [de temps d’exécution de conteneur](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) installé. Vous pouvez avoir autant d’instances du service conteneurisé que nécessaire.

La figure 1-5 montre trois microservices différents, chacun dans son propre conteneur, fonctionnant sur un seul hôte.

![plusieurs conteneurs s’exécutant sur un hôte de conteneurs](./media/hosting-mulitple-containers.png)

**Figure 1-5**. plusieurs conteneurs s’exécutant sur un hôte de conteneurs

Notez comment chaque conteneur maintient son propre ensemble de dépendances et de temps d’exécution, ce qui peut être différent. Ici, nous voyons différentes versions du microservice produit en cours d’exécution sur le même hôte. Chaque conteneur partage une tranche du système d’exploitation, de la mémoire et du processeur d’hôte sous-jacent, mais est isolé les uns des autres.

Notez dans quelle mesure le modèle de conteneurs embrasse le principe des « dépendances » de [l’application douze facteurs](https://12factor.net/).

> *Le \#facteur 2 précise que « chaque microservice isole et emballe ses propres dépendances, embrassant les changements sans avoir d’impact sur l’ensemble du système».*

Les conteneurs prennent en charge les charges de travail Linux et Windows. Le nuage Azure embrasse ouvertement les deux. Fait intéressant, c’est Linux, pas Windows Server, qui est devenu le système d’exploitation le plus populaire en Azure.

Alors que plusieurs vendeurs de conteneurs existent, Docker a capturé la part du lion du marché. La société a été le moteur du mouvement des conteneurs logiciels. Il est devenu la norme de facto pour l’emballage, le déploiement et l’exécution d’applications cloud-native.

### <a name="why-containers"></a>Pourquoi les conteneurs?

Les conteneurs offrent une portabilité et garantissent la cohérence entre les environnements. En encapsulant tout en un seul paquet, vous *isolez* le microservice et ses dépendances de l’infrastructure sous-jacente.

Vous pouvez déployer ce même conteneur dans n’importe quel environnement qui a le moteur De temps d’exécution Docker. Les charges de travail conteneurisées éliminent également les dépenses de pré-configuration de chaque environnement avec des cadres, des bibliothèques de logiciels et des moteurs de temps d’exécution.

En partageant le système d’exploitation sous-jacent et les ressources d’accueil, les conteneurs ont une empreinte beaucoup plus faible qu’une machine virtuelle complète. La plus petite taille augmente la *densité,* ou le nombre de microservices, qu’un hôte donné peut exécuter à un moment donné.

### <a name="container-orchestration"></a>Orchestration de conteneurs

Bien que des outils tels que Docker créent des images et exécutent des conteneurs, vous avez également besoin d’outils pour les gérer. La gestion des conteneurs se fait avec un logiciel spécial appelé un orchestrateur de conteneurs. Lorsqu’il fonctionne à l’échelle, l’orchestration de conteneurs est essentielle.

La figure 1-6 montre les tâches de gestion que les orchestrateurs de conteneurs fournissent.

![Ce que font les orchestrateurs de conteneurs](./media/what-container-orchestrators-do.png)

**Figure 1-6**. Ce que font les orchestrateurs de conteneurs

Le tableau suivant décrit les tâches d’orchestration courantes.

|  Tâches | Explication  |
| :-------- | :-------- |
| Planification | Fourniture automatique d’instances de conteneurs.|
| Affinité/anti-affinité | Conteneurs d’approvisionnement à proximité ou loin les uns des autres, aidant la disponibilité et la performance. |
| Surveillance de l’intégrité | Détectez et corrigez automatiquement les défaillances.|
| Basculement | Automatiquement reprovision échoué instance à des machines saines.|
| Mise à l'échelle | Ajoutez ou supprimez automatiquement l’instance de conteneur pour répondre à la demande.|
| Mise en réseau | Gérer une superposition de réseautage pour la communication des conteneurs.|
| Découverte de service | Permettre aux conteneurs de se localiser les uns les autres.|
| Mises à niveau propagées | Coordonner les mises à niveau incrémentielles avec zéro déploiement en temps d’arrêt. Annulez automatiquement les modifications problématiques.|

Notez comment les orchestrateurs adoptent les principes d’aliénation et de concordance de [l’application à douze facteurs](https://12factor.net/), discutés plus tôt dans le chapitre.

> *Le \#facteur 9 précise que « les instances de service doivent être jetables, favorisant les startups rapides pour augmenter les possibilités d’évolutivité et les arrêts gracieux pour laisser le système dans un état correct. Les conteneurs Docker ainsi qu’un orchestrateur satisfont intrinsèquement à cette exigence.*

> *Le \#facteur 8 précise que « les services s’étendent sur un grand nombre de petits processus identiques (copies) par opposition à l’échelle d’une seule grande instance sur la machine la plus puissante disponible. »*

Bien qu’il existe plusieurs orchestrateurs de conteneurs, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) est devenu la norme de facto pour le monde cloud-natif. Il s’agit d’une plate-forme portable, extensible, open-source pour gérer les charges de travail conteneurisées.

Vous pouvez héberger votre propre exemple de Kubernetes, mais vous seriez responsable de l’approvisionnement et de la gestion de ses ressources - ce qui peut être complexe. Le cloud Azure dispose de Kubernetes comme un service géré, [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). Un service géré vous permet de tirer pleinement parti de ses fonctionnalités, sans avoir à l’installer et à l’entretenir.

Azure Kubernetes Services est couvert en détail Chapitre 2, *Scaling Cloud-Native Applications*.

## <a name="backing-services"></a>Services de soutien

Les systèmes cloud-natifs dépendent de nombreuses ressources auxiliaires différentes, telles que les magasins de données, les courtiers en messages, la surveillance et les services d’identité. Ces services sont connus sous le nom [de services de soutien](https://12factor.net/backing-services).

 La figure 1-7 montre de nombreux services d’accompagnement courants que les systèmes cloud-autochtones consomment.

![Services de soutien communs](./media/common-backing-services.png)

**Figure 1-7**. Services de soutien communs

Les services de soutien favorisent le principe de « l’apatridie » de [l’application à douze facteurs](https://12factor.net/), dont il a été question plus tôt dans le chapitre.

>*Le \#facteur 6* précise que « chaque microservice doit s’exécuter dans son propre processus, isolé des autres services en cours d’exécution. Externes de l’état requis à un service d’accompagnement tel qu’un cache distribué ou un magasin de données.

Vous pourriez héberger vos propres services d’accompagnement, mais vous seriez responsable de l’octroi de licences, de la fourniture et de la gestion de ces ressources.

Les fournisseurs de cloud offrent un assortiment riche de services de *support gérés.* Au lieu de posséder le service, vous le consommez simplement. Le fournisseur exploite la ressource à grande échelle et assume la responsabilité de la performance, de la sécurité et de l’entretien. La surveillance, la redondance et la disponibilité sont intégrées au service. Les fournisseurs prennent pleinement en charge leurs services gérés - ouvrez un billet et ils résolvent votre problème.

Les systèmes cloud-native favorisent les services de support gérés des fournisseurs de cloud. Les économies de temps et de main-d’œuvre sont grandes. Le risque opérationnel d’accueillir le vôtre et de rencontrer des problèmes peut coûter cher rapidement.

Une meilleure pratique consiste à traiter un service d’accompagnement comme une *ressource jointe,* dynamiquement liée à un microservice avec des informations (une URL et des informations d’identification) stockées dans une configuration externe. Ces directives sont énoncées dans la [demande à douze facteurs](https://12factor.net/), discutée plus tôt dans le chapitre.

>*Le \#facteur 4* précise que les services de support "doivent être exposés via une URL adressable. Cela découple la ressource de l’application, ce qui lui permet d’être interchangeable.

>*Le \#facteur 3* précise que « les informations de configuration sont déplacées hors du microservice et externalisées par un outil de gestion de configuration en dehors du code. »

Avec ce modèle, un service de sauvegarde peut être attaché et détaché sans modifications de code. Vous pouvez promouvoir un microservice de l’AQ à un environnement de mise en scène. Vous mettez à jour la configuration du microservice pour indiquer les services d’accompagnement dans la mise en scène et injecter les paramètres dans votre conteneur à travers une variable d’environnement.

Les fournisseurs de cloud vous permettent de communiquer avec leurs services de soutien exclusifs. Ces bibliothèques résument la plomberie et la complexité. Communiquer directement avec ces API couplera étroitement votre code au service d’accompagnement. Il s’agit d’une meilleure pratique pour isoler les détails de mise en œuvre de l’API fournisseur. Introduisez une couche d’intermédiation, ou API intermédiaire, exposant les opérations génériques à votre code de service. Ce couplage lâche vous permet d’échanger un service de sauvegarde contre un autre ou de déplacer votre code vers un cloud public différent sans avoir à apporter des modifications au code de service principal.

Les services d’accompagnement sont discutés en détail Chapitre 5, *Cloud-Native Data Patterns*, et Chapitre 4, *Cloud-Native Communication Patterns*.

## <a name="automation"></a>Automatisation

Comme vous l’avez vu, les systèmes cloud-natifs adoptent des microservices, des conteneurs et la conception moderne du système pour atteindre la vitesse et l’agilité. Mais, ce n’est qu’une partie de l’histoire. Comment approvisionnementz-vous dans les environnements cloud sur lesquels ces systèmes fonctionnent ? Comment déployez-vous rapidement des fonctionnalités et des mises à jour d’applications ? Comment pouvez-vous compléter l’image complète?

Entrez dans la pratique largement acceptée de [l’infrastructure en tant que Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), ou IaC.

Avec IaC, vous automatisez la provision de la plate-forme et le déploiement d’applications. Vous appliquez essentiellement des pratiques d’ingénierie logicielle telles que les tests et la version de vos pratiques DevOps. Votre infrastructure et vos déploiements sont automatisés, cohérents et reproductibles.

### <a name="automating-infrastructure"></a>Automatisation de l’infrastructure

Des outils comme [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/), Terraform et [azure CLI](https://docs.microsoft.com/cli/azure/), vous permettent de script de manière déclarative de l’infrastructure cloud dont vous avez besoin. Les noms de ressources, les emplacements, les capacités et les secrets sont paramétrés et dynamiques. Le script est version et vérifié dans le contrôle source comme un artefact de votre projet. Vous invoquez le script pour fournir une infrastructure cohérente et répétable entre les environnements du système, tels que l’AQ, la mise en scène et la production.

Sous le capot, IaC est idempotent, ce qui signifie que vous pouvez exécuter le même script encore et encore sans effets secondaires. Si l’équipe doit apporter un changement, elle modifie et réexécute le script. Seules les ressources mises à jour sont affectées.

Dans l’article, [Qu’est-ce que l’infrastructure comme code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Auteur Sam Guckenheimer décrit comment, "Les équipes qui mettent en œuvre IaC peut fournir des environnements stables rapidement et à l’échelle. Les équipes évitent la configuration manuelle des environnements et imposent la cohérence en représentant l’état souhaité de leurs environnements via le code. Les déploiements d’infrastructure avec IaC sont reproductibles et préviennent les problèmes de temps d’exécution causés par la dérive de configuration ou les dépendances manquantes. Les équipes de DevOps peuvent travailler ensemble avec un ensemble unifié de pratiques et d’outils pour fournir des applications et leur infrastructure de soutien rapidement, de manière fiable et à grande échelle.

### <a name="automating-deployments"></a>Automatisation des déploiements

[L’application Douze facteurs](https://12factor.net/), discutée plus tôt, appelle à des étapes distinctes lors de la transformation du code terminé en une application en cours d’exécution.

> *Le \#facteur 5* précise que « chaque version doit appliquer une séparation stricte à travers les étapes de construction, de libération et d’exécution. Chacun doit être étiqueté avec une pièce d’identité unique et soutenir la possibilité de revenir en arrière.

Les systèmes CI/CD modernes aident à remplir ce principe. Ils fournissent des étapes de déploiement distinctes et aident à assurer un code cohérent et de qualité facilement accessible aux utilisateurs.

La figure 1-8 indique la séparation tout au long du processus de déploiement.

![Déploiements Étapes dans le pipeline CI/CD](./media/build-release-run-pipeline.png)

**Figure 1-8**. Étapes de déploiement dans un pipeline CI/CD

Dans le chiffre précédent, portez une attention particulière à la séparation des tâches.

Le développeur construit une fonctionnalité dans leur environnement de développement, itérant à travers ce qu’on appelle la « boucle intérieure » du code, de l’exécution et du débogé. Une fois terminé, ce code est *poussé* dans un référentiel de code, comme GitHub, Azure DevOps, ou BitBucket.

La poussée déclenche une étape de construction qui transforme le code en un artefact binaire. Les travaux sont mis en œuvre avec un pipeline [d’intégration continue (CI).](https://martinfowler.com/articles/continuousIntegration.html) Il construit automatiquement, teste et emballe l’application.

L’étape de sortie capte l’artefact binaire, applique des informations externes sur l’application et la configuration de l’environnement, et produit une version immuable. Le rejet est déployé dans un environnement spécifié. Les travaux sont mis en œuvre avec un pipeline [de livraison continue (CD).](https://martinfowler.com/bliki/ContinuousDelivery.html) Chaque version doit être identifiable. Vous pouvez dire : « Ce déploiement est en cours d’exécution Version 2.1.1 de l’application. »

Enfin, la fonction libérée est exécutée dans l’environnement d’exécution cible. Les versions sont immuables, ce qui signifie que toute modification doit créer une nouvelle version.

Appliquant ces pratiques, les organisations ont radicalement évolué leur façon d’expédier des logiciels. Beaucoup sont passés des communiqués trimestriels aux mises à jour à la demande. L’objectif est d’attraper les problèmes au début du cycle de développement quand ils sont moins coûteux à résoudre. Plus la durée entre les intégrations est longue, plus les problèmes deviennent coûteux à résoudre.  Avec la cohérence dans le processus d’intégration, les équipes peuvent valider des modifications de code plus fréquemment, conduisant à une meilleure collaboration et la qualité logicielle.

### <a name="azure-pipelines"></a>Azure Pipelines

Le cloud Azure comprend un nouveau service CI/CD intitulé [Azure Pipelines](https://azure.microsoft.com/services/devops/pipelines/), qui fait partie de l’offre [Azure DevOps](https://azure.microsoft.com/services/devops/) présentée dans la figure 1-9.

![Azure Pipelines à DevOps](./media/devops-components.png)

**Figure 1-9**. Offres Azure DevOps

Azure Pipelines est un service cloud qui allie intégration continue (CI) et livraison continue (CD). Vous pouvez automatiquement tester, construire et expédier votre code à n’importe quelle cible.

Vous définissez votre pipeline dans le code dans un fichier YAML aux côtés du reste du code de votre application.

- Le pipeline est versionné avec votre code et suit la même structure de ramification.
- Vous obtenez la validation de vos modifications grâce à des révisions de code dans les demandes de traction et les stratégies d’accumulation de succursales.
- Chaque branche que vous utilisez peut personnaliser la stratégie de construction en modifiant le fichier azure-pipelines.yml.
- Le fichier de pipeline est contrôlé dans le contrôle de la version et peut faire l’objet d’une enquête en cas de problème.

Le service Azure Pipelines prend en charge la plupart des fournisseurs Git et peut générer des pipelines de déploiement pour des applications écrites sur les plateformes Linux, macOS ou Windows. Il comprend la prise en charge de Java, .NET, JavaScript, Python, PHP, Go, XCode et C.

>[!div class="step-by-step"]
>[Suivant précédent](introduction.md)
>[Next](candidate-apps.md)
