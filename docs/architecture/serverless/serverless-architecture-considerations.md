---
title: Considérations relatives à l’architecture sans serveur-applications sans serveur
description: Comprenez les défis liés à l’architecture des applications sans serveur, de la gestion de l’État et du stockage persistant à la mise à l’échelle, la journalisation, le traçage et les Diagnostics.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 3c07e1149e6af41a6b9a9317238e5c71015d2c4e
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135670"
---
# <a name="serverless-architecture-considerations"></a>Considérations relatives à l’architecture serverless

L’adoption d’une architecture sans serveur est accompagnée de certains défis. Cette section explore certaines des considérations les plus courantes à connaître. Tous ces défis ont des solutions. Comme pour tous les choix d’architecture, la décision d’accéder sans serveur ne doit être effectuée qu’après examen minutieux des avantages et des inconvénients. En fonction des besoins de votre application, vous pouvez décider qu’une implémentation sans serveur n’est pas la bonne solution pour certains composants.

## <a name="managing-state"></a>Gestion de l’état

Les fonctions sans serveur, comme les microservices en général, sont sans état par défaut. L’évitement de l’état permet à un serveur d’être éphémère, de monter en charge et d’assurer la résilience sans point de défaillance central. Dans certains cas, les processus d’entreprise nécessitent un État. Si votre processus requiert un État, deux options s’offrent à vous. Vous pouvez adopter un modèle autre que sans serveur ou interagir avec un service distinct qui fournit l’État. L’ajout de l’État peut compliquer la solution et compliquer la mise à l’échelle, et éventuellement créer un point de défaillance unique. Déterminez avec soin si votre fonction requiert absolument un État. Si la réponse est « oui », déterminez s’il est toujours judicieux de l’implémenter sans serveur.

Il existe plusieurs solutions pour adopter l’État sans compromettre les avantages de l’absence de serveur. Voici quelques-unes des solutions les plus populaires :

