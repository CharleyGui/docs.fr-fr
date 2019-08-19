---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Choix de plateformes de calcul Azure pour les applications basées sur des conteneurs
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578342"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="26df9-103">Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs</span><span class="sxs-lookup"><span data-stu-id="26df9-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="26df9-104">Comme vous l’avez remarqué après avoir lu les sections précédentes, Azure est un Cloud ouvert qui offre plusieurs choix.</span><span class="sxs-lookup"><span data-stu-id="26df9-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="26df9-105">Vous pouvez utiliser la solution la mieux adaptée à vos besoins. Toutefois, elle présente également des questions sur le produit ou la technologie que vous devez utiliser pour vos applications en conteneur.</span><span class="sxs-lookup"><span data-stu-id="26df9-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="26df9-106">En guise de recommandation *par défaut* , les critères principaux recommandés dans ce guide sont les suivants:</span><span class="sxs-lookup"><span data-stu-id="26df9-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="26df9-107">**Application monolithique unique:** Choisir Azure App Service</span><span class="sxs-lookup"><span data-stu-id="26df9-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="26df9-108">**Application multiniveau:** Choisissez des orchestrateurs tels que le service Azure Kubernetes (AKS) ou App Service si vous disposez d’un seul ou de plusieurs services principaux</span><span class="sxs-lookup"><span data-stu-id="26df9-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="26df9-109">**Microservices** Choisir AKS ou Azure Web Apps pour les conteneurs</span><span class="sxs-lookup"><span data-stu-id="26df9-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="26df9-110">**Fonctions sans serveur & gestionnaires d’événements:** Choisir Azure Functions</span><span class="sxs-lookup"><span data-stu-id="26df9-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="26df9-111">**Lot à grande échelle:** Choisir Azure Batch</span><span class="sxs-lookup"><span data-stu-id="26df9-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="26df9-112">Toutefois, cette recommandation doit être prise avec un pincement Salt, car la sélection du produit dépend des besoins et caractéristiques de votre application spécifique.</span><span class="sxs-lookup"><span data-stu-id="26df9-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="26df9-113">Toutes les applications ne sont pas les mêmes, même si elles peuvent sembler des types similaires.</span><span class="sxs-lookup"><span data-stu-id="26df9-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="26df9-114">Après une analyse plus poussée des besoins de l’application, le produit sélectionné peut être différent.</span><span class="sxs-lookup"><span data-stu-id="26df9-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="26df9-115">Mais, comme point de départ, il est judicieux d’avoir des conseils initiaux à partir desquels vous pouvez commencer l’évaluation et le test en fonction de certaines priorités.</span><span class="sxs-lookup"><span data-stu-id="26df9-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="26df9-116">Dans la figure suivante, vous pouvez voir une répartition de différents types d’applications et de leurs scénarios d’hébergement Azure idéaux.</span><span class="sxs-lookup"><span data-stu-id="26df9-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="26df9-117">[Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="26df9-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
