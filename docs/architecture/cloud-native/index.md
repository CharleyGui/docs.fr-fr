---
title: Architecture des applications .NET natives Cloud pour Azure
description: Guide pour la création d’applications Cloud natives tirant parti de conteneurs, de microservices et de fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 11/10/2020
ms.openlocfilehash: 673bfef27c3767f68b1c30d4383cee010ba377f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506647"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="fcd2d-103">Architecture des applications .NET natives Cloud pour Azure</span><span class="sxs-lookup"><span data-stu-id="fcd2d-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![image de couverture](./media/cover.png)

<span data-ttu-id="fcd2d-105">**ÉDITION v 1.0**</span><span class="sxs-lookup"><span data-stu-id="fcd2d-105">**EDITION v1.0**</span></span>

<span data-ttu-id="fcd2d-106">Reportez-vous à [Journal des modifications](https://aka.ms/cn-ebook-changelog) pour les mises à jour de livres et les contributions de la communauté.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-106">Refer [changelog](https://aka.ms/cn-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="fcd2d-107">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="fcd2d-107">PUBLISHED BY</span></span>

<span data-ttu-id="fcd2d-108">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fcd2d-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="fcd2d-109">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="fcd2d-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="fcd2d-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="fcd2d-110">One Microsoft Way</span></span>

<span data-ttu-id="fcd2d-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="fcd2d-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="fcd2d-112">Copyright &copy; 2020 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="fcd2d-112">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="fcd2d-113">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-113">All rights reserved.</span></span> <span data-ttu-id="fcd2d-114">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="fcd2d-115">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="fcd2d-116">Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="fcd2d-117"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="fcd2d-118">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="fcd2d-119">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="fcd2d-120">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="fcd2d-121">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-121">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="fcd2d-122">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="fcd2d-123">Auteurs :</span><span class="sxs-lookup"><span data-stu-id="fcd2d-123">Authors:</span></span>

> <span data-ttu-id="fcd2d-124">**Rob** distribuateur, architecte du système Cloud principal/architecte IP- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcd2d-124">**Rob Vettor** , Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="fcd2d-125">**Steve « ardalis » Smith** , architecte logiciel et formateur- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="fcd2d-125">**Steve "ardalis" Smith** , Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="fcd2d-126">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="fcd2d-126">Participants and Reviewers:</span></span>

> <span data-ttu-id="fcd2d-127">**Cesar de la Torre** , responsable de programme principal, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcd2d-127">**Cesar De la Torre** , Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="fcd2d-128">**Nish Anile** , responsable de programme senior, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcd2d-128">**Nish Anil** , Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="fcd2d-129">**Jeremy Likness** , responsable de programme senior, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcd2d-129">**Jeremy Likness** , Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="fcd2d-130">**Cecil Phillip** , avocat du Cloud senior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcd2d-130">**Cecil Phillip** , Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="fcd2d-131">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="fcd2d-131">Editors:</span></span>

> <span data-ttu-id="fcd2d-132">**Maira Wenzel** , responsable de programme, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcd2d-132">**Maira Wenzel** , Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="fcd2d-133">Version</span><span class="sxs-lookup"><span data-stu-id="fcd2d-133">Version</span></span>

<span data-ttu-id="fcd2d-134">Ce guide a été écrit de façon à couvrir la version **3,1 de .net Core** , ainsi que de nombreuses mises à jour supplémentaires liées aux mêmes « vagues » de technologies (c’est-à-dire, Azure et des technologies tierces) qui coïncident avec la version 3,1 de .net core.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-134">This guide has been written to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="fcd2d-135">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="fcd2d-135">Who should use this guide</span></span>

<span data-ttu-id="fcd2d-136">Le public concerné par ce guide est principalement les développeurs, les responsables du développement et les architectes qui souhaitent apprendre à créer des applications conçues pour le Cloud.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-136">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="fcd2d-137">Un public secondaire est un décideur technique qui prévoit de choisir s’il faut créer ses applications à l’aide d’une approche Cloud native.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-137">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="fcd2d-138">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="fcd2d-138">How you can use this guide</span></span>

<span data-ttu-id="fcd2d-139">Ce guide commence par définir le Cloud native et introduit une application de référence créée à l’aide de principes et de technologies Cloud natifs.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-139">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="fcd2d-140">Au-delà de ces deux premiers chapitres, le reste du livre est divisé en chapitres spécifiques axés sur les sujets communs à la plupart des applications Cloud natives.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-140">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="fcd2d-141">Vous pouvez accéder à l’un de ces chapitres pour en savoir plus sur les approches Cloud-natives pour :</span><span class="sxs-lookup"><span data-stu-id="fcd2d-141">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="fcd2d-142">Données et accès aux données</span><span class="sxs-lookup"><span data-stu-id="fcd2d-142">Data and data access</span></span>
- <span data-ttu-id="fcd2d-143">Modèles de communication</span><span class="sxs-lookup"><span data-stu-id="fcd2d-143">Communication patterns</span></span>
- <span data-ttu-id="fcd2d-144">Mise à l’échelle et évolutivité</span><span class="sxs-lookup"><span data-stu-id="fcd2d-144">Scaling and scalability</span></span>
- <span data-ttu-id="fcd2d-145">Résilience des applications</span><span class="sxs-lookup"><span data-stu-id="fcd2d-145">Application resiliency</span></span>
- <span data-ttu-id="fcd2d-146">Supervision et intégrité</span><span class="sxs-lookup"><span data-stu-id="fcd2d-146">Monitoring and health</span></span>
- <span data-ttu-id="fcd2d-147">Identité et sécurité</span><span class="sxs-lookup"><span data-stu-id="fcd2d-147">Identity and security</span></span>
- <span data-ttu-id="fcd2d-148">DevOps</span><span class="sxs-lookup"><span data-stu-id="fcd2d-148">DevOps</span></span>

<span data-ttu-id="fcd2d-149">Ce guide est disponible au format [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) et en ligne.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-149">This guide is available both in [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) form and online.</span></span> <span data-ttu-id="fcd2d-150">N’hésitez pas à transmettre ce document ou des liens vers sa version en ligne à votre équipe afin de garantir une compréhension commune de ces sujets.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-150">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="fcd2d-151">La plupart de ces rubriques tirent parti d’une compréhension cohérente des principes et des modèles sous-jacents, ainsi que des compromis impliqués dans les décisions relatives à ces sujets.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-151">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="fcd2d-152">L’objectif de ce document est de fournir aux équipes et à leurs dirigeants les informations dont elles ont besoin pour prendre des décisions bien informées sur l’architecture, le développement et l’hébergement de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="fcd2d-152">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="fcd2d-153">Envoyez votre feedback</span><span class="sxs-lookup"><span data-stu-id="fcd2d-153">Send your feedback</span></span>

<span data-ttu-id="fcd2d-154">Ce livre et les exemples associés sont en constante évolution. vos commentaires sont donc accueillis !</span><span class="sxs-lookup"><span data-stu-id="fcd2d-154">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="fcd2d-155">Si vous avez des commentaires sur la façon dont ce livre peut être amélioré, utilisez la section commentaires au bas de toute page reposant sur les [problèmes GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="fcd2d-155">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="fcd2d-156">Next</span><span class="sxs-lookup"><span data-stu-id="fcd2d-156">Next</span></span>](introduction.md)
