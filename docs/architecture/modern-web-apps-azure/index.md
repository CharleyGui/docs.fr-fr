---
title: Architecturer des applications web modernes avec ASP.NET Core et Azure
description: Un guide qui fournit une aide de bout en bout sur la création d’applications web monolithiques avec ASP.NET Core et Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 6ae5de0381c8796faee74abd40f688214ab13211
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199961"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="92c03-103">Architecturer des applications web modernes avec ASP.NET Core et Azure</span><span class="sxs-lookup"><span data-stu-id="92c03-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Image de couverture du livre du Guide des applications Web modernes de l’architecte.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="92c03-105">**Edition v 3.1** -mise à jour vers ASP.net Core 3,1</span><span class="sxs-lookup"><span data-stu-id="92c03-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="92c03-106">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="92c03-106">PUBLISHED BY</span></span>

<span data-ttu-id="92c03-107">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="92c03-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="92c03-108">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="92c03-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="92c03-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="92c03-109">One Microsoft Way</span></span>

<span data-ttu-id="92c03-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="92c03-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="92c03-111">Copyright © 2020 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="92c03-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="92c03-112">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="92c03-112">All rights reserved.</span></span> <span data-ttu-id="92c03-113">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="92c03-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="92c03-114">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="92c03-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="92c03-115">Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="92c03-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="92c03-116"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="92c03-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="92c03-117">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="92c03-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="92c03-118">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur https://www.microsoft.com sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="92c03-118">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="92c03-119">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="92c03-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="92c03-120">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="92c03-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="92c03-121">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="92c03-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="92c03-122">Auteur :</span><span class="sxs-lookup"><span data-stu-id="92c03-122">Author:</span></span>

> <span data-ttu-id="92c03-123">**Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="92c03-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="92c03-124">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="92c03-124">Editors:</span></span>

> <span data-ttu-id="92c03-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="92c03-125">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="92c03-126">Introduction</span><span class="sxs-lookup"><span data-stu-id="92c03-126">Introduction</span></span>

<span data-ttu-id="92c03-127">.NET Core et ASP.NET Core offrent plusieurs avantages par rapport au développement .NET classique.</span><span class="sxs-lookup"><span data-stu-id="92c03-127">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="92c03-128">Il est recommandé d’utiliser .NET Core pour vos applications serveur si tout ou partie des éléments suivants sont importants pour la réussite de votre application :</span><span class="sxs-lookup"><span data-stu-id="92c03-128">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="92c03-129">Prise en charge multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="92c03-129">Cross-platform support.</span></span>

- <span data-ttu-id="92c03-130">Utilisation de microservices.</span><span class="sxs-lookup"><span data-stu-id="92c03-130">Use of microservices.</span></span>

- <span data-ttu-id="92c03-131">Utilisation de conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="92c03-131">Use of Docker containers.</span></span>

- <span data-ttu-id="92c03-132">Exigences en matière de hautes performances et de scalabilité.</span><span class="sxs-lookup"><span data-stu-id="92c03-132">High performance and scalability requirements.</span></span>

- <span data-ttu-id="92c03-133">Gestion côte à côte des versions de .NET par application sur le même serveur.</span><span class="sxs-lookup"><span data-stu-id="92c03-133">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="92c03-134">Les applications .NET classiques prennent en charge nombre de ces spécifications, mais ASP.NET Core et .NET Core ont été optimisés pour offrir une prise en charge améliorée des scénarios ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="92c03-134">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="92c03-135">De plus en plus d’organisations choisissent d’héberger leurs applications web dans le cloud en utilisant des services comme Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="92c03-135">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="92c03-136">Envisagez d’héberger votre application dans le cloud si les points suivants sont importants pour votre application ou votre organisation :</span><span class="sxs-lookup"><span data-stu-id="92c03-136">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="92c03-137">Réduction des investissements dans les coûts des centres de données (matériel, logiciel, espace, utilitaires, administration du serveur, etc.)</span><span class="sxs-lookup"><span data-stu-id="92c03-137">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="92c03-138">Tarification flexible (paiement basé sur l’utilisation et non pas pour une capacité inactive).</span><span class="sxs-lookup"><span data-stu-id="92c03-138">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="92c03-139">Fiabilité extrême.</span><span class="sxs-lookup"><span data-stu-id="92c03-139">Extreme reliability.</span></span>

