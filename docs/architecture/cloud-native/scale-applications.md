---
title: Mise à l’échelle des applications Cloud natives
description: Mise à l’échelle d’applications Cloud natives avec le service Azure Kubernetes et Azure Functions pour répondre à la demande des utilisateurs de manière rentable.
ms.date: 05/13/2020
ms.openlocfilehash: d425976eed248461a9c2e4fe03596f9f6dfd2eba
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613731"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="bdb3b-103">Mise à l’échelle des applications Cloud natives</span><span class="sxs-lookup"><span data-stu-id="bdb3b-103">Scaling cloud-native applications</span></span>

<span data-ttu-id="bdb3b-104">L’évolutivité est l’un des avantages les plus fréquents du passage à un environnement d’hébergement cloud.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="bdb3b-105">L’évolutivité, ou la possibilité pour une application d’accepter une charge utilisateur supplémentaire sans compromettre les performances de chaque utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-105">Scalability, or the ability for an application to accept additional user load without compromising performance for each user.</span></span> <span data-ttu-id="bdb3b-106">La plupart du temps, il est possible de fractionner une application en petites parties, chacune d’entre elles pouvant être affectée à toutes les ressources dont elles ont besoin.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-106">It's most often achieved by breaking up an application into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="bdb3b-107">Les fournisseurs de Cloud permettent une évolutivité massive à tout moment et partout dans le monde.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-107">Cloud vendors enable massive scalability anytime and anywhere in the world.</span></span>

 <span data-ttu-id="bdb3b-108">Dans ce chapitre, nous discutons des technologies qui permettent aux applications Cloud natives de se mettre à l’échelle pour répondre à la demande des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="bdb3b-108">In this chapter, we discuss technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="bdb3b-109">Ces technologies sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdb3b-109">These technologies include:</span></span>

- <span data-ttu-id="bdb3b-110">Containers</span><span class="sxs-lookup"><span data-stu-id="bdb3b-110">Containers</span></span>
- <span data-ttu-id="bdb3b-111">Orchestrators</span><span class="sxs-lookup"><span data-stu-id="bdb3b-111">Orchestrators</span></span>
- <span data-ttu-id="bdb3b-112">Informatique Serverless</span><span class="sxs-lookup"><span data-stu-id="bdb3b-112">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bdb3b-113">[Précédent](centralized-configuration.md) 
> [Suivant](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="bdb3b-113">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
