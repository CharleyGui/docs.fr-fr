---
title: Architecture des applications .NET natives Cloud pour Azure
description: Guide pour la création d’applications Cloud natives tirant parti de conteneurs, de microservices et de fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 01/19/2021
ms.openlocfilehash: ad641517f9dc24aed9180cf6a092f4754739bceb
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506121"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="2fcb6-103">Architecture des applications .NET natives Cloud pour Azure</span><span class="sxs-lookup"><span data-stu-id="2fcb6-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![image de couverture](./media/cover.png)

<span data-ttu-id="2fcb6-105">**ÉDITION v 1.0.2**</span><span class="sxs-lookup"><span data-stu-id="2fcb6-105">**EDITION v1.0.2**</span></span>

<span data-ttu-id="2fcb6-106">Reportez-vous à [Journal des modifications](https://aka.ms/cn-ebook-changelog) pour les mises à jour de livres et les contributions de la communauté.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-106">Refer [changelog](https://aka.ms/cn-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="2fcb6-107">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="2fcb6-107">PUBLISHED BY</span></span>

<span data-ttu-id="2fcb6-108">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2fcb6-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="2fcb6-109">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2fcb6-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="2fcb6-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="2fcb6-110">One Microsoft Way</span></span>

<span data-ttu-id="2fcb6-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="2fcb6-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="2fcb6-112">Copyright &copy; 2021 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2fcb6-112">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="2fcb6-113">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-113">All rights reserved.</span></span> <span data-ttu-id="2fcb6-114">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="2fcb6-115">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="2fcb6-116">Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="2fcb6-117"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="2fcb6-118">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="2fcb6-119">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="2fcb6-120">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="2fcb6-121">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-121">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="2fcb6-122">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="2fcb6-123">Auteurs :</span><span class="sxs-lookup"><span data-stu-id="2fcb6-123">Authors:</span></span>

> <span data-ttu-id="2fcb6-124">**Rob** distribuateur, architecte du système Cloud principal/architecte IP- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="2fcb6-124">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="2fcb6-125">**Steve « ardalis » Smith**, architecte logiciel et formateur- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="2fcb6-125">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="2fcb6-126">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="2fcb6-126">Participants and Reviewers:</span></span>

> <span data-ttu-id="2fcb6-127">**Cesar de la Torre**, responsable de programme principal, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="2fcb6-127">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="2fcb6-128">**Nish Anile**, responsable de programme senior, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="2fcb6-128">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="2fcb6-129">**Jeremy Likness**, responsable de programme senior, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="2fcb6-129">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="2fcb6-130">**Cecil Phillip**, avocat du Cloud senior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="2fcb6-130">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>
>
> <span data-ttu-id="2fcb6-131">**Sumit Ghosh**, consultant principal chez Neudesic</span><span class="sxs-lookup"><span data-stu-id="2fcb6-131">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

<span data-ttu-id="2fcb6-132">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="2fcb6-132">Editors:</span></span>

> <span data-ttu-id="2fcb6-133">**Maira Wenzel**, responsable de programme, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="2fcb6-133">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="2fcb6-134">**David pins**, développeur de contenu senior, .net docs, Microsoft</span><span class="sxs-lookup"><span data-stu-id="2fcb6-134">**David Pine**, Senior Content Developer, .NET docs, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="2fcb6-135">Version</span><span class="sxs-lookup"><span data-stu-id="2fcb6-135">Version</span></span>

<span data-ttu-id="2fcb6-136">Ce guide a été écrit pour couvrir la version de **.net 5** , ainsi que de nombreuses mises à jour supplémentaires liées aux mêmes « vagues » de technologies (c’est-à-dire, Azure et des technologies tierces) qui coïncident avec la version .net 5.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-136">This guide has been written to cover **.NET 5** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET 5 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="2fcb6-137">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="2fcb6-137">Who should use this guide</span></span>

<span data-ttu-id="2fcb6-138">Le public concerné par ce guide est principalement les développeurs, les responsables du développement et les architectes qui souhaitent apprendre à créer des applications conçues pour le Cloud.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-138">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="2fcb6-139">Un public secondaire est un décideur technique qui prévoit de choisir s’il faut créer ses applications à l’aide d’une approche Cloud native.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-139">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="2fcb6-140">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="2fcb6-140">How you can use this guide</span></span>

<span data-ttu-id="2fcb6-141">Ce guide commence par définir le Cloud native et introduit une application de référence créée à l’aide de principes et de technologies Cloud natifs.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-141">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="2fcb6-142">Au-delà de ces deux premiers chapitres, le reste du livre est divisé en chapitres spécifiques axés sur les sujets communs à la plupart des applications Cloud natives.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-142">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="2fcb6-143">Vous pouvez accéder à l’un de ces chapitres pour en savoir plus sur les approches Cloud-natives pour :</span><span class="sxs-lookup"><span data-stu-id="2fcb6-143">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="2fcb6-144">Données et accès aux données</span><span class="sxs-lookup"><span data-stu-id="2fcb6-144">Data and data access</span></span>
- <span data-ttu-id="2fcb6-145">Modèles de communication</span><span class="sxs-lookup"><span data-stu-id="2fcb6-145">Communication patterns</span></span>
- <span data-ttu-id="2fcb6-146">Mise à l’échelle et évolutivité</span><span class="sxs-lookup"><span data-stu-id="2fcb6-146">Scaling and scalability</span></span>
- <span data-ttu-id="2fcb6-147">Résilience des applications</span><span class="sxs-lookup"><span data-stu-id="2fcb6-147">Application resiliency</span></span>
- <span data-ttu-id="2fcb6-148">Supervision et intégrité</span><span class="sxs-lookup"><span data-stu-id="2fcb6-148">Monitoring and health</span></span>
- <span data-ttu-id="2fcb6-149">Identité et sécurité</span><span class="sxs-lookup"><span data-stu-id="2fcb6-149">Identity and security</span></span>
- <span data-ttu-id="2fcb6-150">DevOps</span><span class="sxs-lookup"><span data-stu-id="2fcb6-150">DevOps</span></span>

<span data-ttu-id="2fcb6-151">Ce guide est disponible au format [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) et en ligne.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-151">This guide is available both in [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) form and online.</span></span> <span data-ttu-id="2fcb6-152">N’hésitez pas à transmettre ce document ou des liens vers sa version en ligne à votre équipe afin de garantir une compréhension commune de ces sujets.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-152">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="2fcb6-153">La plupart de ces rubriques tirent parti d’une compréhension cohérente des principes et des modèles sous-jacents, ainsi que des compromis impliqués dans les décisions relatives à ces sujets.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-153">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="2fcb6-154">L’objectif de ce document est de fournir aux équipes et à leurs dirigeants les informations dont elles ont besoin pour prendre des décisions bien informées sur l’architecture, le développement et l’hébergement de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="2fcb6-154">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="2fcb6-155">Envoyez votre feedback</span><span class="sxs-lookup"><span data-stu-id="2fcb6-155">Send your feedback</span></span>

<span data-ttu-id="2fcb6-156">Ce livre et les exemples associés sont en constante évolution. vos commentaires sont donc accueillis !</span><span class="sxs-lookup"><span data-stu-id="2fcb6-156">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="2fcb6-157">Si vous avez des commentaires sur la façon dont ce livre peut être amélioré, utilisez la section commentaires au bas de toute page reposant sur les [problèmes GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="2fcb6-157">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="2fcb6-158">Next</span><span class="sxs-lookup"><span data-stu-id="2fcb6-158">Next</span></span>](introduction.md)