- Utiliser un magasin de données temporaire ou un cache distribué, comme ReDim
- Stocker l’État dans une base de données, comme SQL ou CosmosDB
- Gérer l’état via un moteur de workflow comme des [fonctions durables](https://docs.microsoft.com/azure/azure-functions/durable/durable-functions-overview)

En fin de compte, vous devez être conscient de la nécessité de gérer les États au sein des processus que vous envisagez d’implémenter avec sans serveur.

## <a name="long-running-processes"></a>Processus de longue durée

De nombreux avantages de la confiance sans serveur s’appuient sur les processus éphémères. Des temps d’exécution courts permettent au fournisseur sans serveur de libérer plus facilement des ressources à mesure que les fonctions se terminent et partagent des fonctions entre les hôtes. La plupart des fournisseurs de Cloud limitent la durée totale d’exécution de votre fonction à environ 10 minutes. Si votre processus peut durer plus longtemps, vous pouvez envisager une autre implémentation.

Il existe quelques exceptions et solutions. Une solution peut consister à diviser votre processus en composants plus petits qui prennent un temps d’exécution plus court. Si votre processus s’exécute longtemps en raison de dépendances, vous pouvez également envisager un flux de travail asynchrone à l’aide d’une solution comme fonctions durables. Les fonctions durables suspendent et maintiennent l’état de votre processus pendant qu’il attend qu’un processus externe se termine. La gestion asynchrone réduit le temps d’exécution du processus réel.

## <a name="startup-time"></a>Temps de démarrage

Un problème potentiel avec les implémentations sans serveur est le temps de démarrage. Pour économiser les ressources, de nombreux fournisseurs sans serveur créent une infrastructure « à la demande ». Lorsqu’une fonction sans serveur est déclenchée après un certain laps de temps, il peut être nécessaire de créer ou de redémarrer les ressources pour héberger la fonction. Dans certains cas, les démarrages à froid peuvent entraîner des retards de plusieurs secondes. Le temps de démarrage varie entre les fournisseurs et les niveaux de service. Il existe plusieurs approches pour résoudre le temps de démarrage s’il est important de réduire la réussite de l’application.

- Certains fournisseurs permettent aux utilisateurs de payer des niveaux de service qui garantissent que l’infrastructure est « Always on ».
- Implémentez un mécanisme Keep-Alive (exécutez une commande ping sur le point de terminaison pour le garder « éveillé »).
- Utilisez l’orchestration comme Kubernetes avec une approche de fonction en conteneur (l’ordinateur hôte est déjà en cours d’exécution pour que les nouvelles instances soient extrêmement rapides).

## <a name="database-updates-and-migrations"></a>Mises à jour et migrations de base de données

L’un des avantages du code sans serveur est que vous pouvez publier de nouvelles fonctions sans avoir à redéployer l’application entière. Cet avantage peut devenir un inconvénient lorsqu’il y a une base de données relationnelle impliquée. Les modifications apportées aux schémas de base de données sont difficiles à synchroniser avec les mises à jour sans serveur. Des difficultés supplémentaires sont posées lorsque des problèmes se posent et que les modifications doivent être annulées. L’intégrité des données est l’une des raisons pour lesquelles il s’agit d’une bonne pratique pour les microservices et les fonctions sans serveur. Il est possible de déployer des modifications en tant qu’unité unique de calcul et de données. En réalité, de nombreux systèmes hérités sont dotés d’une base de données principale importante qui doit être conciliée avec l’architecture sans serveur.

Une approche courante pour résoudre le contrôle de version de schéma consiste à ne jamais modifier les propriétés et les colonnes existantes, mais plutôt d’ajouter de nouvelles informations. Par exemple, considérez une modification pour passer d’un indicateur « Completed » booléen pour une liste TODO à une « date d’achèvement ». Au lieu de supprimer l’ancien champ, la modification de la base de données :

1. Ajoutez un nouveau champ « date de fin ».
1. Transformez le champ booléen « Completed » en fonction calculée qui évalue si la date de fin est ultérieure à la date actuelle.
1. Ajoutez un déclencheur pour définir la date de fin sur la date actuelle lorsque la valeur booléenne terminée est définie sur true.

La séquence de modifications garantit que le code hérité continue à s’exécuter « en l’instant », tandis que les fonctions sans serveur plus récentes peuvent tirer parti du nouveau champ.

Pour plus d’informations sur les données des architectures sans serveur, consultez [défis et solutions pour la gestion des données distribuées](../microservices/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Mise à l'échelle

Il s’agit d’une idée fausse de l’absence de serveur. Il s’agit en fait de « moins de serveurs ». Le fait qu’il y ait une infrastructure de sauvegarde est important de comprendre quand il s’agit d’une mise à l’échelle. La plupart des plateformes sans serveur fournissent un ensemble de contrôles pour gérer la mise à l’échelle de l’infrastructure en cas d’augmentation de la densité d’événements. Vous pouvez choisir parmi diverses options, mais votre stratégie peut varier en fonction de la fonction. En outre, les fonctions sont généralement exécutées sous un hôte connexe, de sorte que les fonctions sur le même hôte ont les mêmes options d’échelle. Par conséquent, il est nécessaire d’organiser et de déterminer les fonctions qui sont hébergées ensemble en fonction des exigences de mise à l’échelle.

Les règles spécifient souvent la mise à l’échelle (augmentation des ressources de l’ordinateur hôte) et la montée en puissance parallèle (augmenter le nombre d’instances de l’hôte) en fonction des différents paramètres. Les déclencheurs pour les échelles peuvent inclure la planification, les taux de demandes, l’utilisation du processeur et l’utilisation de la mémoire. Des performances supérieures sont souvent supérieures. Les approches basées sur la consommation moins onéreuses peuvent ne pas être mises à l’échelle aussi rapidement lorsque le taux de demandes augmente soudainement. Il existe un compromis entre le paiement d’un « coût d’assurance » et le paiement strict « au fur et à mesure de vos déplacements » et le risque de réponses plus lentes en raison de l’augmentation soudaine de la demande.

## <a name="monitoring-tracing-and-logging"></a>Surveillance, suivi et journalisation

Un aspect souvent négligé de DevOps est l’analyse des applications une fois qu’elles sont déployées. Il est important de disposer d’une stratégie pour la surveillance des fonctions sans serveur. Le plus grand défi est souvent la corrélation ou la reconnaissance lorsqu’un utilisateur appelle plusieurs fonctions dans le cadre de la même interaction. La plupart des plateformes sans serveur autorisent la journalisation de la console qui peut être importée dans des outils tiers. Il existe également des options pour automatiser la collecte des données de télémétrie, générer et suivre des ID de corrélation et surveiller des actions spécifiques pour fournir des informations détaillées. Azure fournit la [plateforme de application Insights](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) avancée pour la surveillance et l’analyse.

## <a name="inter-service-dependencies"></a>Dépendances entre les services

Une architecture sans serveur peut inclure des fonctions qui reposent sur d’autres fonctions. En fait, il n’est pas rare de faire appel à plusieurs services dans une architecture sans serveur dans le cadre d’une interaction ou d’une transaction distribuée. Pour éviter un couplage fort, il est recommandé que les services ne se référencent pas l’un l’autre directement. Lorsque le point de terminaison d’un service doit être modifié, les références directes peuvent entraîner une refactorisation majeure. Une solution recommandée consiste à fournir un mécanisme de détection de service, tel qu’un registre, qui fournit le point de terminaison approprié pour un type de demande. Une autre solution consiste à utiliser des services de messagerie tels que des files d’attente ou des rubriques pour la communication entre les services.

## <a name="managing-failure-and-providing-resiliency"></a>Gestion des défaillances et fourniture de résilience

Il est également important de prendre en compte le *modèle de disjoncteur*: si, pour une raison quelconque, un service continue de tomber en panne, il n’est pas recommandé d’appeler ce service à plusieurs reprises. Au lieu de cela, un autre service est appelé ou un message est retourné jusqu’à ce que l’intégrité du service dépendant soit rétablie. L’architecture sans serveur doit prendre en compte la stratégie de résolution et de gestion des dépendances entre les services.

Pour continuer le modèle de disjoncteur, les services doivent être tolérants aux pannes et résilients. La tolérance de panne fait référence à la possibilité pour votre application de continuer à s’exécuter même après que des exceptions inattendues ou des États non valides ont été rencontrés. La tolérance de panne est généralement une fonction du code lui-même et de la façon dont il est écrit pour gérer les exceptions. La résilience fait référence à la capacité de récupération de l’application contre les défaillances. La résilience est souvent gérée par la plateforme sans serveur. La plateforme doit pouvoir créer une nouvelle instance de fonction sans serveur lorsque l’instance existante échoue. La plateforme doit également être suffisamment intelligente pour arrêter les nouvelles instances lorsque chaque nouvelle instance échoue.

Pour plus d’informations, consultez [implémentation du modèle disjoncteur](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Gestion des versions et déploiements verts/bleus

L’un des principaux avantages de l’absence de serveur est la possibilité de mettre à niveau une fonction spécifique sans avoir à redéployer l’application entière. Pour que les mises à niveau soient réussies, les fonctions doivent être gérées de manière à ce que les services qui les appellent soient acheminés vers la version correcte du code. Une stratégie de déploiement de nouvelles versions est également importante. Une approche courante consiste à utiliser des « déploiements verts/bleus ». Le déploiement vert est la fonction active. Une nouvelle version « Blue » est déployée en production et testée. Lorsque le test réussit, les versions vert et bleu sont échangées de sorte que la nouvelle version est publiée. Si des problèmes sont rencontrés, ils peuvent être permutés. La prise en charge du contrôle de version et des déploiements verts/bleus requiert une combinaison de la création des fonctions pour prendre en charge les modifications de version et l’utilisation de la plateforme sans serveur pour gérer les déploiements.

>[!div class="step-by-step"]
>[Précédent](serverless-architecture.md)
>[suivant](serverless-design-examples.md)
