---
title: Moderniser vos applications avec la surveillance et la télémétrie
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Moderniser vos applications avec la surveillance et la télémétrie
ms.date: 12/21/2020
ms.openlocfilehash: c79a16400ce9dadca50fabb6c7df2859e4519a41
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025236"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Moderniser vos applications avec la surveillance et la télémétrie

Lorsque vous exécutez une application en production, il est essentiel de disposer d’informations sur le fonctionnement de votre application. Est-il en cours de réalisation à un niveau élevé ? Les utilisateurs reçoivent-ils des erreurs ou l’application est-elle stable et fiable ? Vous avez besoin d’une analyse des performances riche, d’alertes puissantes et de tableaux de bord pour vous assurer que votre application est disponible et qu’elle fonctionne comme prévu. Vous devez également être en mesure de voir rapidement si un problème survient, de déterminer le nombre de clients affectés et d’effectuer une analyse de la cause première pour trouver et résoudre le problème.

## <a name="monitor-your-application-with-application-insights"></a>Surveillez votre application avec Application Insights

Application Insights est un service extensible de gestion des performances des applications (APM) destiné aux développeurs Web qui travaillent sur plusieurs plateformes. Utilisez-le pour analyser votre application web en direct. Application Insights détecte automatiquement les anomalies de performances. Il comprend des outils d’analyse puissants pour vous aider à diagnostiquer les problèmes et pour vous aider à comprendre ce que font les utilisateurs avec votre application. Application Insights a été conçu pour vous permettre d’améliorer continuellement les performances et la facilité d’utilisation. Il fonctionne pour les applications sur un large éventail de plateformes, notamment .NET, Node.js et J2EE, qu’elles soient hébergées en local ou dans le Cloud. Application Insights s’intègre à vos processus DevOps et offre des points de connexion à divers outils de développement.

La figure 4-10 montre un exemple de la façon dont Application Insights surveille votre application et comment elle couvre ces informations dans un tableau de bord.

![Capture d’écran du tableau de bord de surveillance Application Insights.](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Figure 4-10.** Tableau de bord de surveillance Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Surveillez votre infrastructure d’ancrage avec Log Analytics et sa solution de surveillance de conteneur

[Azure log Analytics](/azure/log-analytics/log-analytics-overview) fait partie de la [solution de surveillance globale Microsoft Azure](/azure/monitoring-and-diagnostics/monitoring-overview). Il s’agit également d’un service dans [Operations Management Suite (OMS)](/azure/operations-management-suite/operations-management-suite-overview). Log Analytics surveille les environnements Cloud et locaux (OMS pour les environnements locaux) afin de garantir la disponibilité et les performances. Il collecte les données générées par les ressources de votre cloud et de vos environnements locaux et d’autres outils d’analyse pour fournir une analyse sur plusieurs sources.

En ce qui concerne les journaux d’infrastructure Azure, Log Analytics, en tant que service Azure, ingère les données de journal et de métrique d’autres services Azure (via [Azure Monitor](/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), les machines virtuelles Azure, les conteneurs d’ancrage, les infrastructures locales ou d’autres infrastructures Cloud. Log Analytics offre une recherche de journal flexible et des analyses prêtes à l’emploi en plus de ces données. Il fournit des outils enrichis que vous pouvez utiliser pour analyser des données dans les sources, il autorise des requêtes complexes dans tous les journaux et peut alerter de manière proactive en fonction des conditions spécifiées. Vous pouvez même collecter des données personnalisées dans le référentiel central Log Analytics, où vous pouvez les interroger et les visualiser. Vous pouvez également tirer parti des solutions intégrées Log Analytics pour obtenir immédiatement des informations sur la sécurité et les fonctionnalités de votre infrastructure.

Vous pouvez accéder à Log Analytics via le portail OMS ou le Portail Azure, qui s’exécute dans n’importe quel navigateur et vous donne accès aux paramètres de configuration et à plusieurs outils pour analyser et agir sur les données collectées.

La [solution de surveillance de conteneur](/azure/log-analytics/log-analytics-containers) dans log Analytics vous permet d’afficher et de gérer vos hôtes de conteneur et d’ancrage Windows dans un emplacement unique. La solution montre les conteneurs en cours d’exécution, l’image conteneur qu’ils exécutent et l’emplacement où les conteneurs s’exécutent. Vous pouvez afficher des informations d’audit détaillées, y compris les commandes utilisées avec les conteneurs. Vous pouvez également résoudre les problèmes liés aux conteneurs en affichant et en effectuant des recherches dans des journaux centralisés, sans avoir à afficher à distance les hôtes de l’Dockeur ou de Windows. Vous pouvez trouver des conteneurs qui peuvent être bruyants et consommer des ressources excédentaires sur un ordinateur hôte. En outre, vous pouvez afficher des informations sur l’utilisation du processeur, de la mémoire, du stockage et du réseau, ainsi que des informations sur les performances, pour les conteneurs. Sur les ordinateurs exécutant Windows, vous pouvez centraliser et comparer les journaux d’activité des conteneurs Windows Server, Hyper-V et Docker. La solution prend en charge les orchestrateurs de conteneur suivants :

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

La figure 4-11 montre les relations entre les différents hôtes de conteneur et les agents et OMS.

![Capture d’écran de la solution de surveillance des conteneurs Log Analytics.](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Figure 4-11.** Solution de surveillance des conteneurs Log Analytics

Vous pouvez utiliser la solution de surveillance des conteneurs Log Analytics pour :

- Consultez les informations sur tous les hôtes de conteneur à un seul emplacement.

- Identifiez les conteneurs en cours d’exécution, l’image qu’ils exécutent et l’emplacement où ils s’exécutent.

- Consultez une piste d’audit pour les actions sur les conteneurs.

- Résolvez les problèmes en affichant et en recherchant des journaux centralisés sans connexion distante aux hôtes de la station d’accueil.

- Recherchez les conteneurs qui peuvent être des « voisins bruyants » et consomment des ressources excédentaires sur un ordinateur hôte.

- Affichez les informations relatives à l’utilisation du processeur, de la mémoire, du stockage et du réseau, ainsi que les informations sur les performances, pour les conteneurs.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Vue d’ensemble de l’analyse dans Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Présentation d’Application Insights**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Présentation de Log Analytics**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Solution Container Monitoring dans Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Vue d’ensemble d’Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Présentation d’Operations Management Suite (OMS)**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Précédent](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md) 
> [Suivant](life-cycle-ci-cd-pipelines-devops-tools.md)
