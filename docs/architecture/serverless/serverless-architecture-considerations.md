---
title: Considérations d’architecture sans serveur - Applications sans serveur
description: Comprendre les défis de l’architecture d’applications sans serveur, de la gestion de l’État et le stockage persistant à l’échelle, l’exploitation forestière, le traçage et le diagnostic.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c856683cf6910be98661e634246cd003b93a6d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522432"
---
# <a name="serverless-architecture-considerations"></a>Considérations relatives à l’architecture serverless

L’adoption d’une architecture sans serveur est accompagnée de certains défis. Cette section examine certaines des considérations les plus courantes dont il faut être au courant. Tous ces défis ont des solutions. Comme avec tous les choix d’architecture, la décision d’aller sans serveur ne doit être prise qu’après avoir soigneusement examiné les avantages et les inconvénients. Selon les besoins de votre application, vous pouvez décider qu’une implémentation sans serveur n’est pas la bonne solution pour certains composants.

## <a name="managing-state"></a>Gestion de l’état

Les fonctions sans serveur, comme avec les microservices en général, sont apatrides par défaut. Éviter l’état permet aux sans serveur d’être éphémères, d’évoluer et de fournir une résilience sans point central d’échec. Dans certaines circonstances, les processus opérationnels exigent l’état. Si votre processus nécessite l’état, vous avez deux options. Vous pouvez adopter un modèle autre que sans serveur, ou interagir avec un service distinct qui fournit l’état. L’ajout d’état peut compliquer la solution et la rendre plus difficile à l’échelle, et potentiellement créer un seul point d’échec. Réfléchissez soigneusement si votre fonction nécessite absolument l’état. Si la réponse est "oui", déterminez s’il est toujours logique de l’implémenter sans serveur.

Il existe plusieurs solutions à adopter l’état sans compromettre les avantages de serverless. Voici quelques-unes des solutions les plus populaires :

- Utilisez un magasin de données temporaire ou un cache distribué, comme Redis
- Stockez l’état dans une base de données, comme SQL ou CosmosDB
- Gérer l’état à travers un moteur de flux de travail comme des fonctions durables

L’essentiel est que vous devez être conscient de la nécessité de toute gestion de l’État dans les processus que vous envisagez de mettre en œuvre sans serveur.

## <a name="long-running-processes"></a>Processus à long terme

De nombreux avantages de serverless s’appuient sur les processus étant éphémères. Les temps courts facilitent la libération des ressources par le fournisseur sans serveur au fur et à mesure que les fonctions se terminent et partagent des fonctions entre les hôtes. La plupart des fournisseurs de cloud limitent le temps total que votre fonction peut exécuter à environ 10 minutes. Si votre processus peut prendre plus de temps, vous pourriez envisager une autre implémentation.

Il y a quelques exceptions et solutions. Une solution peut être de briser votre processus en composants plus petits qui prennent individuellement moins de temps à exécuter. Si votre processus est long en raison de dépendances, vous pouvez également envisager un flux de travail asynchrone en utilisant une solution comme les fonctions durables. Les fonctions durables s’arrêtent et maintiennent l’état de votre processus pendant qu’il attend un processus externe pour se terminer. La manipulation asynchrone réduit le temps que le processus réel s’exécute.

## <a name="startup-time"></a>Temps de démarrage

Une préoccupation potentielle avec les implémentations sans serveur est le temps de démarrage. Pour conserver les ressources, de nombreux fournisseurs sans serveur créent une infrastructure « à la demande ». Lorsqu’une fonction sans serveur est déclenchée après un certain temps, les ressources pour héberger la fonction peuvent devoir être créées ou redémarrées. Dans certaines situations, les départs à froid peuvent entraîner des retards de plusieurs secondes. Le temps de démarrage varie d’un fournisseur à l’autre et d’un niveau de service à l’autre. Il existe quelques approches pour aborder le temps de démarrage s’il est important de minimiser le succès de l’application.

