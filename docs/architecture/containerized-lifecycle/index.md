---
title: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
description: Bénéficiez d’une vue d’ensemble du processus de développement et de déploiement pour le développement et le déploiement d’applications en conteneur avec l’arrimeur et la plateforme et les outils Microsoft.
ms.date: 07/30/2020
ms.openlocfilehash: c506a3423ac4511f23452192e361e88dce6efec4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160695"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="811ad-103">Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft</span><span class="sxs-lookup"><span data-stu-id="811ad-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![Couverture de livre](./media/devops-book-cover-large-we.png)

<span data-ttu-id="811ad-105">**Edition v 3.1** -mise à jour vers ASP.net Core 3,1</span><span class="sxs-lookup"><span data-stu-id="811ad-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="811ad-106">Ce guide est une vue d’ensemble générale du développement et du déploiement d’applications ASP.NET Core en conteneur avec l’outil d’amarrage, à l’aide de la plateforme et des outils Microsoft.</span><span class="sxs-lookup"><span data-stu-id="811ad-106">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="811ad-107">Ce guide comprend une présentation générale d’Azure DevOps, pour l’implémentation de pipelines CI/CD, ainsi que Azure Container Registry (ACR) et les services Azure Kubernetes AKS pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="811ad-107">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="811ad-108">Pour obtenir des informations de bas niveau sur le développement, vous pouvez consulter le guide [.net microservices : architecture pour les applications .net en conteneur](../microservices/index.md) et l’application de référence [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="811ad-108">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](../microservices/index.md) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="811ad-109">Envoyez-nous vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="811ad-109">Send us your feedback!</span></span>

<span data-ttu-id="811ad-110">Nous avons rédigé ce guide pour vous aider à comprendre l’architecture des applications en conteneur et des microservices dans .NET.</span><span class="sxs-lookup"><span data-stu-id="811ad-110">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="811ad-111">Le guide et l’application de référence associée étant voués à évoluer, nous faisons bon accueil à vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="811ad-111">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="811ad-112">Si vous avez des commentaires sur la façon dont ce guide peut être amélioré, envoyez vos commentaires à l’adresse <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="811ad-112">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="811ad-113">Crédits</span><span class="sxs-lookup"><span data-stu-id="811ad-113">Credits</span></span>

<span data-ttu-id="811ad-114">Auteur :</span><span class="sxs-lookup"><span data-stu-id="811ad-114">Author:</span></span>

> <span data-ttu-id="811ad-115">**Cesar de la Torre**, chef de produit, équipe produit .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="811ad-115">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="811ad-116">Éditeur des acquisitions :</span><span class="sxs-lookup"><span data-stu-id="811ad-116">Acquisitions Editor:</span></span>

> <span data-ttu-id="811ad-117">**Janine Patrick**</span><span class="sxs-lookup"><span data-stu-id="811ad-117">**Janine Patrick**</span></span>

<span data-ttu-id="811ad-118">Éditeur de développement :</span><span class="sxs-lookup"><span data-stu-id="811ad-118">Developmental Editor:</span></span>

> <span data-ttu-id="811ad-119">**Bob Olivier**, solutions Professional chez Microsoft</span><span class="sxs-lookup"><span data-stu-id="811ad-119">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="811ad-120">**Octal publication, Inc.**</span><span class="sxs-lookup"><span data-stu-id="811ad-120">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="811ad-121">Production éditoriale :</span><span class="sxs-lookup"><span data-stu-id="811ad-121">Editorial Production:</span></span>

> [<span data-ttu-id="811ad-122">Dianne Olivier</span><span class="sxs-lookup"><span data-stu-id="811ad-122">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="811ad-123">**Octal publication, Inc.**</span><span class="sxs-lookup"><span data-stu-id="811ad-123">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="811ad-124">Copyeditor:</span><span class="sxs-lookup"><span data-stu-id="811ad-124">Copyeditor:</span></span>

> <span data-ttu-id="811ad-125">**Bob Olivier**, solutions Professional chez Microsoft</span><span class="sxs-lookup"><span data-stu-id="811ad-125">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="811ad-126">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="811ad-126">Participants and reviewers:</span></span>

> <span data-ttu-id="811ad-127">**Nish Anil**, responsable de programme senior, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="811ad-127">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="811ad-128">**Miguel Veloso**, ingénieur de développement logiciel chez des concepts simples</span><span class="sxs-lookup"><span data-stu-id="811ad-128">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="811ad-129">**Sumit Ghosh**, consultant principal chez Neudesic</span><span class="sxs-lookup"><span data-stu-id="811ad-129">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="811ad-130">Copyright</span><span class="sxs-lookup"><span data-stu-id="811ad-130">Copyright</span></span>

<span data-ttu-id="811ad-131">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="811ad-131">PUBLISHED BY</span></span>

<span data-ttu-id="811ad-132">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="811ad-132">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="811ad-133">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="811ad-133">A division of Microsoft Corporation</span></span>

<span data-ttu-id="811ad-134">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="811ad-134">One Microsoft Way</span></span>

<span data-ttu-id="811ad-135">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="811ad-135">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="811ad-136">Copyright &copy; 2020 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="811ad-136">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="811ad-137">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="811ad-137">All rights reserved.</span></span> <span data-ttu-id="811ad-138">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="811ad-138">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="811ad-139">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="811ad-139">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="811ad-140">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="811ad-140">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="811ad-141"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="811ad-141">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="811ad-142">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="811ad-142">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="811ad-143">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="811ad-143">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="811ad-144">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="811ad-144">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="811ad-145">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="811ad-145">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="811ad-146">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="811ad-146">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="811ad-147">Next</span><span class="sxs-lookup"><span data-stu-id="811ad-147">Next</span></span>](introduction-to-containers-and-docker.md)
