---
title: Journalisation avec Elastic Stack
description: Journalisation à l’aide de la pile élastique, Logstash et Kibana
ms.date: 05/13/2020
ms.openlocfilehash: e886141fa691b75b882b5d67eae4ceb242e8089f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613848"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="3c110-103">Journalisation avec Elastic Stack</span><span class="sxs-lookup"><span data-stu-id="3c110-103">Logging with Elastic Stack</span></span>

<span data-ttu-id="3c110-104">Il existe de nombreux outils de journalisation centralisés et leur coût est inférieur à celui des outils open source gratuits, à des options plus coûteuses.</span><span class="sxs-lookup"><span data-stu-id="3c110-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="3c110-105">Dans de nombreux cas, les outils gratuits sont aussi bons ou mieux que les offres payantes.</span><span class="sxs-lookup"><span data-stu-id="3c110-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="3c110-106">L’un de ces outils est une combinaison de trois composants Open Source : la recherche élastique, Logstash et Kibana.</span><span class="sxs-lookup"><span data-stu-id="3c110-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span>

<span data-ttu-id="3c110-107">Ces outils sont appelés pile élastique ou pile ELK.</span><span class="sxs-lookup"><span data-stu-id="3c110-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="3c110-108">Pile élastique</span><span class="sxs-lookup"><span data-stu-id="3c110-108">Elastic Stack</span></span>

<span data-ttu-id="3c110-109">La pile élastique est une option puissante pour la collecte d’informations à partir d’un cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3c110-109">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="3c110-110">Kubernetes prend en charge l’envoi de journaux à un point de terminaison Elasticsearch. dans la [plupart](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)des cas, vous devez commencer par définir les variables d’environnement, comme illustré dans la figure 7-5 :</span><span class="sxs-lookup"><span data-stu-id="3c110-110">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="3c110-111">**Figure 7-5**.</span><span class="sxs-lookup"><span data-stu-id="3c110-111">**Figure 7-5**.</span></span> <span data-ttu-id="3c110-112">Variables de configuration pour Kubernetes</span><span class="sxs-lookup"><span data-stu-id="3c110-112">Configuration variables for Kubernetes</span></span>

<span data-ttu-id="3c110-113">Cette opération installe Elasticsearch sur le cluster et cible l’envoi de tous les journaux de cluster vers ce dernier.</span><span class="sxs-lookup"><span data-stu-id="3c110-113">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="3c110-114">![Exemple de tableau de bord Kibana présentant les résultats d’une requête sur les journaux ingérés à partir de la ](./media/kibana-dashboard.png)
 **figure 7-6**de Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3c110-114">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="3c110-115">Exemple de tableau de bord Kibana indiquant les résultats d’une requête sur les journaux qui sont ingérés à partir de Kubernetes</span><span class="sxs-lookup"><span data-stu-id="3c110-115">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="3c110-116">Quels sont les avantages de la pile élastique ?</span><span class="sxs-lookup"><span data-stu-id="3c110-116">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="3c110-117">La pile élastique fournit une journalisation centralisée dans une solution cloud conviviale et évolutive.</span><span class="sxs-lookup"><span data-stu-id="3c110-117">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="3c110-118">Son interface utilisateur simplifie l’analyse des données, ce qui vous permet de consacrer du temps à la collecte d’informations à partir de vos données au lieu de combattre une interface plus sourde.</span><span class="sxs-lookup"><span data-stu-id="3c110-118">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="3c110-119">Il prend en charge un large éventail d’entrées, de sorte que votre application distribuée s’étend sur de plus en plus de types de services différents, vous pouvez vous attendre à pouvoir continuer à alimenter le journal et les données de métriques dans le système.</span><span class="sxs-lookup"><span data-stu-id="3c110-119">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="3c110-120">La pile élastique prend également en charge les recherches rapides, même dans les jeux de données volumineux, ce qui permet de consigner les données détaillées dans des applications volumineuses, tout en étant en mesure de les visualiser de manière performante.</span><span class="sxs-lookup"><span data-stu-id="3c110-120">The Elastic Stack also supports fast searches even across large data sets, making it possible even for large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="3c110-121">Logstash</span><span class="sxs-lookup"><span data-stu-id="3c110-121">Logstash</span></span>

