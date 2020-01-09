---
title: Supervision dans Azure Kubernetes Services
description: Supervision dans Azure Kubernetes Services
ms.date: 09/23/2019
ms.openlocfilehash: fc9d84fd738ff1c40d25860680e14313c9323517
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711647"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Supervision dans Azure Kubernetes Services

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La journalisation intégrée dans Kubernetes est primitive. Toutefois, il existe des options intéressantes pour récupérer les journaux de Kubernetes et à un emplacement où ils peuvent être analysés correctement. Si vous devez surveiller vos clusters AKS, la configuration de la pile élastique pour Kubernetes est une solution intéressante.

## <a name="elastic-stack"></a>Pile élastique

La pile élastique est une option puissante pour la collecte d’informations à partir d’un cluster Kubernetes. Kubernetes prend en charge l’envoi de journaux à un point de terminaison Elasticsearch. dans la [plupart](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)des cas, vous devez commencer par définir les variables d’environnement, comme illustré dans la figure 7-5 :

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**Figure 7-5** -variables de configuration pour Kubernetes

Cette opération installe Elasticsearch sur le cluster et cible l’envoi de tous les journaux de cluster vers ce dernier.

![un exemple de tableau de bord Kibana présentant les résultats d’une requête sur les journaux ingérés à partir de Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**. Exemple de tableau de bord Kibana indiquant les résultats d’une requête sur les journaux qui sont ingérés à partir de Kubernetes

## <a name="azure-container-monitoring"></a>Surveillance de conteneur Azure

Azure Container Monitoring prend en charge la consommation des journaux à partir de non seulement Kubernetes mais également d’autres moteurs d’orchestration tels que DC/OS, Dockr essaim et Red Hat OpenShift.

![consomment les journaux de divers conteneurs](./media/containers-diagram.png)
la **Figure 7-7**.  Utilisation des journaux de différents conteneurs

Les informations de journal et de métrique sont collectées non seulement à partir des conteneurs qui s’exécutent dans le cluster, mais également des hôtes de cluster eux-mêmes. Il permet de mettre en corrélation les informations de journalisation des deux, ce qui facilite grandement le suivi d’une erreur.

L’installation des collecteurs de journaux diffère sur les clusters [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) et [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) . Toutefois, dans les deux cas, la collection de journaux est implémentée en tant que [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)Kubernetes, ce qui signifie que log Collector est exécuté en tant que conteneur sur chacun des nœuds.

Quel que soit le système d’exploitation ou Orchestrator exécutant le démon Azure Monitor, les informations du journal sont transférées aux mêmes outils de Azure Monitor que ceux qui sont familiers aux utilisateurs. Cela garantit une expérience parallèle dans les environnements qui mélangent différentes sources de journaux, comme un environnement hybride Kubernetes/Azure Functions.

![un exemple de tableau de bord présentant les informations de journalisation et de métrique d’un certain nombre de conteneurs en cours d’exécution.](./media/containers-dashboard.png)
**Figure 7-8**. Exemple de tableau de bord présentant les informations de journalisation et de métrique d’un certain nombre de conteneurs en cours d’exécution.

## <a name="logfinalize"></a>Log. Finalize ()

La journalisation est l’un des éléments les plus négligés et les plus importants du déploiement d’une application à l’échelle. À mesure que la taille et la complexité des applications augmentent, la difficulté de les déboguer est donc la plus difficile. Le fait de disposer d’un grand nombre de journaux de qualité rend le débogage beaucoup plus facile et le déplace du domaine « presque impossible » vers « une expérience agréable ».

>[!div class="step-by-step"]
>[Précédent](logging-with-elastic-stack.md)
>[Suivant](azure-monitor.md)
