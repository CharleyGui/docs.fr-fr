---
title: Architecturer des applications web modernes avec ASP.NET Core et Azure
description: Un guide qui fournit une aide de bout en bout sur la création d’applications web monolithiques avec ASP.NET Core et Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 936a068507116033ad178f26e77945f30f70387e
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507191"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="7a65a-103">Architecturer des applications web modernes avec ASP.NET Core et Azure</span><span class="sxs-lookup"><span data-stu-id="7a65a-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Image de couverture du livre du Guide des applications Web modernes de l’architecte.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="7a65a-105">**Edition v 3.1** -mise à jour vers ASP.net Core 3,1</span><span class="sxs-lookup"><span data-stu-id="7a65a-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="7a65a-106">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="7a65a-106">PUBLISHED BY</span></span>

<span data-ttu-id="7a65a-107">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a65a-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="7a65a-108">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="7a65a-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="7a65a-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="7a65a-109">One Microsoft Way</span></span>

<span data-ttu-id="7a65a-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="7a65a-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="7a65a-111">Copyright © 2020 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="7a65a-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="7a65a-112">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="7a65a-112">All rights reserved.</span></span> <span data-ttu-id="7a65a-113">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="7a65a-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="7a65a-114">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="7a65a-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="7a65a-115">Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="7a65a-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="7a65a-116"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="7a65a-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="7a65a-117">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="7a65a-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="7a65a-118">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur https://www.microsoft.com sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7a65a-118">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="7a65a-119">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="7a65a-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="7a65a-120">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="7a65a-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="7a65a-121">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="7a65a-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="7a65a-122">Auteur :</span><span class="sxs-lookup"><span data-stu-id="7a65a-122">Author:</span></span>

> <span data-ttu-id="7a65a-123">**Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="7a65a-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="7a65a-124">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="7a65a-124">Editors:</span></span>

> <span data-ttu-id="7a65a-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="7a65a-125">**Maira Wenzel**</span></span>

## <a name="action-links"></a><span data-ttu-id="7a65a-126">Liens d'action</span><span class="sxs-lookup"><span data-stu-id="7a65a-126">Action links</span></span>

