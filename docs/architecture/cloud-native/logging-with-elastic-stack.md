---
title: Journalisation avec Elastic Stack
description: Journalisation à l’aide de la pile élastique, Logstash et Kibana
ms.date: 05/13/2020
ms.openlocfilehash: 32d9d0dae175d8d45d48b56d17f133b4cc432363
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811169"
---
# <a name="logging-with-elastic-stack"></a>Journalisation avec Elastic Stack

Il existe de nombreux outils de journalisation centralisés et leur coût est inférieur à celui des outils open source gratuits, à des options plus coûteuses. Dans de nombreux cas, les outils gratuits sont aussi bons ou mieux que les offres payantes. L’un de ces outils est une combinaison de trois composants Open Source : la recherche élastique, Logstash et Kibana.

Ces outils sont appelés pile élastique ou pile ELK.

## <a name="elastic-stack"></a>Pile élastique

La pile élastique est une option puissante pour la collecte d’informations à partir d’un cluster Kubernetes. Kubernetes prend en charge l’envoi de journaux à un point de terminaison Elasticsearch. dans la [plupart](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)des cas, vous devez commencer par définir les variables d’environnement, comme illustré dans la figure 7-5 :

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**Figure 7-5**. Variables de configuration pour Kubernetes

Cette opération installe Elasticsearch sur le cluster et cible l’envoi de tous les journaux de cluster vers ce dernier.

![Exemple de tableau de bord Kibana présentant les résultats d’une requête sur les journaux ingérés à partir de la ](./media/kibana-dashboard.png)
 **figure 7-6**de Kubernetes. Exemple de tableau de bord Kibana indiquant les résultats d’une requête sur les journaux qui sont ingérés à partir de Kubernetes

## <a name="what-are-the-advantages-of-elastic-stack"></a>Quels sont les avantages de la pile élastique ?

La pile élastique fournit une journalisation centralisée dans une solution cloud conviviale et évolutive. Son interface utilisateur simplifie l’analyse des données, ce qui vous permet de consacrer du temps à la collecte d’informations à partir de vos données au lieu de combattre une interface plus sourde. Il prend en charge un large éventail d’entrées, de sorte que votre application distribuée s’étend sur de plus en plus de types de services différents, vous pouvez vous attendre à pouvoir continuer à alimenter le journal et les données de métriques dans le système. La pile élastique prend également en charge les recherches rapides, même dans les jeux de données volumineux, ce qui permet de consigner les données détaillées dans des applications volumineuses, tout en étant en mesure de les visualiser de manière performante.

## <a name="logstash"></a>Logstash

Le premier composant est [Logstash](https://www.elastic.co/products/logstash). Cet outil est utilisé pour collecter des informations de journalisation à partir d’une grande variété de sources différentes. Par exemple, Logstash peut lire les journaux à partir du disque et recevoir également des messages des bibliothèques de journalisation telles que [Serilog](https://serilog.net/). Logstash peut effectuer un filtrage et une expansion de base sur les journaux au fur et à mesure de leur arrivée. Par exemple, si vos journaux contiennent des adresses IP, Logstash peut être configuré pour effectuer une recherche géographique et obtenir un pays ou même une ville d’origine pour ce message.

Serilog est une bibliothèque de journalisation pour les langages .NET, qui permet la journalisation paramétrée. Au lieu de générer un message de journalisation qui incorpore des champs, les paramètres sont conservés séparément. Cela permet un filtrage et une recherche plus intelligents. Un exemple de configuration Serilog pour l’écriture dans Logstash apparaît dans la figure 7-7.

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

**Figure 7-7**. Configuration de Serilog pour écrire des informations de journal directement dans logstash sur HTTP

Logstash utilise une configuration telle que celle illustrée dans la figure 7-8.

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

**Figure 7-8**. Une configuration Logstash pour la consommation des journaux à partir de Serilog

Dans les scénarios où une manipulation de journal étendue n’est pas nécessaire, il existe une alternative à Logstash appelée [temps](https://www.elastic.co/products/beats). Le temps est une famille d’outils qui peuvent recueillir un large éventail de données à partir des journaux vers les données réseau et les informations de temps d’activité. De nombreuses applications utilisent à la fois les Logstash et les temps.

Une fois les journaux collectés par Logstash, il faut les placer. Bien que Logstash prenne en charge de nombreuses sorties différentes, l’une des plus intéressantes est la recherche élastique.

## <a name="elastic-search"></a>Recherche élastique

La recherche élastique est un moteur de recherche puissant qui peut indexer les journaux à mesure qu’ils arrivent. Elle accélère l’exécution des requêtes sur les journaux. La recherche élastique peut gérer de grandes quantités de journaux et, dans des cas extrêmes, peut être montée en charge sur plusieurs nœuds.

Les messages de journal qui ont été conçus pour contenir des paramètres ou dont les paramètres ont été fractionnés à l’aide du traitement Logstash peuvent être interrogés directement, car Elasticsearch conserve ces informations.

Une requête qui recherche les 10 premières pages visitées par `jill@example.com` , apparaît dans la Figure 7-9.

```json
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

**Figure 7-9**. Requête Elasticsearch pour rechercher les 10 premières pages visitées par un utilisateur

## <a name="visualizing-information-with-kibana-web-dashboards"></a>Visualisation des informations avec les tableaux de bord Web Kibana

Le composant final de la pile est Kibana. Cet outil est utilisé pour fournir des visualisations interactives dans un tableau de bord Web. Les tableaux de bord peuvent être créés même par des utilisateurs non techniques. La plupart des données qui résident dans l’index Elasticsearch peuvent être incluses dans les tableaux de bord Kibana. Les utilisateurs individuels peuvent avoir différents tableaux de bord, et Kibana permet cette personnalisation en autorisant des tableaux de bord spécifiques à l’utilisateur.

## <a name="installing-elastic-stack-on-azure"></a>Installation de la pile élastique sur Azure

La pile élastique peut être installée sur Azure de plusieurs façons. Comme toujours, il est possible d' [approvisionner des machines virtuelles et d’y installer directement la pile élastique](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch). Cette option est recommandée par certains utilisateurs expérimentés, car elle offre le degré de personnalisation le plus élevé. Le déploiement sur infrastructure as a service introduit une surcharge de gestion importante qui oblige les personnes qui utilisent ce chemin d’accès à prendre possession de toutes les tâches associées à infrastructure as a service telles que la sécurisation des ordinateurs et la mise à jour des correctifs.

Une option avec moins de surcharge consiste à utiliser l’un des nombreux conteneurs d’ancrage sur lesquels la pile élastique a déjà été configurée. Ces conteneurs peuvent être déposés dans un cluster Kubernetes existant et exécutés avec le code d’application. Le conteneur [sebp/Elk](https://elk-docker.readthedocs.io/) est un conteneur de pile élastique bien documenté et testé.

Une autre option est une [offre de kit en tant que service récemment annoncée](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).

## <a name="references"></a>Références

- [Installer la pile élastique sur Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
>[Précédent](observability-patterns.md) 
> [Suivant](monitoring-azure-kubernetes.md)
