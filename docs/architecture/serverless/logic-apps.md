---
title: Applications sans serveur Azure Logic Apps
description: Azure Logic Apps activer la création de flux de travail évolutifs automatisés qui intègrent des applications et des données dans les services Cloud et les systèmes locaux.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577452"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) fournit un moteur sans serveur pour créer des flux de travail automatisés pour intégrer des applications et des données entre les services Cloud et les systèmes locaux. Vous générez des flux de travail à l’aide d’un concepteur visuel. Vous pouvez déclencher des flux de travail basés sur des événements ou des minuteurs et tirer parti des connecteurs pour les applications d’intégration et faciliter la communication entre entreprises (B2B). Logic Apps s’intègre parfaitement à Azure Functions.

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

Logic Apps pouvez faire plus que connecter simplement vos services Cloud (comme les fonctions) aux ressources cloud (telles que les files d’attente et les bases de données). Vous pouvez également orchestrer des flux de travail locaux avec la passerelle locale. Par exemple, vous pouvez utiliser l’application logique pour déclencher une procédure stockée SQL locale en réponse à un événement basé sur le Cloud ou à une logique conditionnelle dans votre flux de travail. En savoir plus sur la [connexion aux sources de données locales avec la passerelle de données locale Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Architecture Logic Apps](./media/logic-apps-architecture.png)

Comme Azure Functions, vous démarrez les workflows d’application logique avec un déclencheur. Vous pouvez choisir parmi de nombreux déclencheurs. La capture suivante présente quelques-unes des centaines de centaines disponibles parmi les plus populaires.

![Déclencheurs Logic Apps](./media/logic-app-triggers.png)

Une fois l’application déclenchée, vous pouvez utiliser le concepteur visuel pour créer des étapes, des boucles, des conditions et des actions. Toutes les données ingérées au cours d’une étape précédente sont disponibles pour être utilisées dans les étapes suivantes. Le flux de travail suivant charge les URL à partir d’une base de données CosmosDB. Il trouve ceux qui ont un hôte `t.co` , puis les recherche sur Twitter. S’il trouve des tweets correspondants, il met à jour les documents avec les tweets associés en appelant une fonction.

![Flux de travail d’application logique](./media/logic-app-workflow.png)

Le tableau de bord Logic Apps affiche l’historique de l’exécution de vos workflows et indique si chaque exécution s’est terminée correctement. Vous pouvez naviguer dans une exécution donnée et inspecter les données utilisées par chaque étape pour la résolution des problèmes. Logic Apps fournit également des modèles existants que vous pouvez modifier et qui conviennent parfaitement aux flux de travail d’entreprise complexes.

Pour plus d’informations, consultez [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Précédent](application-insights.md)
>[Suivant](event-grid.md)
