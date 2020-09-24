---
title: Résilience de la plateforme Azure
description: Architecture des applications .NET natives Cloud pour Azure | Résilience de l’infrastructure cloud avec Azure
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 88634bc60df15cc93b1769a85879795ae383757a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163763"
---
# <a name="azure-platform-resiliency"></a>Résilience de la plateforme Azure

La création d’une application fiable dans le Cloud est différente du développement d’applications locales traditionnelles. Bien que vous ayez acheté un matériel de haut niveau pour monter en puissance, dans un environnement Cloud, vous augmentez l’échelle. Au lieu de tenter d’éviter les défaillances, l’objectif est de réduire leurs effets et de maintenir la stabilité du système.

Cela dit, les applications Cloud fiables affichent des caractéristiques distinctes :

- Ils sont résilients, récupèrent correctement des problèmes et continuent de fonctionner.
- Ils sont hautement disponibles et s’exécutent comme étant conçus dans un état sain, sans temps d’arrêt significatif.

Comprendre comment ces caractéristiques fonctionnent ensemble et comment elles ont une incidence sur le coût est essentiel à la création d’une application fiable Cloud-native. Nous allons ensuite étudier les différentes façons dont vous pouvez créer la résilience et la disponibilité dans vos applications Cloud natives en tirant parti des fonctionnalités du Cloud Azure.

## <a name="design-with-resiliency"></a>Conception avec résilience

Nous avons dit que la résilience permet à votre application de réagir à une défaillance tout en restant fonctionnelle. Le livre blanc, [résilience dans le livre blanc Azure](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf), fournit des conseils pour obtenir une résilience dans la plateforme Azure. Voici quelques recommandations clés :

- *Défaillance matérielle.* Intégrez la redondance dans l’application en déployant des composants dans différents domaines d’erreur. Par exemple, assurez-vous que les machines virtuelles Azure sont placées dans des racks différents à l’aide de groupes à haute disponibilité.

- *Échec du centre de.* Intégrez la redondance à l’application avec des zones d’isolation des erreurs dans les centres de centres. Par exemple, assurez-vous que les machines virtuelles Azure sont placées dans différents centres de centres d’erreur isolés à l’aide de Zones de disponibilité Azure.

- *Défaillance régionale.* Répliquez les données et les composants dans une autre région afin que les applications puissent être récupérées rapidement. Par exemple, utilisez Azure Site Recovery pour répliquer des machines virtuelles Azure vers une autre région Azure.

- *Charge lourde.* Équilibrer la charge entre les instances pour gérer les pics d’utilisation. Par exemple, placez au moins deux machines virtuelles Azure derrière un équilibreur de charge pour répartir le trafic vers toutes les machines virtuelles.

- *Suppression accidentelle ou altération des données.* Sauvegardez les données afin qu’elles puissent être restaurées en cas de suppression ou d’endommagement. Par exemple, utilisez Azure Backup pour sauvegarder périodiquement vos machines virtuelles Azure.

## <a name="design-with-redundancy"></a>Conception avec redondance

L'ampleur de l'impact des défaillances est variable. Une défaillance matérielle, telle qu’un disque défaillant, peut affecter un nœud unique dans un cluster. Mais un commutateur réseau défaillant peut impacter un rack tout entier de serveurs. Les défaillances moins courantes, telles que la perte de puissance, peuvent perturber l’ensemble d’un centre de donné. Exceptionnellement, une région entière peut être indisponible.

La [redondance](/azure/architecture/guide/design-principles/redundancy) est un moyen d’assurer la résilience des applications. Le niveau exact de redondance nécessaire dépend des besoins de votre entreprise et a un impact sur le coût et la complexité de votre système. Par exemple, un déploiement sur plusieurs régions est plus onéreux et plus complexe à gérer qu’un déploiement sur une seule région. Vous aurez besoin de procédures opérationnelles pour gérer le basculement et la restauration automatique. Les coûts et la complexité supplémentaires peuvent être justifiés pour certains scénarios d’entreprise, mais pas pour d’autres.

Pour concevoir la redondance, vous devez identifier les chemins critiques dans votre application, puis déterminer s’il existe une redondance à chaque point du chemin d’accès ? En cas d’échec d’un sous-système, l’application bascule-t-elle vers autre chose ? Enfin, vous avez besoin d’une compréhension claire des fonctionnalités intégrées à la plateforme Cloud Azure que vous pouvez exploiter pour répondre à vos besoins en matière de redondance. Voici des recommandations pour l’architecture de la redondance :

- *Déployez plusieurs instances des services.* Si votre application repose sur une seule instance unique d’un service, cela crée un point de défaillance unique. L’approvisionnement de plusieurs instances améliore à la fois la résilience et l’extensibilité. Lors de l’hébergement dans le service Azure Kubernetes, vous pouvez configurer de manière déclarative des instances redondantes (jeux de réplicas) dans le fichier manifeste Kubernetes. La valeur du nombre de réplicas peut être gérée par programme, dans le portail ou à l’aide des fonctionnalités de mise à l’échelle automatique.

