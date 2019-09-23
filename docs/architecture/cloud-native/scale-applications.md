---
title: Mise à l’échelle des applications Cloud natives
description: Mise à l’échelle d’applications Cloud natives avec le service Azure Kubernetes et Azure Functions pour répondre à la demande des utilisateurs de manière rentable.
ms.date: 09/23/2019
ms.openlocfilehash: 5f4aac5804c5498c331787083c943a6ea1b69748
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184826"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="00d3c-103">Mise à l’échelle des applications Cloud natives</span><span class="sxs-lookup"><span data-stu-id="00d3c-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="00d3c-104">L’évolutivité est l’un des avantages les plus fréquents du passage à un environnement d’hébergement cloud.</span><span class="sxs-lookup"><span data-stu-id="00d3c-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="00d3c-105">L’évolutivité, ou la possibilité pour une application d’accepter une charge utilisateur supplémentaire sans dégrader les performances de chaque utilisateur, est le plus souvent obtenue en scindant les applications en petites parties qui peuvent chacune avoir les ressources requises.</span><span class="sxs-lookup"><span data-stu-id="00d3c-105">Scalability, or the ability for an application to accept additional user load without unduly degrading performance for each user, is most often achieved by breaking up applications into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="00d3c-106">Dans ce chapitre, nous présentons les technologies qui permettent aux applications Cloud natives de se mettre à l’échelle pour répondre à la demande des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="00d3c-106">In this chapter, we introduce the technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="00d3c-107">Ces technologies sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="00d3c-107">These technologies include:</span></span>

- <span data-ttu-id="00d3c-108">Conteneurs</span><span class="sxs-lookup"><span data-stu-id="00d3c-108">Containers</span></span>
- <span data-ttu-id="00d3c-109">Orchestrateurs</span><span class="sxs-lookup"><span data-stu-id="00d3c-109">Orchestrators</span></span>
- <span data-ttu-id="00d3c-110">Informatique sans serveur</span><span class="sxs-lookup"><span data-stu-id="00d3c-110">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="00d3c-111">[Précédent](centralized-configuration.md)
>[Suivant](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="00d3c-111">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