<span data-ttu-id="3c110-122">Le premier composant est [Logstash](https://www.elastic.co/products/logstash).</span><span class="sxs-lookup"><span data-stu-id="3c110-122">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="3c110-123">Cet outil est utilisé pour collecter des informations de journalisation à partir d’une grande variété de sources différentes.</span><span class="sxs-lookup"><span data-stu-id="3c110-123">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="3c110-124">Par exemple, Logstash peut lire les journaux à partir du disque et recevoir également des messages des bibliothèques de journalisation telles que [Serilog](https://serilog.net/).</span><span class="sxs-lookup"><span data-stu-id="3c110-124">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="3c110-125">Logstash peut effectuer un filtrage et une expansion de base sur les journaux au fur et à mesure de leur arrivée.</span><span class="sxs-lookup"><span data-stu-id="3c110-125">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="3c110-126">Par exemple, si vos journaux contiennent des adresses IP, Logstash peut être configuré pour effectuer une recherche géographique et obtenir un pays ou même une ville d’origine pour ce message.</span><span class="sxs-lookup"><span data-stu-id="3c110-126">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span>

<span data-ttu-id="3c110-127">Serilog est une bibliothèque de journalisation pour les langages .NET, qui permet la journalisation paramétrée.</span><span class="sxs-lookup"><span data-stu-id="3c110-127">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="3c110-128">Au lieu de générer un message de journalisation qui incorpore des champs, les paramètres sont conservés séparément.</span><span class="sxs-lookup"><span data-stu-id="3c110-128">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="3c110-129">Cela permet un filtrage et une recherche plus intelligents.</span><span class="sxs-lookup"><span data-stu-id="3c110-129">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="3c110-130">Un exemple de configuration Serilog pour l’écriture dans Logstash apparaît dans la figure 7-7.</span><span class="sxs-lookup"><span data-stu-id="3c110-130">A sample Serilog configuration for writing to Logstash appears in Figure 7-7.</span></span>

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="3c110-131">**Figure 7-7**.</span><span class="sxs-lookup"><span data-stu-id="3c110-131">**Figure 7-7**.</span></span> <span data-ttu-id="3c110-132">Configuration de Serilog pour écrire des informations de journal directement dans logstash sur HTTP</span><span class="sxs-lookup"><span data-stu-id="3c110-132">Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="3c110-133">Logstash utilise une configuration telle que celle illustrée dans la figure 7-8.</span><span class="sxs-lookup"><span data-stu-id="3c110-133">Logstash would use a configuration like the one shown in Figure 7-8.</span></span>

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

<span data-ttu-id="3c110-134">**Figure 7-8**.</span><span class="sxs-lookup"><span data-stu-id="3c110-134">**Figure 7-8**.</span></span> <span data-ttu-id="3c110-135">Une configuration Logstash pour la consommation des journaux à partir de Serilog</span><span class="sxs-lookup"><span data-stu-id="3c110-135">A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="3c110-136">Dans les scénarios où une manipulation de journal étendue n’est pas nécessaire, il existe une alternative à Logstash appelée [temps](https://www.elastic.co/products/beats).</span><span class="sxs-lookup"><span data-stu-id="3c110-136">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="3c110-137">Le temps est une famille d’outils qui peuvent recueillir un large éventail de données à partir des journaux vers les données réseau et les informations de temps d’activité.</span><span class="sxs-lookup"><span data-stu-id="3c110-137">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="3c110-138">De nombreuses applications utilisent à la fois les Logstash et les temps.</span><span class="sxs-lookup"><span data-stu-id="3c110-138">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="3c110-139">Une fois les journaux collectés par Logstash, il faut les placer.</span><span class="sxs-lookup"><span data-stu-id="3c110-139">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="3c110-140">Bien que Logstash prenne en charge de nombreuses sorties différentes, l’une des plus intéressantes est la recherche élastique.</span><span class="sxs-lookup"><span data-stu-id="3c110-140">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="3c110-141">Recherche élastique</span><span class="sxs-lookup"><span data-stu-id="3c110-141">Elastic search</span></span>

<span data-ttu-id="3c110-142">La recherche élastique est un moteur de recherche puissant qui peut indexer les journaux à mesure qu’ils arrivent.</span><span class="sxs-lookup"><span data-stu-id="3c110-142">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="3c110-143">Elle accélère l’exécution des requêtes sur les journaux.</span><span class="sxs-lookup"><span data-stu-id="3c110-143">It makes running queries against the logs quick.</span></span> <span data-ttu-id="3c110-144">La recherche élastique peut gérer de grandes quantités de journaux et, dans des cas extrêmes, peut être montée en charge sur plusieurs nœuds.</span><span class="sxs-lookup"><span data-stu-id="3c110-144">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span>

<span data-ttu-id="3c110-145">Les messages de journal qui ont été conçus pour contenir des paramètres ou dont les paramètres ont été fractionnés à l’aide du traitement Logstash peuvent être interrogés directement, car Elasticsearch conserve ces informations.</span><span class="sxs-lookup"><span data-stu-id="3c110-145">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="3c110-146">Une requête qui recherche les 10 premières pages visitées par `jill@example.com` , apparaît dans la Figure 7-9.</span><span class="sxs-lookup"><span data-stu-id="3c110-146">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-9.</span></span>

```
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

<span data-ttu-id="3c110-147">**Figure 7-9**.</span><span class="sxs-lookup"><span data-stu-id="3c110-147">**Figure 7-9**.</span></span> <span data-ttu-id="3c110-148">Requête Elasticsearch pour rechercher les 10 premières pages visitées par un utilisateur</span><span class="sxs-lookup"><span data-stu-id="3c110-148">An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="3c110-149">Visualisation des informations avec les tableaux de bord Web Kibana</span><span class="sxs-lookup"><span data-stu-id="3c110-149">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="3c110-150">Le composant final de la pile est Kibana.</span><span class="sxs-lookup"><span data-stu-id="3c110-150">The final component of the stack is Kibana.</span></span> <span data-ttu-id="3c110-151">Cet outil est utilisé pour fournir des visualisations interactives dans un tableau de bord Web.</span><span class="sxs-lookup"><span data-stu-id="3c110-151">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="3c110-152">Les tableaux de bord peuvent être créés même par des utilisateurs non techniques.</span><span class="sxs-lookup"><span data-stu-id="3c110-152">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="3c110-153">La plupart des données qui résident dans l’index Elasticsearch peuvent être incluses dans les tableaux de bord Kibana.</span><span class="sxs-lookup"><span data-stu-id="3c110-153">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="3c110-154">Les utilisateurs individuels peuvent avoir différents tableaux de bord, et Kibana permet cette personnalisation en autorisant des tableaux de bord spécifiques à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3c110-154">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span>

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="3c110-155">Installation de la pile élastique sur Azure</span><span class="sxs-lookup"><span data-stu-id="3c110-155">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="3c110-156">La pile élastique peut être installée sur Azure de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="3c110-156">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="3c110-157">Comme toujours, il est possible d' [approvisionner des machines virtuelles et d’y installer directement la pile élastique](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span><span class="sxs-lookup"><span data-stu-id="3c110-157">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="3c110-158">Cette option est recommandée par certains utilisateurs expérimentés, car elle offre le degré de personnalisation le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="3c110-158">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="3c110-159">Le déploiement sur infrastructure as a service introduit une surcharge de gestion importante qui oblige les personnes qui utilisent ce chemin d’accès à prendre possession de toutes les tâches associées à infrastructure as a service telles que la sécurisation des ordinateurs et la mise à jour des correctifs.</span><span class="sxs-lookup"><span data-stu-id="3c110-159">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span>

<span data-ttu-id="3c110-160">Une option avec moins de surcharge consiste à utiliser l’un des nombreux conteneurs d’ancrage sur lesquels la pile élastique a déjà été configurée.</span><span class="sxs-lookup"><span data-stu-id="3c110-160">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="3c110-161">Ces conteneurs peuvent être déposés dans un cluster Kubernetes existant et exécutés avec le code d’application.</span><span class="sxs-lookup"><span data-stu-id="3c110-161">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="3c110-162">Le conteneur [sebp/Elk](https://elk-docker.readthedocs.io/) est un conteneur de pile élastique bien documenté et testé.</span><span class="sxs-lookup"><span data-stu-id="3c110-162">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="3c110-163">Une autre option est une [offre de kit en tant que service récemment annoncée](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="3c110-163">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="3c110-164">References</span><span class="sxs-lookup"><span data-stu-id="3c110-164">References</span></span>

- [<span data-ttu-id="3c110-165">Installer la pile élastique sur Azure</span><span class="sxs-lookup"><span data-stu-id="3c110-165">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="3c110-166">[Précédent](observability-patterns.md) 
> [Suivant](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="3c110-166">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