- *Utilisation d’un équilibreur de charge.* L’équilibrage de charge distribue les demandes de votre application à des instances de service saines et supprime automatiquement les instances défectueuses de la rotation. Lors du déploiement sur Kubernetes, l’équilibrage de charge peut être spécifié dans le fichier manifeste Kubernetes de la section services.

- *Planifier un déploiement à régions.* Si vous déployez votre application dans une seule région et que cette région n’est plus disponible, votre application devient également indisponible. Cela peut être inacceptable selon les termes des contrats de niveau de service de votre application. Au lieu de cela, envisagez de déployer votre application et ses services dans plusieurs régions. Par exemple, un cluster Azure Kubernetes service (AKS) est déployé dans une seule région. Pour protéger votre système contre les défaillances régionales, vous pouvez déployer votre application sur plusieurs clusters AKS dans différentes régions et utiliser la fonctionnalité de [régions jumelées](https://buildazure.com/2017/01/06/azure-region-pairs-explained/) pour coordonner les mises à jour de plateforme et hiérarchiser les efforts de récupération.

- *Activez [la géo-réplication](/azure/sql-database/sql-database-active-geo-replication).* La géo-réplication pour des services tels que Azure SQL Database et Cosmos DB créera des réplicas secondaires de vos données dans plusieurs régions. Alors que les deux services répliquent automatiquement les données dans la même région, la géo-réplication vous protège contre une panne régionale en vous permettant de basculer vers une région secondaire. Une autre pratique recommandée pour la géo-réplication consiste à stocker des images de conteneur. Pour déployer un service dans AKS, vous devez stocker et extraire l’image à partir d’un référentiel. Azure Container Registry s’intègre à AKS et peut stocker des images de conteneur en toute sécurité. Pour améliorer les performances et la disponibilité, envisagez de géo-répliquer vos images dans un registre dans chaque région où vous disposez d’un cluster AKS. Chaque cluster AKS extrait ensuite les images de conteneur à partir du registre de conteneurs local dans sa région, comme le montre la figure 6-4 :

![Ressources répliquées dans les régions](./media/replicated-resources.png)

**Figure 6-4**. Ressources répliquées dans les régions

- *Implémentez un équilibreur de charge du trafic DNS.* [Azure Traffic Manager](/azure/traffic-manager/traffic-manager-overview) fournit une haute disponibilité pour les applications critiques en équilibrant la charge au niveau du DNS. Il peut acheminer le trafic vers différentes régions en fonction de la géographie, du temps de réponse du cluster et même de l’intégrité du point de terminaison d’application. Par exemple, Azure Traffic Manager peut diriger les clients vers l’instance d’application et le cluster AKS le plus proche. Si vous possédez plusieurs clusters AKS dans différentes régions, utilisez Traffic Manager pour contrôler la façon dont le trafic afflue vers les applications qui s’exécutent dans chaque cluster. La figure 6-5 illustre ce scénario.

![AKS et Azure Traffic Manager](./media/aks-traffic-manager.png)

**Figure 6-5.** AKS et Azure Traffic Manager

## <a name="design-for-scalability"></a>Conception dans l’optique de la scalabilité

Le Cloud est très prospère en matière de mise à l’échelle. La possibilité d’augmenter ou de diminuer les ressources système pour résoudre la charge système en hausse/en baisse est un principe essentiel du Cloud Azure. Toutefois, pour mettre à l’échelle efficacement une application, vous devez comprendre les fonctionnalités de mise à l’échelle de chaque service Azure que vous incluez dans votre application.  Voici des recommandations pour implémenter efficacement la mise à l’échelle dans votre système.

- *Concevez pour la mise à l’échelle.* Une application doit être conçue pour la mise à l’échelle. Pour commencer, les services doivent être sans État afin que les demandes puissent être routées vers n’importe quelle instance. L’utilisation de services sans état signifie également que l’ajout ou la suppression d’une instance n’a pas d’impact négatif sur les utilisateurs actuels.

- *Partitionner les charges de travail*. La décomposition de domaines en microservices indépendants et autonomes permet à chaque service de se mettre à l’échelle indépendamment des autres. En règle générale, les services ont des besoins et des exigences d’évolutivité différents. Le partitionnement vous permet de mettre à l’échelle uniquement ce qui doit être mis à l’échelle sans le coût inutile de mise à l’échelle d’une application entière.

- *Privilégiez la montée en* puissance parallèle. Les applications basées sur le Cloud favorisent la montée en charge des ressources par opposition à la montée en puissance. La montée en charge (également appelée mise à l’échelle horizontale) implique l’ajout de ressources de service supplémentaires à un système existant pour atteindre et partager un niveau de performances souhaité. La montée en puissance (également appelée mise à l’échelle verticale) implique de remplacer les ressources existantes par du matériel plus puissant (plus de disques, de mémoire et de cœurs de traitement). La montée en charge peut être automatiquement appelée avec les fonctionnalités de mise à l’échelle automatique disponibles dans certaines ressources de Cloud Azure. La montée en charge sur plusieurs ressources ajoute également une redondance à l’ensemble du système. Enfin, la mise à l’échelle d’une ressource unique est généralement plus coûteuse que la montée en charge sur de nombreuses ressources plus petites. La figure 6-6 illustre les deux approches :

![Évolution verticale et montée en puissance parallèle](./media/scale-up-scale-out.png)

**Figure 6-6.** Évolution verticale et montée en puissance parallèle

- *Mettre à l’échelle proportionnellement.* Lors de la mise à l’échelle d’un service, pensez aux *jeux de ressources*. Si vous deviez augmenter considérablement la capacité d’un service spécifique, quel impact aurait-il sur les magasins de données principaux, les caches et les services dépendants ? Certaines ressources, telles que Cosmos DB, peuvent être mises à l’échelle proportionnellement, tandis que beaucoup d’autres ne le sont pas. Vous souhaitez vous assurer que vous n’augmentez pas la mise à l’échelle d’une ressource à un point où elle épuise les autres ressources associées.

- *Évitez les affinités.* Une meilleure pratique consiste à s’assurer qu’un nœud ne nécessite pas d’affinité locale, souvent appelée *session rémanente*. Une demande doit pouvoir être acheminée vers n’importe quelle instance. Si vous devez conserver l’État, il doit être enregistré dans un cache distribué, tel que le [cache redims Azure](https://azure.microsoft.com/services/cache/).

- *Tirez parti des fonctionnalités de mise à l’échelle automatique de la plateforme.* Utilisez les fonctionnalités de mise à l’échelle automatique dans la mesure du possible, au lieu de mécanismes personnalisés ou tiers. Dans la mesure du possible, utilisez des règles de mise à l’échelle planifiées pour vous assurer que les ressources sont disponibles sans délai de démarrage, mais ajoutez la mise à l’échelle automatique réactive aux règles, le cas échéant, afin de faire face aux modifications inattendues de la demande. Pour plus d’informations, consultez [Recommandations en matière de mise à l’échelle automatique](/azure/architecture/best-practices/auto-scaling).

- *Montée en charge de manière agressive.* Une dernière pratique serait de monter en puissance de façon agressive afin que vous puissiez répondre rapidement aux pics immédiats du trafic sans perdre votre activité. Et, puis mettre à l’échelle dans (autrement dit, supprimer les instances inutiles) de manière conservatrice pour garantir la stabilité du système. Un moyen simple d’implémenter cela consiste à définir la période de refroidissement, qui est le temps d’attente entre les opérations de mise à l’échelle, à cinq minutes pour l’ajout de ressources et jusqu’à 15 minutes pour la suppression des instances.

## <a name="built-in-retry-in-services"></a>Nouvelle tentative intégrée dans les services

Nous avons encouragé la meilleure pratique qui consiste à implémenter des opérations de nouvelle tentative par programmation dans une section précédente. Gardez à l’esprit que de nombreux services Azure et leurs kits de développement logiciel (SDK) clients correspondants incluent également des mécanismes de nouvelle tentative. La liste suivante récapitule les fonctionnalités des nouvelles tentatives dans les nombreux services Azure qui sont abordés dans ce document :

- *Azure Cosmos DB.* La <xref:Microsoft.Azure.Documents.Client.DocumentClient> classe de l’API client retire automatiquement les tentatives ayant échoué. Le nombre de nouvelles tentatives et le délai d’attente maximal peuvent être configurés. Les exceptions levées par l’API client sont soit des demandes qui dépassent la stratégie de nouvelle tentative, soit des erreurs non temporaires.

- *Cache Redims Azure.* Le client StackExchanges ReDim utilise une classe de gestionnaire de connexions qui comprend les nouvelles tentatives en cas d’échec. Le nombre de nouvelles tentatives, la stratégie de nouvelle tentative spécifique et le temps d’attente sont tous configurables.

- *Azure Service Bus.* Le client Service Bus expose une [classe RetryPolicy](xref:Microsoft.ServiceBus.RetryPolicy) qui peut être configurée avec un intervalle d’interruption, le nombre de tentatives, et <xref:Microsoft.ServiceBus.RetryExponential.TerminationTimeBuffer%2A> , qui spécifie la durée maximale qu’une opération peut prendre. La stratégie par défaut est de neuf tentatives de nouvelle tentative au maximum, avec une période d’interruption de 30 secondes entre chaque tentative.

- *Azure SQL Database.* La prise en charge des nouvelles tentatives est fournie lors de l’utilisation de la bibliothèque de [Entity Framework Core](/ef/core/miscellaneous/connection-resiliency) .

- *Stockage Azure.* La bibliothèque cliente de stockage prend en charge les opérations de nouvelle tentative. Les stratégies varient selon les tables, les objets BLOB et les files d’attente Azure Storage. De même, les autres tentatives basculent entre les emplacements des services de stockage principaux et secondaires lorsque la fonctionnalité de géoredondance est activée.

- *Event Hubs Azure.* La bibliothèque cliente Event Hub comporte une propriété RetryPolicy, qui comprend une fonctionnalité d’interruption exponentielle configurable.

>[!div class="step-by-step"]
>[Précédent](application-resiliency-patterns.md) 
> [Suivant](resilient-communications.md)
