---
title: Moderniser vos applications avec la surveillance et la télémétrie
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Moderniser vos applications avec la surveillance et télémétrie
ms.date: 04/30/2018
ms.openlocfilehash: 5bffb336234f63dca150acc9ef31f9efa2e3937b
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758622"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Moderniser vos applications avec la surveillance et la télémétrie

Lorsque vous exécutez une application en production, il est essentiel que vous avez des informations sur les performances de votre application. Il effectue un haut niveau ? Les utilisateurs bénéficient d’erreurs ou est l’application stable et fiable ? Vous avez besoin d’analyse des performances enrichie, puissantes alertes et des tableaux de bord pour vous assurer que votre application est disponible et fonctionnent comme prévu. Vous devez également être en mesure de voir rapidement s’il existe un problème, déterminez combien de clients est affectés et effectuer une analyse des causes racines pour rechercher et corriger le problème.

## <a name="monitor-your-application-with-application-insights"></a>Surveiller votre application avec Application Insights

Application Insights est un service de gestion des performances des applications (APM) extensible destiné aux développeurs web travaillant sur plusieurs plateformes. Il permet de surveiller votre application web dynamique. Application Insights détecte automatiquement les anomalies de performances. Il inclut des outils d’analytique puissants pour vous aider à diagnostiquer les problèmes et pour vous aider à comprendre ce que les utilisateurs font avec votre application. Application Insights est conçu pour vous aider à améliorer en permanence les performances et la convivialité. Il fonctionne pour les applications sur un large éventail de plateformes, y compris .NET, Node.js et J2EE, si hébergées en local ou dans le cloud. Application Insights s’intègre à vos processus DevOps et offre des points de connexion à une variété d’outils de développement.

Figure 4-10 illustre un exemple de comment Application Insights surveille votre application et comment il expose ces informations à un tableau de bord.

![Tableau de bord de surveillance application Insights](./media/image10.png)

> **Figure 4-10.** Tableau de bord de surveillance application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Surveiller votre infrastructure de Docker avec Analytique de journal et de sa solution Container Monitoring

[Analytique de journal Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) fait partie de la [globale de solution de surveillance de Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Il est également un service [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Analytique de journal surveille le cloud et des environnements locaux (OMS en local) pour aider à maintenir la disponibilité et les performances. Il collecte les données générées par les ressources dans vos environnements cloud et locaux et d’autres outils d’analyse pour fournir une analyse sur plusieurs sources.

Par rapport aux journaux d’infrastructure Azure, Analytique de journal, comme un service Azure, ingère les données de journal et les métriques à partir d’autres services Azure (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), les machines virtuelles Azure, des conteneurs Docker et en local ou autres infrastructures de cloud. Journal Analytique offre des recherches de journal et analytique hors de la zone sur ces données. Il fournit des outils riches, que vous pouvez utiliser pour analyser les données sources, il permet des requêtes complexes sur tous les journaux et il peut alerter de manière proactive en fonction des conditions spécifiées. Vous pouvez même collecter des données personnalisées dans le référentiel d’Analytique de journal central, où vous pouvez interroger et visualiser. Vous pouvez également tirer parti des solutions intégrées Analytique de journal pour obtenir immédiatement des informations sur la sécurité et les fonctionnalités de votre infrastructure.

Vous pouvez accéder aux journaux Analytique via le portail OMS ou le portail Azure, qui s’exécutent dans n’importe quel navigateur, et vous donne accès aux paramètres de configuration et plusieurs outils pour analyser et agir sur les données collectées.

Le [solution Container Monitoring](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) permet d’Analytique de journal vous permet d’afficher et gérer vos hôtes Docker et des conteneurs de Windows dans un emplacement unique. La solution montre les conteneurs qui sont en cours d’exécution, image conteneur qu’ils s’exécutent, et où les conteneurs sont en cours d’exécution. Vous pouvez afficher des informations d’audit détaillées, y compris les commandes qui sont utilisées avec des conteneurs. Vous pouvez également résoudre les conteneurs par afficher et rechercher des journaux centralisés, sans avoir besoin d’afficher à distance les hôtes Docker ou Windows. Vous pouvez trouver des conteneurs qui peuvent être bruyants et consommant des ressources excessives sur un ordinateur hôte. En outre, vous pouvez afficher centralisées sur le processeur, mémoire, stockage, l’utilisation du réseau et des informations relatives aux performances, les conteneurs. Sur les ordinateurs exécutant Windows, vous pouvez centraliser et comparer les journaux à partir de Windows Server, Hyper-V et les conteneurs Docker. La solution prend en charge les orchestrateurs de conteneurs suivants :

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

Figure 4-11 montre les relations entre les différents hôtes de conteneur et les agents et OMS.

![Solution de surveillance des conteneurs d’Analytique de journal](./media/image11.png)

> **Figure 4-11.** Solution de surveillance des conteneurs d’Analytique de journal

Vous pouvez utiliser la solution d’analyse de journal Analytique conteneur pour :

- Afficher des informations sur tous les hôtes de conteneur dans un emplacement unique.

- Savoir quels conteneurs sont en cours d’exécution, image qu’ils s’exécutent et où ils s’exécutent.

- Consultez une piste d’audit pour les actions sur les conteneurs.

- Résoudre les problèmes en affichant et en recherchant des journaux centralisés sans connexion à distance pour les hôtes Docker.

- Rechercher des conteneurs qui peuvent être « voisins bruyants » et consommer des ressources excessives sur un ordinateur hôte.

- Afficher centralisées sur le processeur, mémoire, stockage, l’utilisation du réseau et des informations relatives aux performances, les conteneurs.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Vue d’ensemble de l’analyse dans Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Présentation d’Application Insights**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Nouveautés d’Analytique de journal ?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Solution Container Monitoring dans Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Vue d’ensemble d’Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Nouveautés d’Operations Management Suite (OMS) ?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Précédent](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[Suivant](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
