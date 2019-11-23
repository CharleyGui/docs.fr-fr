---
title: Supervision dans Azure Kubernetes Services
description: Supervision dans Azure Kubernetes Services
ms.date: 09/23/2019
ms.openlocfilehash: 71192601eac2169db188b25da3dc91b71b860903
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184987"
---
# <a name="monitoring-in-azure-kubernetes-services"></a><span data-ttu-id="6d7e6-103">Supervision dans Azure Kubernetes Services</span><span class="sxs-lookup"><span data-stu-id="6d7e6-103">Monitoring in Azure Kubernetes Services</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6d7e6-104">La journalisation intégrée dans Kubernetes est primitive.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-104">The built-in logging in Kubernetes is primitive.</span></span> <span data-ttu-id="6d7e6-105">Toutefois, il existe des options intéressantes pour récupérer les journaux de Kubernetes et à un emplacement où ils peuvent être analysés correctement.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-105">However, there are some great options for getting the logs out of Kubernetes and into a place where they can be properly analyzed.</span></span> <span data-ttu-id="6d7e6-106">Si vous devez surveiller vos clusters AKS, la configuration de la pile élastique pour Kubernetes est une solution intéressante.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-106">If you need to monitor your AKS clusters, configuring Elastic Stack for Kubernetes is a great solution.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="6d7e6-107">Pile élastique</span><span class="sxs-lookup"><span data-stu-id="6d7e6-107">Elastic Stack</span></span>

<span data-ttu-id="6d7e6-108">La pile élastique est une option puissante pour la collecte d’informations à partir d’un cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-108">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="6d7e6-109">Kubernetes prend en charge l’envoi de journaux à un point de terminaison Elasticsearch. dans la [plupart](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)des cas, vous devez commencer par définir les variables d’environnement, comme illustré dans la figure 7-5 :</span><span class="sxs-lookup"><span data-stu-id="6d7e6-109">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="6d7e6-110">**Figure 7-5** -variables de configuration pour Kubernetes</span><span class="sxs-lookup"><span data-stu-id="6d7e6-110">**Figure 7-5** - Configuration variables for Kubernetes</span></span>

<span data-ttu-id="6d7e6-111">Cette opération installe Elasticsearch sur le cluster et cible l’envoi de tous les journaux de cluster vers ce dernier.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-111">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="6d7e6-112">![un exemple de tableau de bord Kibana présentant les résultats d’une requête sur les journaux ingérés à partir de Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-112">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="6d7e6-113">Exemple de tableau de bord Kibana indiquant les résultats d’une requête sur les journaux qui sont ingérés à partir de Kubernetes</span><span class="sxs-lookup"><span data-stu-id="6d7e6-113">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="azure-container-monitoring"></a><span data-ttu-id="6d7e6-114">Surveillance de conteneur Azure</span><span class="sxs-lookup"><span data-stu-id="6d7e6-114">Azure Container Monitoring</span></span>

<span data-ttu-id="6d7e6-115">Azure Container Monitoring prend en charge la consommation des journaux à partir de non seulement Kubernetes mais également d’autres moteurs d’orchestration tels que DC/OS, Dockr essaim et Red Hat OpenShift.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-115">Azure Container Monitoring supports consuming logs from not just Kubernetes but also from other orchestration engines such as DC/OS, Docker Swarm, and Red Hat OpenShift.</span></span>

<span data-ttu-id="6d7e6-116">![consomment les journaux de divers conteneurs](./media/containers-diagram.png)
la **Figure 7-7**.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-116">![Consuming logs from various containers](./media/containers-diagram.png)
**Figure 7-7**.</span></span>  <span data-ttu-id="6d7e6-117">Utilisation des journaux de différents conteneurs</span><span class="sxs-lookup"><span data-stu-id="6d7e6-117">Consuming logs from various containers</span></span>

<span data-ttu-id="6d7e6-118">Les informations de journal et de métrique sont collectées non seulement à partir des conteneurs qui s’exécutent dans le cluster, mais également des hôtes de cluster eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-118">Log and metric information is gathered not just from the containers running in the cluster but also from the cluster hosts themselves.</span></span> <span data-ttu-id="6d7e6-119">Il permet de mettre en corrélation les informations de journalisation des deux, ce qui facilite grandement le suivi d’une erreur.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-119">It allows correlating log information from the two making it much easier to track down an error.</span></span>

<span data-ttu-id="6d7e6-120">L’installation des collecteurs de journaux diffère sur les clusters [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) et [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) .</span><span class="sxs-lookup"><span data-stu-id="6d7e6-120">Installing the log collectors differs on [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) and [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) clusters.</span></span> <span data-ttu-id="6d7e6-121">Toutefois, dans les deux cas, la collection de journaux est implémentée en tant que [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)Kubernetes, ce qui signifie que log Collector est exécuté en tant que conteneur sur chacun des nœuds.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-121">But in both cases the log collection is implemented as a Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), meaning that the log collector is run as a container on each of the nodes.</span></span>

<span data-ttu-id="6d7e6-122">Quel que soit le système d’exploitation ou Orchestrator exécutant le démon Azure Monitor, les informations du journal sont transférées aux mêmes outils de Azure Monitor que ceux qui sont familiers aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-122">No matter which orchestrator or operating system is running the Azure Monitor daemon, the log information is forwarded to the same Azure Monitor tools with which users are familiar.</span></span> <span data-ttu-id="6d7e6-123">Cela garantit une expérience parallèle dans les environnements qui mélangent différentes sources de journaux, comme un environnement hybride Kubernetes/Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-123">This ensures a parallel experience in environments that mix different log sources such as a hybrid Kubernetes/Azure Functions environment.</span></span>

<span data-ttu-id="6d7e6-124">![un exemple de tableau de bord présentant les informations de journalisation et de métrique d’un certain nombre de conteneurs en cours d’exécution.](./media/containers-dashboard.png)
**Figure 7-8**.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-124">![A sample dashboard showing logging and metric information from a number of running containers.](./media/containers-dashboard.png)
**Figure 7-8**.</span></span> <span data-ttu-id="6d7e6-125">Exemple de tableau de bord présentant les informations de journalisation et de métrique d’un certain nombre de conteneurs en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-125">A sample dashboard showing logging and metric information from a number of running containers.</span></span>

## <a name="logfinalize"></a><span data-ttu-id="6d7e6-126">Log. Finalize ()</span><span class="sxs-lookup"><span data-stu-id="6d7e6-126">Log.Finalize()</span></span>

<span data-ttu-id="6d7e6-127">La journalisation est l’un des éléments les plus négligés et les plus importants du déploiement d’une application à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-127">Logging is one of the most overlooked and yet most important parts of deploying any application at scale.</span></span> <span data-ttu-id="6d7e6-128">À mesure que la taille et la complexité des applications augmentent, la difficulté de les déboguer est donc la plus difficile.</span><span class="sxs-lookup"><span data-stu-id="6d7e6-128">As the size and complexity of applications increase, then so does the difficulty of debugging them.</span></span> <span data-ttu-id="6d7e6-129">Le fait de disposer d’un grand nombre de journaux de qualité rend le débogage beaucoup plus facile et le déplace du domaine « presque impossible » vers « une expérience agréable ».</span><span class="sxs-lookup"><span data-stu-id="6d7e6-129">Having top quality logs available makes debugging much easier and moves it from the realm of "nearly impossible" to "a pleasant experience".</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6d7e6-130">[Précédent](logging-with-elastic-stack.md)
>[Suivant](azure-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="6d7e6-130">[Previous](logging-with-elastic-stack.md)
[Next](azure-monitor.md)</span></span>
