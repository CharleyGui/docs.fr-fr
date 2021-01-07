---
title: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
description: Bénéficiez d’une vue d’ensemble du processus de développement et de déploiement pour le développement et le déploiement d’applications en conteneur avec l’arrimeur et la plateforme et les outils Microsoft.
ms.date: 01/06/2021
ms.openlocfilehash: 94c277e349bacee9b9fc7b160043005dd4135958
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970113"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="e0b6d-103">Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft</span><span class="sxs-lookup"><span data-stu-id="e0b6d-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![Couverture de livre](./media/devops-book-cover-large-we.png)

<span data-ttu-id="e0b6d-105">**Édition v 5.0** -mise à jour vers ASP.net Core 5,0</span><span class="sxs-lookup"><span data-stu-id="e0b6d-105">**EDITION v5.0** - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="e0b6d-106">Reportez-vous à [Journal des modifications](https://aka.ms/DockerLifecycleEbookChangelog) pour les mises à jour de livres et les contributions de la communauté.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-106">Refer [changelog](https://aka.ms/DockerLifecycleEbookChangelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="e0b6d-107">Ce guide est une vue d’ensemble générale du développement et du déploiement d’applications ASP.NET Core en conteneur avec l’outil d’amarrage, à l’aide de la plateforme et des outils Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-107">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="e0b6d-108">Ce guide comprend une présentation générale d’Azure DevOps, pour l’implémentation de pipelines CI/CD, ainsi que Azure Container Registry (ACR) et les services Azure Kubernetes AKS pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-108">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="e0b6d-109">Pour obtenir des informations de bas niveau sur le développement, vous pouvez consulter le guide [.net microservices : architecture pour les applications .net en conteneur](../microservices/index.md) et l’application de référence [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="e0b6d-109">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](../microservices/index.md) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="e0b6d-110">Envoyez-nous vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="e0b6d-110">Send us your feedback!</span></span>

<span data-ttu-id="e0b6d-111">Nous avons rédigé ce guide pour vous aider à comprendre l’architecture des applications en conteneur et des microservices dans .NET.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-111">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="e0b6d-112">Le guide et l’application de référence associée étant voués à évoluer, nous faisons bon accueil à vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="e0b6d-112">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="e0b6d-113">Si vous avez des commentaires sur la façon dont ce guide peut être amélioré, envoyez vos commentaires à l’adresse <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="e0b6d-113">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="e0b6d-114">Crédits</span><span class="sxs-lookup"><span data-stu-id="e0b6d-114">Credits</span></span>

<span data-ttu-id="e0b6d-115">Auteur :</span><span class="sxs-lookup"><span data-stu-id="e0b6d-115">Author:</span></span>

> <span data-ttu-id="e0b6d-116">**Cesar de la Torre**, chef de produit, équipe produit .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-116">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="e0b6d-117">Éditeur des acquisitions :</span><span class="sxs-lookup"><span data-stu-id="e0b6d-117">Acquisitions Editor:</span></span>

> <span data-ttu-id="e0b6d-118">**Janine Patrick**</span><span class="sxs-lookup"><span data-stu-id="e0b6d-118">**Janine Patrick**</span></span>

<span data-ttu-id="e0b6d-119">Éditeur de développement :</span><span class="sxs-lookup"><span data-stu-id="e0b6d-119">Developmental Editor:</span></span>

> <span data-ttu-id="e0b6d-120">**Bob Olivier**, solutions Professional chez Microsoft</span><span class="sxs-lookup"><span data-stu-id="e0b6d-120">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="e0b6d-121">**Octal publication, Inc.**</span><span class="sxs-lookup"><span data-stu-id="e0b6d-121">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="e0b6d-122">Production éditoriale :</span><span class="sxs-lookup"><span data-stu-id="e0b6d-122">Editorial Production:</span></span>

> [<span data-ttu-id="e0b6d-123">Dianne Olivier</span><span class="sxs-lookup"><span data-stu-id="e0b6d-123">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="e0b6d-124">**Octal publication, Inc.**</span><span class="sxs-lookup"><span data-stu-id="e0b6d-124">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="e0b6d-125">Copyeditor:</span><span class="sxs-lookup"><span data-stu-id="e0b6d-125">Copyeditor:</span></span>

> <span data-ttu-id="e0b6d-126">**Bob Olivier**, solutions Professional chez Microsoft</span><span class="sxs-lookup"><span data-stu-id="e0b6d-126">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="e0b6d-127">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="e0b6d-127">Participants and reviewers:</span></span>

> <span data-ttu-id="e0b6d-128">**Nish Anil**, responsable de programme senior, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="e0b6d-128">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="e0b6d-129">**Miguel Veloso**, ingénieur de développement logiciel chez des concepts simples</span><span class="sxs-lookup"><span data-stu-id="e0b6d-129">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="e0b6d-130">**Sumit Ghosh**, consultant principal chez Neudesic</span><span class="sxs-lookup"><span data-stu-id="e0b6d-130">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="e0b6d-131">copyright</span><span class="sxs-lookup"><span data-stu-id="e0b6d-131">Copyright</span></span>

<span data-ttu-id="e0b6d-132">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="e0b6d-132">PUBLISHED BY</span></span>

<span data-ttu-id="e0b6d-133">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e0b6d-133">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="e0b6d-134">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e0b6d-134">A division of Microsoft Corporation</span></span>

<span data-ttu-id="e0b6d-135">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="e0b6d-135">One Microsoft Way</span></span>

<span data-ttu-id="e0b6d-136">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="e0b6d-136">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="e0b6d-137">Copyright &copy; 2021 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e0b6d-137">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="e0b6d-138">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-138">All rights reserved.</span></span> <span data-ttu-id="e0b6d-139">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-139">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="e0b6d-140">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-140">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="e0b6d-141">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-141">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="e0b6d-142"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-142">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="e0b6d-143">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-143">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="e0b6d-144">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-144">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="e0b6d-145">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-145">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="e0b6d-146">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-146">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="e0b6d-147">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="e0b6d-147">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="e0b6d-148">Next</span><span class="sxs-lookup"><span data-stu-id="e0b6d-148">Next</span></span>](introduction-to-containers-and-docker.md)
