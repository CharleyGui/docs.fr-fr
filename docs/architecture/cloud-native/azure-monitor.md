---
title: Azure Monitor
description: L’utilisation de Azure Monitor pour obtenir une visibilité de votre système est en cours d’exécution.
ms.date: 07/05/2020
ms.openlocfilehash: 65e17740dba49c3ac3f6e13462897b5342da6710
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160968"
---
# <a name="azure-monitor"></a>Azure Monitor

Aucun autre fournisseur de Cloud n’a été aussi mature qu’une solution de surveillance des applications Cloud que celle qui se trouvait dans Azure. Azure Monitor est un nom de parapluie pour un ensemble d’outils conçus pour offrir une visibilité de l’état de votre système. Il vous aide à comprendre comment vos services Cloud natifs fonctionnent et identifie de manière proactive les problèmes qui les affectent. La figure 7-12 présente un haut niveau de vue des Azure Monitor.

![Affichage de haut niveau des Azure Monitor. ](./media/azure-monitor.png)
 **Figure 7-12**. Affichage de haut niveau des Azure Monitor.

## <a name="gathering-logs-and-metrics"></a>Collecte des journaux et des métriques

La première étape d’une solution de surveillance consiste à rassembler le plus de données possible. Plus le nombre de données collectées est élevé, plus les Insights sont précises. L’instrumentation des systèmes a toujours été difficile. Le protocole SNMP (simple Network Management Protocol) était le protocole Gold standard pour la collecte d’informations au niveau de l’ordinateur, mais il nécessitait beaucoup de connaissances et de configuration. Heureusement, une grande partie de ce travail a été éliminée, car les métriques les plus courantes sont collectées automatiquement par Azure Monitor.

Les métriques et les événements au niveau de l’application ne peuvent pas être instrumentés automatiquement, car ils sont spécifiques à l’application déployée. Pour rassembler ces mesures, des kits de développement logiciel ( [SDK) et des API sont disponibles](/azure/azure-monitor/app/api-custom-events-metrics) pour signaler directement ces informations, par exemple lorsqu’un client s’inscrit ou termine une commande. Les exceptions peuvent également être capturées et renvoyées dans Azure Monitor via Application Insights. Les kits de développement logiciel (SDK) prennent en charge la plupart des langages disponibles dans les applications Cloud natives, y compris Go, Python, JavaScript et les langages .NET.

L’objectif ultime de la collecte d’informations sur l’état de votre application est de s’assurer que vos utilisateurs finaux ont une bonne expérience. Quelle est la meilleure façon de savoir si les utilisateurs rencontrent des problèmes que d’effectuer des [tests Web externes](/azure/azure-monitor/app/monitor-web-app-availability)? Ces tests peuvent être aussi simples que l’utilisation d’une commande ping sur votre site Web à partir d’emplacements du monde entier ou en cas de connexion des agents au site et de simulation des actions des utilisateurs.

## <a name="reporting-data"></a>Données de rapport

Une fois les données collectées, elles peuvent être manipulées, synthétisées et tracées dans des graphiques, ce qui permet aux utilisateurs de voir instantanément quand il y a des problèmes. Ces graphiques peuvent être rassemblés dans des tableaux de bord ou dans des classeurs, un rapport à plusieurs pages conçu pour raconter un récit sur certains aspects du système.

