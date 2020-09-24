---
title: Supervision dans Azure Kubernetes Services
description: Supervision dans Azure Kubernetes Services
ms.date: 05/13/2020
ms.openlocfilehash: 3900f169b9be4f807e72392da38a1224d6ce28e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163698"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Supervision dans Azure Kubernetes Services

La journalisation intégrée dans Kubernetes est primitive. Toutefois, il existe des options intéressantes pour récupérer les journaux de Kubernetes et à un emplacement où ils peuvent être analysés correctement. Si vous devez surveiller vos clusters AKS, la configuration de la pile élastique pour Kubernetes est une solution intéressante.

## <a name="azure-monitor-for-containers"></a>Azure Monitor pour conteneurs

[Azure Monitor pour les conteneurs](/azure/azure-monitor/insights/container-insights-overview) prend en charge la consommation des journaux à partir de non seulement Kubernetes mais également d’autres moteurs d’orchestration tels que DC/OS, dockr essaim et Red Hat OpenShift.

![Utilisation des journaux de divers conteneurs ](./media/containers-diagram.png)
 **figure 7-10**. Utilisation des journaux de différents conteneurs

[Prometheus](https://prometheus.io/) est une solution de surveillance des métriques Open source populaire. Il fait partie de la Fondation de calcul native Cloud. En règle générale, l’utilisation de Prometheus nécessite la gestion d’un serveur Prometheus avec son propre magasin. Toutefois, [Azure Monitor pour les conteneurs permet une intégration directe avec les points de terminaison de métriques Prometheus](/azure/azure-monitor/insights/container-insights-prometheus-integration), un serveur distinct n’est donc pas nécessaire.

Les informations de journal et de métrique sont collectées non seulement à partir des conteneurs qui s’exécutent dans le cluster, mais également des hôtes de cluster eux-mêmes. Il permet de mettre en corrélation les informations de journalisation des deux, ce qui facilite grandement le suivi d’une erreur.

L’installation des collecteurs de journaux diffère sur les clusters [Windows](/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) et [Linux](/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) . Toutefois, dans les deux cas, la collection de journaux est implémentée en tant que [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)Kubernetes, ce qui signifie que log Collector est exécuté en tant que conteneur sur chacun des nœuds.

Quel que soit le système d’exploitation ou Orchestrator exécutant le démon Azure Monitor, les informations du journal sont transférées aux mêmes outils de Azure Monitor que ceux qui sont familiers aux utilisateurs. Cela garantit une expérience parallèle dans les environnements qui mélangent différentes sources de journaux, comme un environnement hybride Kubernetes/Azure Functions.

![Exemple de tableau de bord présentant les informations de journalisation et de métrique d’un certain nombre de conteneurs en cours d’exécution. ](./media/containers-dashboard.png)
 **Figure 7-11**. Exemple de tableau de bord présentant les informations de journalisation et de métrique d’un certain nombre de conteneurs en cours d’exécution.

## <a name="logfinalize"></a>Log. Finalize ()

La journalisation est l’un des éléments les plus négligés et les plus importants du déploiement d’une application à l’échelle. À mesure que la taille et la complexité des applications augmentent, la difficulté de les déboguer est donc la plus difficile. Le fait de disposer d’un grand nombre de journaux de qualité rend le débogage beaucoup plus facile et le déplace du domaine « presque impossible » vers « une expérience agréable ».

>[!div class="step-by-step"]
>[Précédent](logging-with-elastic-stack.md) 
> [Suivant](azure-monitor.md)