- Certains fournisseurs permettent aux utilisateurs de payer pour les niveaux de service qui garantissent que l’infrastructure est "toujours allumée".
- Mettre en œuvre un mécanisme de maintien en vie (ping le point de terminaison pour le garder "éveillé").
- Utilisez l’orchestration comme Kubernetes avec une approche de fonction conteneurisée (l’hôte est déjà en cours d’exécution afin de tourner de nouvelles instances est extrêmement rapide).

## <a name="database-updates-and-migrations"></a>Mises à jour et migrations de base de données

Un avantage du code sans serveur est que vous pouvez libérer de nouvelles fonctions sans avoir à redéployer l’ensemble de l’application. Cet avantage peut devenir un inconvénient lorsqu’il y a une base de données relationnelle en cause. Les modifications apportées aux schémas de base de données sont difficiles à synchroniser avec des mises à jour sans serveur. D’autres défis sont posés lorsque les choses tournent mal et que les changements doivent être annulés. L’intégrité des données est l’une des raisons pour lesquelles une pratique exemplaire pour les microservices et les fonctions sans serveur est qu’ils possèdent leurs propres données. Il est possible de déployer des modifications en tant qu’unité unique de calcul et de données. La réalité est que de nombreux systèmes hérités disposent d’une grande base de données back-end qui doit être conciliée avec l’architecture sans serveur.

Une approche populaire pour résoudre la version schéma est de ne jamais modifier les propriétés existantes et les colonnes, mais plutôt ajouter de nouvelles informations. Par exemple, envisagez une modification pour passer d’un drapeau Boolean « rempli » pour une liste de todo à une « date terminée ». Au lieu de supprimer l’ancien champ, le changement de base de données :

1. Ajoutez un nouveau champ de « date de sortie ».
1. Transformez le champ Boolean « terminé » en fonction calculée qui évalue si la date d’achèvement est après la date actuelle.
1. Ajoutez un déclencheur pour définir la date de fin à la date actuelle où le Boolean terminé est réglé pour vrai.

La séquence de modifications garantit que le code hérité continue de fonctionner « tel qu’est » tandis que de nouvelles fonctions sans serveur peuvent tirer parti du nouveau champ.

