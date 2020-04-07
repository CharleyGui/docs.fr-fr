---
title: Azure Monitor
description: L’utilisation d’Azure Monitor pour gagner en visibilité sur votre système est en cours d’exécution.
ms.date: 02/05/2020
ms.openlocfilehash: 4e5ddba6c1c13dc65662a7748d4ae3a58a6a6f68
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805631"
---
# <a name="azure-monitor"></a>Azure Monitor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aucun autre fournisseur de cloud n’a autant de maturité qu’une solution de surveillance d’applications cloud que celle trouvée dans Azure. Azure Monitor est un nom générique pour une collection d’outils conçus pour fournir une visibilité sur l’état de votre système, des informations sur tous les problèmes et l’optimisation de votre application.

![Azure Monitor, une collection d’outils pour donner un aperçu du fonctionnement d’une application cloud-native. ](./media/azure-monitor.png)
 **Figure 7-12**. Azure Monitor, une collection d’outils pour donner un aperçu du fonctionnement d’une application cloud-native.

## <a name="gathering-logs-and-metrics"></a>Collecte de journaux et de mesures

La première étape de toute solution de surveillance consiste à recueillir autant de données que possible. Plus il y a de données à recueillir, plus les idées peuvent être obtenues. Les systèmes d’instrumentation ont toujours été difficiles. Le protocole de gestion du réseau simple (SNMP) était le protocole de référence pour recueillir des informations au niveau de la machine, mais il a exigé beaucoup de connaissances et de configuration. Heureusement, une grande partie de ce travail acharné a été éliminée car les mesures les plus courantes sont recueillies automatiquement par Azure Monitor.

Les mesures et les événements de niveau d’application ne sont pas possibles d’instrumenter automatiquement parce qu’ils sont spécifiques à l’application déployée. Afin de recueillir ces mesures, il existe [des SDK et des API disponibles](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) pour signaler directement ces informations, par exemple lorsqu’un client s’inscrit ou termine une commande. Des exceptions peuvent également être capturées et signalées dans Azure Monitor via Application Insights. Les SDK prennent en charge la plupart de toutes les langues trouvées dans les applications natives Cloud, y compris Go, Python, JavaScript, et les langues .NET.

Le but ultime de recueillir des informations sur l’état de votre application est de s’assurer que vos utilisateurs finaux ont une bonne expérience. Quelle meilleure façon de savoir si les utilisateurs éprouvent des problèmes que de faire [des tests Web extérieurs](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability)? Ces tests peuvent être aussi simples que de ping votre site Web à partir d’endroits à travers le monde ou aussi impliqués que d’avoir des agents se connecter dans le site et simuler les actions des utilisateurs.

## <a name="reporting-data"></a>Reporting des données

Une fois les données recueillies, elles peuvent être manipulées, résumées et tracées dans des graphiques, qui permettent aux utilisateurs de voir instantanément quand il y a des problèmes. Ces graphiques peuvent être rassemblés dans des tableaux de bord ou dans workbooks, un rapport de plusieurs pages conçu pour raconter une histoire sur certains aspects du système.