Aucune application moderne n’est complète sans intelligence artificielle ni Machine Learning. À cette fin, les données [peuvent être transmises](https://www.youtube.com/watch?v=Cuza-I1g9tw) aux différents outils de machine learning dans Azure pour vous permettre d’extraire les tendances et les informations qui seraient autrement masquées.

Application Insights fournit un langage de requête puissant (similaire à SQL) appelé *Kusto* qui peut interroger des enregistrements, les résumer et même tracer des graphiques. Par exemple, la requête suivante localise tous les enregistrements pour le mois de novembre 2007, les regroupe par État et les 10 premiers sous forme de graphique à secteurs.

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

La figure 7-13 montre les résultats de cette requête Application Insights.

![Application Insights les résultats de la requête ](./media/application_insights_example.png)
 ,**figure 7-13**. Application Insights les résultats de la requête.

Il existe un [terrain pour expérimenter les requêtes Kusto](https://dataexplorer.azure.com/clusters/help/databases/Samples) . La lecture des [exemples de requêtes](/azure/kusto/query/samples) peut également être instructive.

## <a name="dashboards"></a>Tableaux de bord

Il existe plusieurs technologies de tableau de bord différentes qui peuvent être utilisées pour mettre en surface les informations de Azure Monitor. Le plus simple consiste peut-être simplement à exécuter des requêtes dans Application Insights et à [tracer les données dans un graphique](/azure/azure-monitor/learn/tutorial-app-dashboards).

![Voici un exemple de Application Insights graphiques incorporés dans le tableau de bord principal Azure ](./media/azure_dashboard.png)
 **figure 7-14**. Voici un exemple de Application Insights graphiques incorporés dans le tableau de bord principal Azure.

Ces graphiques peuvent ensuite être incorporés dans le Portail Azure correctement à l’aide de la fonctionnalité de tableau de bord. Pour les utilisateurs ayant des exigences plus précises, telles que la possibilité d’accéder à plusieurs niveaux de données, Azure Monitor données sont disponibles pour les [Power bi](https://powerbi.microsoft.com/). Power BI est un outil d’analyse décisionnelle à la pointe du secteur, qui peut agréger des données à partir de nombreuses sources de données différentes.

![Exemple de tableau de bord Power BI](./media/powerbidashboard.png)

**Figure 7-15**. Exemple Power BI tableau de bord.

## <a name="alerts"></a>Alertes

Parfois, le fait d’avoir des tableaux de bord de données est insuffisant. Si personne n’est en éveil pour regarder les tableaux de bord, il peut toujours y avoir plusieurs heures avant que le problème soit résolu, voire détecté. À cette fin, Azure Monitor fournit également une solution d' [alerte](/azure/azure-monitor/platform/alerts-overview)de pointe. Les alertes peuvent être déclenchées par un large éventail de conditions, notamment :

- Valeurs de métrique
- Requêtes de recherche de journal
- Événements du journal d'activité
- Contrôle d’intégrité de la plateforme Azure sous-jacente
- Tests de disponibilité des sites web

Lorsqu’elles sont déclenchées, les alertes peuvent effectuer une grande variété de tâches. Du côté simple, les alertes peuvent simplement envoyer une notification par courrier électronique à une liste de diffusion ou un message texte à une personne. Des alertes plus impliquées peuvent déclencher un flux de travail dans un outil tel que PagerDuty, qui est à l’origine de l’appel d’une application particulière. Les alertes peuvent déclencher des actions dans [Microsoft Flow](https://flow.microsoft.com/) le déverrouillage des possibilités presque illimitées pour les flux de travail.

Comme les causes courantes des alertes sont identifiées, les alertes peuvent être améliorées avec des détails sur les causes courantes des alertes et les étapes à suivre pour les résoudre. Les déploiements d’applications Cloud-natives très matures peuvent choisir de déclencher des tâches de réparation spontanée, qui effectuent des actions telles que la suppression de nœuds défaillants d’un groupe identique ou le déclenchement d’une activité de mise à l’échelle automatique. Il se peut qu’il ne soit plus nécessaire de réveiller le personnel sur 2AM pour résoudre un problème de site actif, car le système sera en mesure de s’adapter pour compenser ou au moins LIMP, jusqu’à ce que quelqu’un arrive au travail le lendemain matin.

Azure Monitor s’appuie automatiquement sur Machine Learning pour comprendre les paramètres de fonctionnement normaux des applications déployées. Cela lui permet de détecter les services qui fonctionnent en dehors de leurs paramètres normaux. Par exemple, le trafic de jour de la semaine classique sur le site peut être de 10 000 demandes par minute. Puis, pour une semaine donnée, soudain, le nombre de demandes atteint un nombre de demandes 20 000 très inhabituelles par minute. La [détection intelligente](/azure/azure-monitor/app/proactive-diagnostics) remarquera cet écart par rapport à la norme et déclenchera une alerte. En même temps, l’analyse des tendances est suffisamment intelligente pour éviter de déclencher des faux positifs lorsque la charge du trafic est attendue.

## <a name="references"></a>Références

- [Azure Monitor](/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Précédent](monitoring-azure-kubernetes.md) 
> [Suivant](identity.md)