Pour plus d’informations sur les données dans les architectures sans serveur, voir [Défis et solutions pour la gestion des données distribuées](../microservices/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Mise à l'échelle

C’est une idée fausse commune que sans serveur signifie "pas de serveur." C’est en fait "moins de serveur." Le fait qu’il y ait une infrastructure de soutien est important de comprendre quand il s’agit de mise à l’échelle. La plupart des plates-formes sans serveur fournissent un ensemble de contrôles pour gérer la façon dont l’infrastructure devrait évoluer lorsque la densité des événements augmente. Vous pouvez choisir parmi une variété d’options, mais votre stratégie peut varier en fonction de la fonction. En outre, les fonctions sont généralement exécutées sous un hôte connexe, de sorte que les fonctions sur le même hôte ont les mêmes options d’échelle. Il est donc nécessaire d’organiser et de stratégier les fonctions qui sont hébergées ensemble en fonction des exigences d’échelle.

Les règles précisent souvent comment augmenter (augmenter les ressources de l’hôte) et l’échelle (augmenter le nombre d’instances hôtes) en fonction de paramètres variables. Les déclencheurs pour les échelles peuvent inclure le calendrier, les taux de demande, l’utilisation du processeur et l’utilisation de la mémoire. Des performances plus élevées ont souvent un coût plus élevé. Les approches moins coûteuses basées sur la consommation peuvent ne pas évoluer aussi rapidement lorsque le taux de demande augmente soudainement. Il y a un compromis entre le paiement du « coût d’assurance » avant par rapport au paiement strictement « au fur et à mesure » et risque de ralentir les réponses en raison d’une augmentation soudaine de la demande.

## <a name="monitoring-tracing-and-logging"></a>Surveillance, traçage et exploitation forestière

Un aspect souvent négligé de DevOps est la surveillance des applications une fois déployée. Il est important d’avoir une stratégie pour surveiller les fonctions sans serveur. Le plus grand défi est souvent la corrélation, ou de reconnaître quand un utilisateur appelle plusieurs fonctions dans le cadre de la même interaction. La plupart des plates-formes sans serveur permettent la connexion de console qui peut être importée en outils tiers. Il existe également des options pour automatiser la collecte de la télémétrie, générer et suivre les cartes d’ID de corrélation, et surveiller des actions spécifiques pour fournir des informations détaillées. Azure fournit la [plate-forme](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) avancée Application Insights pour la surveillance et l’analyse.

## <a name="inter-service-dependencies"></a>Dépendances inter-services

Une architecture sans serveur peut inclure des fonctions qui s’appuient sur d’autres fonctions. En fait, il n’est pas rare dans une architecture sans serveur d’avoir plusieurs services s’appellent dans le cadre d’une interaction ou d’une transaction distribuée. Pour éviter un couplage fort, il est recommandé que les services ne se référencent pas directement. Lorsque le critère d’évaluation d’un service doit être modifié, des références directes peuvent entraîner une refonte majeure. Une solution suggérée consiste à fournir un mécanisme de découverte de services, comme un registre, qui fournit le point final approprié pour un type de demande. Une autre solution consiste à tirer parti des services de messagerie comme les files d’attente ou des sujets de communication entre les services.

## <a name="managing-failure-and-providing-resiliency"></a>Gérer l’échec et fournir de la résilience

Il est également important de tenir compte du *modèle de disjoncteur*: si, pour une raison quelconque, un service continue d’échouer, il n’est pas conseillé d’appeler ce service à plusieurs reprises. Au lieu de cela, un service alternatif est appelé ou un message retourné jusqu’à ce que la santé du service dépendant soit rétablie. L’architecture sans serveur doit tenir compte de la stratégie de résolution et de gestion des dépendances inter-services.

Pour continuer le circuit-breaker, les services doivent être tolérants et résilients. La tolérance à la faute se réfère à la capacité de votre demande de continuer à fonctionner même après des exceptions inattendues ou des états invalides sont rencontrés. La tolérance à la faute est généralement fonction du code lui-même et de la façon dont il est écrit pour gérer les exceptions. La résilience se réfère à la capacité de l’application est à récupérer des défaillances. La résilience est souvent gérée par la plate-forme sans serveur. La plate-forme devrait être en mesure de faire tourner vers le haut d’une nouvelle instance de fonction sans serveur lorsque l’existant échoue. La plate-forme devrait également être assez intelligente pour arrêter de faire tourner de nouveaux cas lorsque chaque nouvelle instance échoue.

Pour plus d’informations, voir [Mise en œuvre du modèle De disjoncteur](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Déploiements en version et vert/bleu

Un avantage majeur de serverless est la possibilité de mettre à niveau une fonction spécifique sans avoir à redéployer l’ensemble de l’application. Pour que les mises à niveau soient réussies, les fonctions doivent être versions de sorte que les services qui les appellent soient acheminés vers la bonne version du code. Une stratégie de déploiement de nouvelles versions est également importante. Une approche courante consiste à utiliser des « déploiements verts/bleus ». Le déploiement vert est la fonction actuelle. Une nouvelle version «bleue» est déployée à la production et testée. Lorsque le test passe, les versions verte et bleue sont échangées afin que la nouvelle version arrive en direct. Si des problèmes sont rencontrés, ils peuvent être échangés en arrière. La version de soutien et les déploiements verts/bleus nécessitent une combinaison de la rédaction des fonctions pour tenir compte des modifications de version et de travailler avec la plate-forme sans serveur pour gérer les déploiements. Une approche possible est d’utiliser des procurations, qui sont décrites dans le chapitre de la [plate-forme sans serveur Azure.](azure-functions.md#proxies)

>[!div class="step-by-step"]
>[Suivant précédent](serverless-architecture.md)
>[Next](serverless-design-examples.md)
