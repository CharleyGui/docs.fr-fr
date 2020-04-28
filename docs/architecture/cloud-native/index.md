---
title: Architecture des applications .NET natives Cloud pour Azure
description: Guide pour la création d’applications Cloud natives tirant parti de conteneurs, de microservices et de fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 04/23/2020
ms.openlocfilehash: ebef97fb355cbf682b37ee441a19fbbfdd2d0dc3
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199818"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="d4e31-103">Architecture des applications .NET natives Cloud pour Azure</span><span class="sxs-lookup"><span data-stu-id="d4e31-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![image de couverture](./media/cover.png)

<span data-ttu-id="d4e31-105">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="d4e31-105">PUBLISHED BY</span></span>

<span data-ttu-id="d4e31-106">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d4e31-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="d4e31-107">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d4e31-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="d4e31-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="d4e31-108">One Microsoft Way</span></span>

<span data-ttu-id="d4e31-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="d4e31-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="d4e31-110">Copyright &copy; 2019 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d4e31-110">Copyright &copy; 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="d4e31-111">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="d4e31-111">All rights reserved.</span></span> <span data-ttu-id="d4e31-112">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="d4e31-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="d4e31-113">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="d4e31-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="d4e31-114">Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="d4e31-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="d4e31-115"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="d4e31-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="d4e31-116">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="d4e31-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="d4e31-117">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur https://www.microsoft.com sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d4e31-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="d4e31-118">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="d4e31-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="d4e31-119">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="d4e31-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="d4e31-120">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="d4e31-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="d4e31-121">Auteurs :</span><span class="sxs-lookup"><span data-stu-id="d4e31-121">Authors:</span></span>

> <span data-ttu-id="d4e31-122">**Rob**distribuateur, architecte du système Cloud principal/architecte IP- [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4e31-122">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="d4e31-123">**Steve « ardalis » Smith**, architecte logiciel et formateur- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="d4e31-123">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="d4e31-124">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="d4e31-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="d4e31-125">**Cesar de la Torre**, responsable de programme principal, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4e31-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="d4e31-126">**Nish Anile**, responsable de programme senior, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4e31-126">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="d4e31-127">**Jeremy ignorent**, responsable de programme senior, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4e31-127">**Jeremy Likeness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="d4e31-128">**Cecil Phillip**, avocat du Cloud senior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4e31-128">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="d4e31-129">En savoir plus sur eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="d4e31-129">Learn more about eShopOnContainers</span></span>

<span data-ttu-id="d4e31-130">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="d4e31-130">Editors:</span></span>

> <span data-ttu-id="d4e31-131">**Maira Wenzel**, responsable de programme, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4e31-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="d4e31-132">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="d4e31-132">Who should use this guide</span></span>

<span data-ttu-id="d4e31-133">Le public concerné par ce guide est principalement les développeurs, les responsables du développement et les architectes qui souhaitent apprendre à créer des applications conçues pour le Cloud.</span><span class="sxs-lookup"><span data-stu-id="d4e31-133">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="d4e31-134">Un public secondaire est un décideur technique qui prévoit de choisir s’il faut créer ses applications à l’aide d’une approche Cloud native.</span><span class="sxs-lookup"><span data-stu-id="d4e31-134">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="d4e31-135">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="d4e31-135">How you can use this guide</span></span>

<span data-ttu-id="d4e31-136">Ce guide commence par définir le Cloud native et introduit une application de référence créée à l’aide de principes et de technologies Cloud natifs.</span><span class="sxs-lookup"><span data-stu-id="d4e31-136">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="d4e31-137">Au-delà de ces deux premiers chapitres, le reste du livre est divisé en chapitres spécifiques axés sur les sujets communs à la plupart des applications Cloud natives.</span><span class="sxs-lookup"><span data-stu-id="d4e31-137">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="d4e31-138">Vous pouvez accéder à l’un de ces chapitres pour en savoir plus sur les approches Cloud-natives pour :</span><span class="sxs-lookup"><span data-stu-id="d4e31-138">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="d4e31-139">Données et accès aux données</span><span class="sxs-lookup"><span data-stu-id="d4e31-139">Data and data access</span></span>
- <span data-ttu-id="d4e31-140">Modèles de communication</span><span class="sxs-lookup"><span data-stu-id="d4e31-140">Communication patterns</span></span>
- <span data-ttu-id="d4e31-141">Mise à l’échelle et évolutivité</span><span class="sxs-lookup"><span data-stu-id="d4e31-141">Scaling and scalability</span></span>
- <span data-ttu-id="d4e31-142">Résilience des applications</span><span class="sxs-lookup"><span data-stu-id="d4e31-142">Application resiliency</span></span>
- <span data-ttu-id="d4e31-143">Supervision et intégrité</span><span class="sxs-lookup"><span data-stu-id="d4e31-143">Monitoring and health</span></span>
- <span data-ttu-id="d4e31-144">Identité et sécurité</span><span class="sxs-lookup"><span data-stu-id="d4e31-144">Identity and security</span></span>
- <span data-ttu-id="d4e31-145">DevOps</span><span class="sxs-lookup"><span data-stu-id="d4e31-145">DevOps</span></span>

<span data-ttu-id="d4e31-146">Ce guide est disponible au format PDF et en ligne.</span><span class="sxs-lookup"><span data-stu-id="d4e31-146">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="d4e31-147">N’hésitez pas à transmettre ce document ou des liens vers sa version en ligne à votre équipe afin de garantir une compréhension commune de ces sujets.</span><span class="sxs-lookup"><span data-stu-id="d4e31-147">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="d4e31-148">La plupart de ces rubriques tirent parti d’une compréhension cohérente des principes et des modèles sous-jacents, ainsi que des compromis impliqués dans les décisions relatives à ces sujets.</span><span class="sxs-lookup"><span data-stu-id="d4e31-148">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="d4e31-149">L’objectif de ce document est de fournir aux équipes et à leurs dirigeants les informations dont elles ont besoin pour prendre des décisions bien informées sur l’architecture, le développement et l’hébergement de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="d4e31-149">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d4e31-150">Suivant</span><span class="sxs-lookup"><span data-stu-id="d4e31-150">Next</span></span>](introduction.md)
