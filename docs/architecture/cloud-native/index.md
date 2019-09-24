---
title: Architecture des applications .NET natives Cloud pour Azure
description: Guide pour la création d’applications Cloud natives tirant parti de conteneurs, de microservices et de fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 67e235b051702308d2455b2501bfb59a4317635b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214168"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="18bba-103">Architecture des applications .NET natives Cloud pour Azure</span><span class="sxs-lookup"><span data-stu-id="18bba-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![image de couverture](./media/cover.png)

<span data-ttu-id="18bba-105">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="18bba-105">PUBLISHED BY</span></span>

<span data-ttu-id="18bba-106">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="18bba-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="18bba-107">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="18bba-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="18bba-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="18bba-108">One Microsoft Way</span></span>

<span data-ttu-id="18bba-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="18bba-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="18bba-110">Copyright © 2019 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="18bba-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="18bba-111">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="18bba-111">All rights reserved.</span></span> <span data-ttu-id="18bba-112">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="18bba-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="18bba-113">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="18bba-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="18bba-114">Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="18bba-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="18bba-115">Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs.</span><span class="sxs-lookup"><span data-stu-id="18bba-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="18bba-116">Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.</span><span class="sxs-lookup"><span data-stu-id="18bba-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="18bba-117">Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse https://www.microsoft.com sont des marques du groupe de sociétés Microsoft.</span><span class="sxs-lookup"><span data-stu-id="18bba-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="18bba-118">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="18bba-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="18bba-119">Le logo de Docker représentant une baleine est une marque déposée de Docker, Inc. Utilisé sous autorisation.</span><span class="sxs-lookup"><span data-stu-id="18bba-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="18bba-120">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="18bba-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="18bba-121">Extrait</span><span class="sxs-lookup"><span data-stu-id="18bba-121">Authors:</span></span>

> <span data-ttu-id="18bba-122">**Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="18bba-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="18bba-123">**Rob** -Guide-Microsoft-principal Cloud System Architect/IP architect- [RobVettor.com](https://robvettor.com)</span><span class="sxs-lookup"><span data-stu-id="18bba-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)</span></span>

<span data-ttu-id="18bba-124">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="18bba-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="18bba-125">**Cesar de la Torre**, responsable de programme principal, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18bba-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="18bba-126">**Nish Anil**, responsable de programme senior, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18bba-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="18bba-127">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="18bba-127">Editors:</span></span>

> <span data-ttu-id="18bba-128">**Maira Wenzel**, développeur de service de contenu, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18bba-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="18bba-129">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="18bba-129">Who should use this guide</span></span>

<span data-ttu-id="18bba-130">Le public concerné par ce guide est principalement les développeurs, les responsables du développement et les architectes qui souhaitent apprendre à créer des applications conçues pour le Cloud.</span><span class="sxs-lookup"><span data-stu-id="18bba-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="18bba-131">Un public secondaire est un décideur technique qui prévoit de choisir s’il faut créer ses applications à l’aide d’une approche Cloud native.</span><span class="sxs-lookup"><span data-stu-id="18bba-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="18bba-132">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="18bba-132">How you can use this guide</span></span>

<span data-ttu-id="18bba-133">Ce guide commence par définir le Cloud native et introduit une application de référence créée à l’aide de principes et de technologies Cloud natifs.</span><span class="sxs-lookup"><span data-stu-id="18bba-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="18bba-134">Au-delà de ces deux premiers chapitres, le reste du livre est divisé en chapitres spécifiques axés sur les sujets communs à la plupart des applications Cloud natives.</span><span class="sxs-lookup"><span data-stu-id="18bba-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="18bba-135">Vous pouvez accéder à l’un de ces chapitres pour en savoir plus sur les approches Cloud-natives pour :</span><span class="sxs-lookup"><span data-stu-id="18bba-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="18bba-136">Données et accès aux données</span><span class="sxs-lookup"><span data-stu-id="18bba-136">Data and data access</span></span>
- <span data-ttu-id="18bba-137">Modèles de communication</span><span class="sxs-lookup"><span data-stu-id="18bba-137">Communication patterns</span></span>
- <span data-ttu-id="18bba-138">Mise à l’échelle et évolutivité</span><span class="sxs-lookup"><span data-stu-id="18bba-138">Scaling and scalability</span></span>
- <span data-ttu-id="18bba-139">Résilience des applications</span><span class="sxs-lookup"><span data-stu-id="18bba-139">Application resiliency</span></span>
- <span data-ttu-id="18bba-140">Supervision et intégrité</span><span class="sxs-lookup"><span data-stu-id="18bba-140">Monitoring and health</span></span>
- <span data-ttu-id="18bba-141">Identité et sécurité</span><span class="sxs-lookup"><span data-stu-id="18bba-141">Identity and security</span></span>
- <span data-ttu-id="18bba-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="18bba-142">DevOps</span></span>

<span data-ttu-id="18bba-143">Ce guide est disponible au format PDF et en ligne.</span><span class="sxs-lookup"><span data-stu-id="18bba-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="18bba-144">N’hésitez pas à transmettre ce document ou des liens vers sa version en ligne à votre équipe afin de garantir une compréhension commune de ces sujets.</span><span class="sxs-lookup"><span data-stu-id="18bba-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="18bba-145">La plupart de ces rubriques tirent parti d’une compréhension cohérente des principes et des modèles sous-jacents, ainsi que des compromis impliqués dans les décisions relatives à ces sujets.</span><span class="sxs-lookup"><span data-stu-id="18bba-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="18bba-146">L’objectif de ce document est de fournir aux équipes et à leurs dirigeants les informations dont elles ont besoin pour prendre des décisions bien informées sur l’architecture, le développement et l’hébergement de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="18bba-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="18bba-147">Next</span><span class="sxs-lookup"><span data-stu-id="18bba-147">Next</span></span>](introduction.md)
