---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Choisir des plates-formes de calcul Azure pour les applications en conteneur
ms.date: 05/04/2018
ms.openlocfilehash: d91cd279402dc24beb5f766c06cb85ac8d74f482
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758827"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="4af8e-103">Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs</span><span class="sxs-lookup"><span data-stu-id="4af8e-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="4af8e-104">Comme vous l’avez remarqué après avoir lu les sections précédentes, Azure est un cloud ouverte qui offre plusieurs choix.</span><span class="sxs-lookup"><span data-stu-id="4af8e-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="4af8e-105">Vous pouvez utiliser la mieux adaptée à vos besoins, toutefois, il met également en évidence questions sur les produits et technologies que vous devez utiliser pour vos applications en conteneur.</span><span class="sxs-lookup"><span data-stu-id="4af8e-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="4af8e-106">Comme un *par défaut* recommandation, ce qui suit est le principal critère recommandé dans ce guide :</span><span class="sxs-lookup"><span data-stu-id="4af8e-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="4af8e-107">**Application monolithique unique :** Choisissez Azure App Service</span><span class="sxs-lookup"><span data-stu-id="4af8e-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="4af8e-108">**Application multiniveau :** Choisissez des orchestrateurs tels que Azure Kubernetes Service (AKS) ou App Service si vous avez un seul ou plusieurs services back-end</span><span class="sxs-lookup"><span data-stu-id="4af8e-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="4af8e-109">**Microservices de Linux :** Choisissez AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="4af8e-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="4af8e-110">**Microservices de Windows :** Choisissez Azure Web Apps for Containers</span><span class="sxs-lookup"><span data-stu-id="4af8e-110">**Windows microservices:** Choose Azure Web Apps for Containers</span></span>
- <span data-ttu-id="4af8e-111">**& Gestionnaires d’événements de fonctions sans serveur :** Choisissez Azure Functions</span><span class="sxs-lookup"><span data-stu-id="4af8e-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="4af8e-112">**Lots à grande échelle :** Choisissez Azure Batch</span><span class="sxs-lookup"><span data-stu-id="4af8e-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="4af8e-113">Toutefois, cette recommandation à entreprendre avec une pincée de salt, comme la sélection du produit varie selon les besoins spécifiques de votre application et de caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="4af8e-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="4af8e-114">Pas toutes les applications sont les mêmes, même lorsque initialement, il peut présenter des types similaires.</span><span class="sxs-lookup"><span data-stu-id="4af8e-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="4af8e-115">Après une analyse plus approfondie des besoins de l’application, le produit sélectionné peut être différent.</span><span class="sxs-lookup"><span data-stu-id="4af8e-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="4af8e-116">Mais, en tant que point de départ, il est judicieux d’avoir des recommandations initiales relatives à partir d’où vous pouvez commencer à évaluer et de test en fonction de certaine priorité.</span><span class="sxs-lookup"><span data-stu-id="4af8e-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="4af8e-117">Dans la figure suivante, vous pouvez voir une répartition des différents types d’applications et leurs Azure idéale scénarios d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="4af8e-117">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="4af8e-118">[Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="4af8e-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
