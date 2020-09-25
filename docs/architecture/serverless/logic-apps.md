---
title: Applications sans serveur Azure Logic Apps
description: Azure Logic Apps activer la création de flux de travail évolutifs automatisés qui intègrent des applications et des données dans les services Cloud et les systèmes locaux.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 11fdf5b5f176eb0d66eee6dde7638d3eae1e1f55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171843"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="947f8-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="947f8-103">Azure Logic Apps</span></span>

<span data-ttu-id="947f8-104">[Azure Logic Apps](/azure/logic-apps) fournit un moteur sans serveur pour créer des flux de travail automatisés pour intégrer des applications et des données entre les services Cloud et les systèmes locaux.</span><span class="sxs-lookup"><span data-stu-id="947f8-104">[Azure Logic Apps](/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="947f8-105">Vous générez des flux de travail à l’aide d’un concepteur visuel.</span><span class="sxs-lookup"><span data-stu-id="947f8-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="947f8-106">Vous pouvez déclencher des flux de travail basés sur des événements ou des minuteurs et tirer parti des connecteurs pour les applications d’intégration et faciliter la communication entre entreprises (B2B).</span><span class="sxs-lookup"><span data-stu-id="947f8-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="947f8-107">Logic Apps s’intègre parfaitement à Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="947f8-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Logo Azure Logic Apps](./media/logic-apps-logo.png)

<span data-ttu-id="947f8-109">Logic Apps pouvez faire plus que connecter simplement vos services Cloud (comme les fonctions) aux ressources cloud (telles que les files d’attente et les bases de données).</span><span class="sxs-lookup"><span data-stu-id="947f8-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="947f8-110">Vous pouvez également orchestrer des flux de travail locaux avec la passerelle locale.</span><span class="sxs-lookup"><span data-stu-id="947f8-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="947f8-111">Par exemple, vous pouvez utiliser l’application logique pour déclencher une procédure stockée SQL locale en réponse à un événement basé sur le Cloud ou à une logique conditionnelle dans votre flux de travail.</span><span class="sxs-lookup"><span data-stu-id="947f8-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="947f8-112">En savoir plus sur la [connexion aux sources de données locales avec la passerelle de données locale Azure](/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="947f8-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](/azure/analysis-services/analysis-services-gateway).</span></span>

![Architecture Logic Apps](./media/logic-apps-architecture.png)

<span data-ttu-id="947f8-114">Comme Azure Functions, vous démarrez les workflows d’application logique avec un déclencheur.</span><span class="sxs-lookup"><span data-stu-id="947f8-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="947f8-115">Vous pouvez choisir parmi de nombreux déclencheurs.</span><span class="sxs-lookup"><span data-stu-id="947f8-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="947f8-116">La capture suivante présente quelques-unes des centaines de centaines disponibles parmi les plus populaires.</span><span class="sxs-lookup"><span data-stu-id="947f8-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Déclencheurs Logic Apps](./media/logic-app-triggers.png)

<span data-ttu-id="947f8-118">Une fois l’application déclenchée, vous pouvez utiliser le concepteur visuel pour créer des étapes, des boucles, des conditions et des actions.</span><span class="sxs-lookup"><span data-stu-id="947f8-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="947f8-119">Toutes les données ingérées au cours d’une étape précédente sont disponibles pour être utilisées dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="947f8-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="947f8-120">Le flux de travail suivant charge les URL à partir d’une base de données CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="947f8-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="947f8-121">Il trouve ceux qui ont un hôte `t.co` , puis les recherche sur Twitter.</span><span class="sxs-lookup"><span data-stu-id="947f8-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="947f8-122">S’il trouve des tweets correspondants, il met à jour les documents avec les tweets associés en appelant une fonction.</span><span class="sxs-lookup"><span data-stu-id="947f8-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Flux de travail d’application logique](./media/logic-app-workflow.png)

<span data-ttu-id="947f8-124">Le tableau de bord Logic Apps affiche l’historique de l’exécution de vos workflows et indique si chaque exécution s’est terminée correctement.</span><span class="sxs-lookup"><span data-stu-id="947f8-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="947f8-125">Vous pouvez naviguer dans une exécution donnée et inspecter les données utilisées par chaque étape pour la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="947f8-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="947f8-126">Logic Apps fournit également des modèles existants que vous pouvez modifier et qui conviennent parfaitement aux flux de travail d’entreprise complexes.</span><span class="sxs-lookup"><span data-stu-id="947f8-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="947f8-127">Pour plus d’informations, consultez [Azure Logic Apps](/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="947f8-127">To learn more, see [Azure Logic Apps](/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="947f8-128">[Précédent](application-insights.md) 
> [Suivant](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="947f8-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