Aucune application moderne ne serait complète sans une certaine intelligence artificielle ou l’apprentissage automatique. À cette fin, les données [peuvent être transmises](https://www.youtube.com/watch?v=Cuza-I1g9tw) aux différents outils d’apprentissage automatique d’Azure pour vous permettre d’extraire des tendances et des informations qui seraient autrement cachées.

Application Insights fournit un langage de requête puissant appelé Kusto qui peut être utilisé pour trouver des enregistrements, les résumer, et même tracer des graphiques. Par exemple, cette requête permettra de localiser tous les enregistrements pour le mois de Novembre 2007, les regrouper par état, et tracer le top 10 comme un graphique à secteurs.

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

![Le résultat de la requête](./media/azure-monitor.png)
d’application Insights**Figure 7-13**. Le résultat de la requête Application Insights.

Il ya un [terrain de jeu pour expérimenter avec les requêtes Kusto,](https://dataexplorer.azure.com/clusters/help/databases/Samples) qui est un endroit fantastique pour passer une heure ou deux. La lecture [des requêtes d’échantillons](https://docs.microsoft.com/azure/kusto/query/samples) peut également être instructive.

## <a name="dashboards"></a>Tableaux de bord

Il existe plusieurs technologies de tableau de bord différentes qui peuvent être utilisées pour faire surface les informations d’Azure Monitor. Peut-être le plus simple est de simplement exécuter des requêtes dans Application Insights et [tracer les données dans un graphique](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards).

![Un exemple de graphiques d’applications intégrés dans la figure principale du tableau de bord](./media/azure-monitor.png)
Azure**7-14**. Un exemple de graphiques d’applications insights intégrés dans le tableau de bord Azure principal.

Ces graphiques peuvent ensuite être intégrés dans le portail Azure correctement grâce à l’utilisation de la fonction de tableau de bord. Pour les utilisateurs ayant des exigences plus exigeantes, telles que la possibilité de forer vers le bas dans plusieurs niveaux de données, les données Azure Monitor est disponible pour [Power BI](https://powerbi.microsoft.com/). Power BI est un outil d’intelligence d’affaires de classe d’entreprise de premier plan qui peut agréger des données provenant de nombreuses sources de données différentes.

![Un exemple Power](./media/azure-monitor.png)
BI tableau de bord**Figure 7-15**. Un exemple de tableau de bord Power BI.

## <a name="alerts"></a>Alertes

Parfois, avoir des tableaux de bord de données est insuffisant. Si personne n’est éveillé pour regarder les tableaux de bord, alors il peut encore être de nombreuses heures avant qu’un problème est résolu, ou même détecté. À cette fin, Azure Monitor fournit également une [solution d’alerte](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview)de premier ordre. Les alertes peuvent être déclenchées par un large éventail de conditions, y compris :

- Valeurs de métrique
- Requêtes de recherche de journal
- Événements du journal d'activité
- Contrôle d’intégrité de la plateforme Azure sous-jacente
- Tests de disponibilité des sites web

Lorsqu’elles sont déclenchées, les alertes peuvent effectuer une grande variété de tâches. Sur le côté simple, les alertes peuvent simplement envoyer une notification par e-mail à une liste de diffusion ou un message texte à une personne. Des alertes plus impliquées pourraient déclencher un flux de travail dans un outil tel que PagerDuty, qui est au courant de qui est sur appel pour une application particulière. Les alertes peuvent déclencher des actions dans [Microsoft Flow](https://flow.microsoft.com/) déverrouillant des possibilités presque illimitées pour les flux de travail.

Au fur et à mesure que les causes courantes des alertes sont identifiées, les alertes peuvent être renforcées avec des détails sur les causes courantes des alertes et les mesures à prendre pour les résoudre. Les déploiements d’applications cloud-natives très matures peuvent choisir de lancer des tâches d’auto-guérison, qui effectuent des actions telles que la suppression des nœuds défaillants d’un ensemble d’échelle ou le déclenchement d’une activité d’autoscalage. Finalement, il ne sera peut-être plus nécessaire de réveiller le personnel de garde à 2 heures du matin pour résoudre un problème de site en direct que le système sera en mesure de s’ajuster pour compenser ou au moins boiter le long jusqu’à ce que quelqu’un arrive au travail le lendemain matin.

Azure Monitor tire automatiquement parti de l’apprentissage automatique pour comprendre les paramètres de fonctionnement normaux des applications déployées. Cela lui permet de détecter les services qui fonctionnent en dehors de leurs paramètres normaux. Par exemple, le trafic typique en semaine sur le site peut être de 10 000 demandes par minute. Et puis, sur une semaine donnée, tout à coup le nombre de demandes atteint un très inhabituel 20.000 demandes par minute. [Smart Detection](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) remarquera cette déviation par la norme et déclenchera une alerte. Dans le même temps, l’analyse des tendances est assez intelligente pour éviter de tirer de faux positifs lorsque la charge de trafic est prévue.

## <a name="references"></a>References

- [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Suivant précédent](monitoring-azure-kubernetes.md)
>[Next](identity.md)