- <span data-ttu-id="7a65a-127">Ce livre électronique est également disponible au [Téléchargement](https://aka.ms/webappebook) au format PDF (version anglaise uniquement).</span><span class="sxs-lookup"><span data-stu-id="7a65a-127">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/webappebook)</span></span>

- <span data-ttu-id="7a65a-128">Cloner/Dupliquer l’application [de référence eShopOnWeb sur GitHub](https://github.com/dotnet-architecture/eShopOnWeb)</span><span class="sxs-lookup"><span data-stu-id="7a65a-128">Clone/Fork the reference application [eShopOnWeb on GitHub](https://github.com/dotnet-architecture/eShopOnWeb)</span></span>

## <a name="introduction"></a><span data-ttu-id="7a65a-129">Introduction</span><span class="sxs-lookup"><span data-stu-id="7a65a-129">Introduction</span></span>

<span data-ttu-id="7a65a-130">.NET Core et ASP.NET Core offrent plusieurs avantages par rapport au développement .NET classique.</span><span class="sxs-lookup"><span data-stu-id="7a65a-130">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="7a65a-131">Il est recommandé d’utiliser .NET Core pour vos applications serveur si tout ou partie des éléments suivants sont importants pour la réussite de votre application :</span><span class="sxs-lookup"><span data-stu-id="7a65a-131">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="7a65a-132">Prise en charge multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="7a65a-132">Cross-platform support.</span></span>

- <span data-ttu-id="7a65a-133">Utilisation de microservices.</span><span class="sxs-lookup"><span data-stu-id="7a65a-133">Use of microservices.</span></span>

- <span data-ttu-id="7a65a-134">Utilisation de conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="7a65a-134">Use of Docker containers.</span></span>

- <span data-ttu-id="7a65a-135">Exigences en matière de hautes performances et de scalabilité.</span><span class="sxs-lookup"><span data-stu-id="7a65a-135">High performance and scalability requirements.</span></span>

- <span data-ttu-id="7a65a-136">Gestion côte à côte des versions de .NET par application sur le même serveur.</span><span class="sxs-lookup"><span data-stu-id="7a65a-136">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="7a65a-137">Les applications .NET classiques prennent en charge nombre de ces spécifications, mais ASP.NET Core et .NET Core ont été optimisés pour offrir une prise en charge améliorée des scénarios ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7a65a-137">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="7a65a-138">De plus en plus d’organisations choisissent d’héberger leurs applications web dans le cloud en utilisant des services comme Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="7a65a-138">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="7a65a-139">Envisagez d’héberger votre application dans le cloud si les points suivants sont importants pour votre application ou votre organisation :</span><span class="sxs-lookup"><span data-stu-id="7a65a-139">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="7a65a-140">Réduction des investissements dans les coûts des centres de données (matériel, logiciel, espace, utilitaires, administration du serveur, etc.)</span><span class="sxs-lookup"><span data-stu-id="7a65a-140">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="7a65a-141">Tarification flexible (paiement basé sur l’utilisation et non pas pour une capacité inactive).</span><span class="sxs-lookup"><span data-stu-id="7a65a-141">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="7a65a-142">Fiabilité extrême.</span><span class="sxs-lookup"><span data-stu-id="7a65a-142">Extreme reliability.</span></span>

- <span data-ttu-id="7a65a-143">Mobilité accrue de l’application ; changement facile de l’endroit et de la façon dont votre application est déployée.</span><span class="sxs-lookup"><span data-stu-id="7a65a-143">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="7a65a-144">Capacité flexible ; montée ou descente en puissance en fonction des besoins réels.</span><span class="sxs-lookup"><span data-stu-id="7a65a-144">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="7a65a-145">La création d’applications web avec ASP.NET Core, hébergées dans Azure, offre de nombreux avantages concurrentiels par rapport aux alternatives classiques.</span><span class="sxs-lookup"><span data-stu-id="7a65a-145">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="7a65a-146">ASP.NET Core est optimisé pour les pratiques de développement d’applications web modernes et les scénarios d’hébergement cloud.</span><span class="sxs-lookup"><span data-stu-id="7a65a-146">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="7a65a-147">Dans ce guide, vous découvrez comment architecturer vos applications ASP.NET Core pour tirer le meilleur parti de ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="7a65a-147">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="7a65a-148">Objectif</span><span class="sxs-lookup"><span data-stu-id="7a65a-148">Purpose</span></span>

<span data-ttu-id="7a65a-149">Ce guide fournit des conseils de bout en bout sur la création d’applications Web *monolithiques* à l’aide d’ASP.net Core et d’Azure.</span><span class="sxs-lookup"><span data-stu-id="7a65a-149">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="7a65a-150">Dans ce contexte, « monolithiques » fait référence au fait que ces applications sont déployées comme une seule unité, pas comme une collection d’applications et de services qui interagissent.</span><span class="sxs-lookup"><span data-stu-id="7a65a-150">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="7a65a-151">Ce guide est complémentaire aux [_microservices .net. Architecture pour les applications .NET en conteneur_»](../microservices/index.md), qui se concentre sur l’ancrage, les microservices et le déploiement de conteneurs pour héberger des applications d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="7a65a-151">This guide is complementary to ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md), which focuses more on Docker, microservices, and deployment of containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="7a65a-152">Microservices .NET.</span><span class="sxs-lookup"><span data-stu-id="7a65a-152">.NET Microservices.</span></span> <span data-ttu-id="7a65a-153">Architecture pour les applications .NET en conteneur</span><span class="sxs-lookup"><span data-stu-id="7a65a-153">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="7a65a-154">**livre électronique**</span><span class="sxs-lookup"><span data-stu-id="7a65a-154">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="7a65a-155">**Exemple d’application**</span><span class="sxs-lookup"><span data-stu-id="7a65a-155">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="7a65a-156">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="7a65a-156">Who should use this guide</span></span>

<span data-ttu-id="7a65a-157">Le public visé par ce guide est principalement constitué de développeurs, de responsables du développement et d’architectes qui sont intéressés par la création d’applications web modernes avec des technologies et des services Microsoft dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="7a65a-157">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="7a65a-158">Il s’adresse aussi aux décideurs techniques qui connaissent déjà ASP.NET ou Azure, et qui recherchent des informations sur la pertinence d’un passage à ASP.NET Core pour des projets nouveaux ou existants.</span><span class="sxs-lookup"><span data-stu-id="7a65a-158">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="7a65a-159">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="7a65a-159">How you can use this guide</span></span>

<span data-ttu-id="7a65a-160">Ce guide a été condensé dans un document relativement petit qui se concentre sur la création d’applications Web avec des technologies .NET modernes et Azure.</span><span class="sxs-lookup"><span data-stu-id="7a65a-160">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Azure.</span></span> <span data-ttu-id="7a65a-161">Il peut ainsi être lu dans sa totalité, et permet de comprendre ces applications et les considérations techniques qui s’y rattachent.</span><span class="sxs-lookup"><span data-stu-id="7a65a-161">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="7a65a-162">Le guide, ainsi que son exemple d’application, peut aussi servir de point de départ ou de référence.</span><span class="sxs-lookup"><span data-stu-id="7a65a-162">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="7a65a-163">Utilisez l’exemple d’application associé comme modèle pour vos propres applications, ou pour voir comment organiser les composants de votre application.</span><span class="sxs-lookup"><span data-stu-id="7a65a-163">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="7a65a-164">Reportez-vous aux principes exposés dans le guide, à la couverture des options d’architecture et de technologie, et aux considérations sur les décisions à prendre quand vous évaluez ces choix pour votre propre application.</span><span class="sxs-lookup"><span data-stu-id="7a65a-164">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="7a65a-165">N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités.</span><span class="sxs-lookup"><span data-stu-id="7a65a-165">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="7a65a-166">Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.</span><span class="sxs-lookup"><span data-stu-id="7a65a-166">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="7a65a-167">References</span><span class="sxs-lookup"><span data-stu-id="7a65a-167">References</span></span>

- <span data-ttu-id="7a65a-168">**Choix entre .NET Core et .NET Framework pour les applications serveur**</span><span class="sxs-lookup"><span data-stu-id="7a65a-168">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="7a65a-169">Suivant</span><span class="sxs-lookup"><span data-stu-id="7a65a-169">Next</span></span>](modern-web-applications-characteristics.md)
