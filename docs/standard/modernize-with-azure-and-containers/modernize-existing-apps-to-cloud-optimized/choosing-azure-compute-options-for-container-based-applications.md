---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Choisir des plates-formes de calcul Azure pour les applications en conteneur
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833856"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="97522-103">Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs</span><span class="sxs-lookup"><span data-stu-id="97522-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="97522-104">Comme vous l’avez remarqué après avoir lu les sections précédentes, Azure est un cloud ouverte qui offre plusieurs choix.</span><span class="sxs-lookup"><span data-stu-id="97522-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="97522-105">Vous pouvez utiliser la mieux adaptée à vos besoins, toutefois, il met également en évidence questions sur les produits et technologies que vous devez utiliser pour vos applications en conteneur.</span><span class="sxs-lookup"><span data-stu-id="97522-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="97522-106">Comme un *par défaut* recommandation, ce qui suit est le principal critère recommandé dans ce guide :</span><span class="sxs-lookup"><span data-stu-id="97522-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="97522-107">**Application monolithique unique :** Choisissez Azure App Service</span><span class="sxs-lookup"><span data-stu-id="97522-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="97522-108">**Application multiniveau :** Choisissez des orchestrateurs tels que Azure Kubernetes Service (AKS) ou App Service si vous avez un seul ou plusieurs services back-end</span><span class="sxs-lookup"><span data-stu-id="97522-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="97522-109">**Microservices :** Choisissez AKS ou Azure Web Apps for Containers</span><span class="sxs-lookup"><span data-stu-id="97522-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="97522-110">**& Gestionnaires d’événements de fonctions sans serveur :** Choisissez Azure Functions</span><span class="sxs-lookup"><span data-stu-id="97522-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="97522-111">**Lots à grande échelle :** Choisissez Azure Batch</span><span class="sxs-lookup"><span data-stu-id="97522-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="97522-112">Toutefois, cette recommandation à entreprendre avec une pincée de salt, comme la sélection du produit varie selon les besoins spécifiques de votre application et de caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="97522-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="97522-113">Pas toutes les applications sont les mêmes, même lorsque initialement, il peut présenter des types similaires.</span><span class="sxs-lookup"><span data-stu-id="97522-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="97522-114">Après une analyse plus approfondie des besoins de l’application, le produit sélectionné peut être différent.</span><span class="sxs-lookup"><span data-stu-id="97522-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="97522-115">Mais, en tant que point de départ, il est judicieux d’avoir des recommandations initiales relatives à partir d’où vous pouvez commencer à évaluer et de test en fonction de certaine priorité.</span><span class="sxs-lookup"><span data-stu-id="97522-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="97522-116">Dans la figure suivante, vous pouvez voir une répartition des différents types d’applications et leurs Azure idéale scénarios d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="97522-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="97522-117">[Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="97522-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
