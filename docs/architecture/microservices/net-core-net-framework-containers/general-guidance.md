---
title: Règle générale
description: Architecture de microservices .NET pour les applications .NET en conteneur | Recommandations générales
ms.date: 09/11/2018
ms.openlocfilehash: 6e63d7804abc1703f17378584d58d66a933022c7
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306875"
---
# <a name="general-guidance"></a><span data-ttu-id="43eff-103">Règle générale</span><span class="sxs-lookup"><span data-stu-id="43eff-103">General guidance</span></span>

<span data-ttu-id="43eff-104">Cette section indique brièvement dans quels cas choisir .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43eff-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="43eff-105">Vous trouverez des détails complémentaires sur ces choix dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="43eff-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="43eff-106">Utilisez .NET Core, avec des conteneurs Linux ou Windows, pour votre application serveur d’amarrage en conteneur lorsque :</span><span class="sxs-lookup"><span data-stu-id="43eff-106">Use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="43eff-107">vous avez des besoins multiplateformes ;</span><span class="sxs-lookup"><span data-stu-id="43eff-107">You have cross-platform needs.</span></span> <span data-ttu-id="43eff-108">Par exemple, vous souhaitez utiliser à la fois des conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="43eff-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="43eff-109">L’architecture de votre application est basée sur des microservices.</span><span class="sxs-lookup"><span data-stu-id="43eff-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="43eff-110">Vous avez besoin de démarrer les conteneurs rapidement et souhaitez un faible encombrement par conteneur pour profiter d’une meilleure densité ou davantage de conteneurs par unité matérielle afin de réduire les coûts.</span><span class="sxs-lookup"><span data-stu-id="43eff-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="43eff-111">En somme, quand il s’agit de créer des applications .NET en conteneur, vous devez envisager .NET Core comme le choix par défaut.</span><span class="sxs-lookup"><span data-stu-id="43eff-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="43eff-112">Il offre de nombreux avantages et correspond le mieux à la philosophie et au type de fonctionnement des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="43eff-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="43eff-113">L’autre avantage de .NET Core est lié au fait que vous pouvez exécuter différentes versions de .NET côte à côte pour les applications présentes sur une même machine.</span><span class="sxs-lookup"><span data-stu-id="43eff-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="43eff-114">Cet avantage est plus important pour les serveurs ou les machines virtuelles qui n’utilisent pas de conteneurs, car les conteneurs isolent les versions de .NET dont l’application a besoin.</span><span class="sxs-lookup"><span data-stu-id="43eff-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="43eff-115">(Du moment qu’elles sont compatibles avec le système d’exploitation sous-jacent.)</span><span class="sxs-lookup"><span data-stu-id="43eff-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="43eff-116">Utilisez .NET Framework pour votre application serveur d’amarrage en conteneur lorsque :</span><span class="sxs-lookup"><span data-stu-id="43eff-116">Use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="43eff-117">Votre application utilise actuellement le .NET Framework et présente de fortes dépendances vis-à-vis de Windows.</span><span class="sxs-lookup"><span data-stu-id="43eff-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="43eff-118">Vous avez besoin d’utiliser des API Windows qui ne sont pas prises en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43eff-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="43eff-119">Vous avez besoin d’utiliser des bibliothèques .NET ou des packages NuGet tiers qui ne sont pas disponibles pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43eff-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="43eff-120">Le fait d’utiliser le .NET Framework sur Docker peut améliorer vos expériences de déploiement en limitant les problèmes de déploiement.</span><span class="sxs-lookup"><span data-stu-id="43eff-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="43eff-121">Ce [scénario « lift-and-shift »](https://aka.ms/liftandshiftwithcontainersebook) est important pour la mise en conteneur d’applications existantes qui ont été développées à l’origine avec le .NET Framework classique, comme les applications Web Forms ASP.NET, les applications web MVC ou les services WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="43eff-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="43eff-122">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="43eff-122">Additional resources</span></span>

- <span data-ttu-id="43eff-123">**Livre électronique : moderniser les applications .NET Framework existantes avec des conteneurs Windows et Azure**</span><span class="sxs-lookup"><span data-stu-id="43eff-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    <https://aka.ms/liftandshiftwithcontainersebook>

- <span data-ttu-id="43eff-124">**Exemples d’application : Modernisation d’applications web ASP.NET héritées à l’aide de conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="43eff-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
><span data-ttu-id="43eff-125">[Précédent](index.md) 
> [Suivant](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="43eff-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