- <span data-ttu-id="92c03-140">Mobilité accrue de l’application ; changement facile de l’endroit et de la façon dont votre application est déployée.</span><span class="sxs-lookup"><span data-stu-id="92c03-140">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="92c03-141">Capacité flexible ; montée ou descente en puissance en fonction des besoins réels.</span><span class="sxs-lookup"><span data-stu-id="92c03-141">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="92c03-142">La création d’applications web avec ASP.NET Core, hébergées dans Azure, offre de nombreux avantages concurrentiels par rapport aux alternatives classiques.</span><span class="sxs-lookup"><span data-stu-id="92c03-142">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="92c03-143">ASP.NET Core est optimisé pour les pratiques de développement d’applications web modernes et les scénarios d’hébergement cloud.</span><span class="sxs-lookup"><span data-stu-id="92c03-143">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="92c03-144">Dans ce guide, vous découvrez comment architecturer vos applications ASP.NET Core pour tirer le meilleur parti de ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="92c03-144">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="92c03-145">Objectif</span><span class="sxs-lookup"><span data-stu-id="92c03-145">Purpose</span></span>

<span data-ttu-id="92c03-146">Ce guide fournit des conseils de bout en bout sur la création d’applications Web *monolithiques* à l’aide d’ASP.net Core et d’Azure.</span><span class="sxs-lookup"><span data-stu-id="92c03-146">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="92c03-147">Dans ce contexte, « monolithiques » fait référence au fait que ces applications sont déployées comme une seule unité, pas comme une collection d’applications et de services qui interagissent.</span><span class="sxs-lookup"><span data-stu-id="92c03-147">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="92c03-148">Ce guide est complémentaire aux [_microservices .net. Architecture pour les applications .NET en conteneur_»](../microservices/index.md), qui se concentre sur l’ancrage, les microservices et le déploiement de conteneurs pour héberger des applications d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="92c03-148">This guide is complementary to ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md), which focuses more on Docker, microservices, and deployment of containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="92c03-149">Microservices .NET.</span><span class="sxs-lookup"><span data-stu-id="92c03-149">.NET Microservices.</span></span> <span data-ttu-id="92c03-150">Architecture pour les applications .NET en conteneur</span><span class="sxs-lookup"><span data-stu-id="92c03-150">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="92c03-151">**livre électronique**</span><span class="sxs-lookup"><span data-stu-id="92c03-151">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="92c03-152">**Exemple d’application**</span><span class="sxs-lookup"><span data-stu-id="92c03-152">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="92c03-153">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="92c03-153">Who should use this guide</span></span>

<span data-ttu-id="92c03-154">Le public visé par ce guide est principalement constitué de développeurs, de responsables du développement et d’architectes qui sont intéressés par la création d’applications web modernes avec des technologies et des services Microsoft dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="92c03-154">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="92c03-155">Il s’adresse aussi aux décideurs techniques qui connaissent déjà ASP.NET ou Azure, et qui recherchent des informations sur la pertinence d’un passage à ASP.NET Core pour des projets nouveaux ou existants.</span><span class="sxs-lookup"><span data-stu-id="92c03-155">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="92c03-156">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="92c03-156">How you can use this guide</span></span>

<span data-ttu-id="92c03-157">Ce guide a été condensé dans un document relativement petit qui se concentre sur la création d’applications Web avec des technologies .NET modernes et Azure.</span><span class="sxs-lookup"><span data-stu-id="92c03-157">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Azure.</span></span> <span data-ttu-id="92c03-158">Il peut ainsi être lu dans sa totalité, et permet de comprendre ces applications et les considérations techniques qui s’y rattachent.</span><span class="sxs-lookup"><span data-stu-id="92c03-158">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="92c03-159">Le guide, ainsi que son exemple d’application, peut aussi servir de point de départ ou de référence.</span><span class="sxs-lookup"><span data-stu-id="92c03-159">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="92c03-160">Utilisez l’exemple d’application associé comme modèle pour vos propres applications, ou pour voir comment organiser les composants de votre application.</span><span class="sxs-lookup"><span data-stu-id="92c03-160">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="92c03-161">Reportez-vous aux principes exposés dans le guide, à la couverture des options d’architecture et de technologie, et aux considérations sur les décisions à prendre quand vous évaluez ces choix pour votre propre application.</span><span class="sxs-lookup"><span data-stu-id="92c03-161">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="92c03-162">N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités.</span><span class="sxs-lookup"><span data-stu-id="92c03-162">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="92c03-163">Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.</span><span class="sxs-lookup"><span data-stu-id="92c03-163">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="92c03-164">References</span><span class="sxs-lookup"><span data-stu-id="92c03-164">References</span></span>

- <span data-ttu-id="92c03-165">**Choix entre .NET Core et .NET Framework pour les applications serveur**</span><span class="sxs-lookup"><span data-stu-id="92c03-165">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="92c03-166">Suivant</span><span class="sxs-lookup"><span data-stu-id="92c03-166">Next</span></span>](modern-web-applications-characteristics.md)
