---
title: Moderniser vos applications avec la surveillance et la télémétrie
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Modernisez vos applications grâce à la surveillance et à la télémétrie
ms.date: 04/30/2018
ms.openlocfilehash: a5101f150d6548406db8638904fb4ab6375edf9c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739180"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Moderniser vos applications avec la surveillance et la télémétrie

Lorsque vous exécutez une application en production, il est essentiel que vous ayez des informations sur l’exécution de votre application. Est-ce qu’il fonctionne à un niveau élevé? Les utilisateurs obtiennent-ils des erreurs, ou l’application est-elle stable et fiable ? Vous avez besoin d’une surveillance des performances riche, d’une alerte puissante et de tableaux de bord pour vous assurer que votre application est disponible et performante comme prévu. Vous devez également être en mesure de voir rapidement s’il ya un problème, déterminer combien de clients sont touchés, et effectuer une analyse de cause racine pour trouver et résoudre le problème.

## <a name="monitor-your-application-with-application-insights"></a>Surveillez votre application avec Application Insights

Application Insights est un service de gestion de la performance des applications (APM) pour les développeurs Web qui travaillent sur plusieurs plates-formes. Utilisez-le pour analyser votre application web en direct. Application Insights détecte automatiquement les anomalies de performances. Il comprend de puissants outils d’analyse pour vous aider à diagnostiquer les problèmes, et pour vous aider à comprendre ce que les utilisateurs font réellement avec votre application. Application Insights a été conçu pour vous permettre d’améliorer continuellement les performances et la facilité d’utilisation. Il fonctionne pour des applications sur une grande variété de plates-formes, y compris .NET, Node.js, et J2EE, que ce soit hébergé sur place ou dans le cloud. Application Insights s’intègre à vos processus DevOps et dispose de points de connexion à une variété d’outils de développement.

La figure 4-10 montre un exemple de la façon dont Application Insights surveille votre application et comment elle fait surface ces informations à un tableau de bord.

![Capture d’écran du tableau de bord de surveillance d’Application Insights.](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Figure 4-10.** Tableau de bord de surveillance d’applications Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Surveillez votre infrastructure Docker avec Log Analytics et sa solution de surveillance des conteneurs

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) fait partie de la [solution de surveillance globale Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). C’est aussi un service dans [operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Log Analytics surveille les environnements cloud et sur site (OMS pour les personnes sur place) pour aider à maintenir la disponibilité et les performances. Il collecte les données générées par les ressources de votre cloud et de vos environnements locaux et d’autres outils d’analyse pour fournir une analyse sur plusieurs sources.

En ce qui concerne les journaux d’infrastructure Azure, Log Analytics, en tant que service Azure, ingère le journal et les données métriques d’autres services Azure (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), les VM Azure, les conteneurs Docker, les infrastructures sur site ou autres infrastructures cloud. Log Analytics offre une recherche de journal flexible et des analyses hors boîte en plus de ces données. Il fournit des outils riches que vous pouvez utiliser pour analyser les données à travers les sources, il permet des requêtes complexes dans tous les journaux, et il peut alerter de manière proactive en fonction de conditions spécifiées. Vous pouvez même collecter des données personnalisées dans le référentiel central d’analyse de journal, où vous pouvez les interroger et les visualiser. Vous pouvez également profiter des solutions intégrées Log Analytics pour obtenir immédiatement un aperçu de la sécurité et de la fonctionnalité de votre infrastructure.

Vous pouvez accéder à Log Analytics via le portail OMS ou le portail Azure, qui s’exécutent dans n’importe quel navigateur, et vous fournir accès aux paramètres de configuration et à plusieurs outils pour analyser et agir sur les données collectées.

La [solution de surveillance des conteneurs](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) dans Log Analytics vous aide à afficher et à gérer vos hôtes Docker et Windows Container en un seul emplacement. La solution montre quels conteneurs sont en marche, quelle image de conteneur ils exécutent et où les conteneurs sont en cours d’exécution. Vous pouvez consulter des informations détaillées de vérification, y compris des commandes qui sont utilisées avec des conteneurs. Vous pouvez également dépanner les conteneurs en visualisant et en recherchant des journaux centralisés, sans avoir besoin de visualiser à distance les hôtes Docker ou Windows. Vous pouvez trouver des conteneurs qui pourraient être bruyants et consommer des ressources excédentaires sur un hôte. En outre, vous pouvez afficher le processeur centralisé, la mémoire, le stockage, et l’utilisation du réseau, et des informations de performance, pour les conteneurs. Sur les ordinateurs exécutant Windows, vous pouvez centraliser et comparer les journaux d’activité des conteneurs Windows Server, Hyper-V et Docker. La solution prend en charge les orchestrateurs de conteneur suivants :

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

La figure 4-11 montre les relations entre les différents hôtes et agents de conteneurs et OMS.

![Capture d’écran de la solution de surveillance des conteneurs d’analyse des journaux.](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Figure 4-11.** Solution de surveillance des conteneurs d’analyse de connexion

Vous pouvez utiliser la solution de surveillance des conteneurs d’analyse de connexion pour :

- Voir les informations sur tous les hôtes de conteneurs en un seul endroit.

- Sachez quels conteneurs sont en marche, quelle image ils courent et où ils fonctionnent.

- Consultez une piste de vérification pour les actions sur les conteneurs.

- Dépannage en visualisant et en fouillant les journaux centralisés sans connexion à distance aux hôtes Docker.

- Trouvez des contenants qui pourraient être des « voisins bruyants » et consommez des ressources excédentaires sur un hôte.

- Afficher le processeur centralisé, la mémoire, le stockage et l’utilisation du réseau, ainsi que les informations de performance, pour les conteneurs.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Aperçu de la surveillance dans Microsoft Azure**

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
>[Suivant précédent](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[Next](life-cycle-ci-cd-pipelines-devops-tools.md)
