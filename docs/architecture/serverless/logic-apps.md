---
title: Azure Logic Apps - Applications sans serveur
description: Azure Logic Apps permet de construire des flux de travail évolutifs automatisés qui intègrent des applications et des données dans les services cloud et les systèmes sur site.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577452"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) fournit un moteur sans serveur pour construire des flux de travail automatisés pour intégrer des applications et des données entre les services cloud et les systèmes sur site. Vous construisez des flux de travail à l’aide d’un concepteur visuel. Vous pouvez déclencher des flux de travail en fonction d’événements ou de minuteries et tirer parti des connecteurs vers des applications d’intégration et faciliter la communication interentrant (B2B). Logic Apps s’intègre parfaitement avec Azure Functions.

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

Logic Apps peut faire plus que simplement connecter vos services cloud (comme les fonctions) avec des ressources cloud (comme les files d’attente et les bases de données). Vous pouvez également orchestrer des workflows sur place avec la passerelle sur place. Par exemple, vous pouvez utiliser l’application Logic pour déclencher une procédure stockée SQL sur place en réponse à un événement basé sur le cloud ou à une logique conditionnelle dans votre flux de travail. En savoir plus sur [la connexion aux sources de données sur site avec Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Architecture Logic Apps](./media/logic-apps-architecture.png)

Comme Azure Functions, vous lancez des workflows Logic App avec un déclencheur. Il ya beaucoup de déclencheurs pour vous de choisir. La capture suivante montre seulement quelques-uns des plus populaires sur des centaines qui sont disponibles.

![Déclencheurs Logic Apps](./media/logic-app-triggers.png)

Une fois l’application déclenchée, vous pouvez utiliser le concepteur visuel pour créer des étapes, des boucles, des conditions et des actions. Toutes les données ingérées lors d’une étape précédente sont disponibles pour que vous utilisiez dans les étapes suivantes. Le flux de travail suivant charge les URL d’une base de données CosmosDB. Il trouve ceux avec une `t.co` foule de recherches alors pour eux sur Twitter. S’il trouve des tweets correspondants, il met à jour les documents avec les tweets connexes en appelant une fonction.

![Flux de travail Logic App](./media/logic-app-workflow.png)

Le tableau de bord Logic Apps montre l’historique de l’exécution de vos flux de travail et si chaque exécution est terminée avec succès ou non. Vous pouvez naviguer dans n’importe quelle exécution donnée et inspecter les données utilisées par chaque étape pour le dépannage. Logic Apps fournit également des modèles existants que vous pouvez modifier et sont bien adaptés pour les flux de travail d’entreprise complexes.

Pour en savoir plus, voir [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Suivant précédent](application-insights.md)
>[Next](event-grid.md)
