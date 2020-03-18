---
title: Architecting Cloud Native .NET Applications pour Azure
description: Un guide pour la construction d’applications cloud-natives tirant parti des conteneurs, des microservices et des fonctionnalités sans serveur d’Azure.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 7f14a690d0153edc43f0ce7f4e91c9e9cd2c6858
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71696774"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="fcea3-103">Architecting Cloud Native .NET Applications pour Azure</span><span class="sxs-lookup"><span data-stu-id="fcea3-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![image de couverture](./media/cover.png)

<span data-ttu-id="fcea3-105">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="fcea3-105">PUBLISHED BY</span></span>

<span data-ttu-id="fcea3-106">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fcea3-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="fcea3-107">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="fcea3-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="fcea3-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="fcea3-108">One Microsoft Way</span></span>

<span data-ttu-id="fcea3-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="fcea3-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="fcea3-110">Copyright © 2019 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="fcea3-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="fcea3-111">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="fcea3-111">All rights reserved.</span></span> <span data-ttu-id="fcea3-112">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="fcea3-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="fcea3-113">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="fcea3-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="fcea3-114">Les points de vue, les opinions et les informations exprimés dans cet ouvrage, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="fcea3-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="fcea3-115"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="fcea3-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="fcea3-116">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="fcea3-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="fcea3-117">Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse https://www.microsoft.com sont des marques du groupe de sociétés Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fcea3-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="fcea3-118">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="fcea3-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="fcea3-119">Le logo de la baleine Docker est une marque déposée de Docker, Inc. Utilisée par permission.</span><span class="sxs-lookup"><span data-stu-id="fcea3-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="fcea3-120">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="fcea3-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="fcea3-121">Auteurs :</span><span class="sxs-lookup"><span data-stu-id="fcea3-121">Authors:</span></span>

> <span data-ttu-id="fcea3-122">**Steve « ardalis » Smith** - Architecte et formateur logiciel - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="fcea3-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="fcea3-123">**Rob Vettor** - Microsoft - Architecte principal du système Cloud/IP Architecte - [RobVettor.com](https://robvettor.com)</span><span class="sxs-lookup"><span data-stu-id="fcea3-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)</span></span>

<span data-ttu-id="fcea3-124">Participants et évaluateurs :</span><span class="sxs-lookup"><span data-stu-id="fcea3-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="fcea3-125">**Cesar De la Torre**, Gestionnaire principal de programme, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcea3-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="fcea3-126">**Nish Anil**, responsable de programme senior, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcea3-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="fcea3-127">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="fcea3-127">Editors:</span></span>

> <span data-ttu-id="fcea3-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="fcea3-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="fcea3-129">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="fcea3-129">Who should use this guide</span></span>

<span data-ttu-id="fcea3-130">Le public de ce guide est principalement des développeurs, des responsables du développement et des architectes qui sont intéressés à apprendre à construire des applications conçues pour le cloud.</span><span class="sxs-lookup"><span data-stu-id="fcea3-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="fcea3-131">Un public secondaire est celui des décideurs techniques qui prévoient choisir de construire ou non leurs applications en utilisant une approche cloud-native.</span><span class="sxs-lookup"><span data-stu-id="fcea3-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="fcea3-132">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="fcea3-132">How you can use this guide</span></span>

<span data-ttu-id="fcea3-133">Ce guide commence par définir le cloud natif et l’introduction d’une application de référence construite en utilisant des principes et des technologies cloud-native.</span><span class="sxs-lookup"><span data-stu-id="fcea3-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="fcea3-134">Au-delà de ces deux premiers chapitres, le reste du livre est divisé en chapitres spécifiques axés sur des sujets communs à la plupart des applications cloud-natives.</span><span class="sxs-lookup"><span data-stu-id="fcea3-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="fcea3-135">Vous pouvez sauter à l’un de ces chapitres pour en apprendre davantage sur les approches cloud-native à:</span><span class="sxs-lookup"><span data-stu-id="fcea3-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="fcea3-136">Accès aux données et aux données</span><span class="sxs-lookup"><span data-stu-id="fcea3-136">Data and data access</span></span>
- <span data-ttu-id="fcea3-137">Modèles de communication</span><span class="sxs-lookup"><span data-stu-id="fcea3-137">Communication patterns</span></span>
- <span data-ttu-id="fcea3-138">Mise à l’échelle et évolutivité</span><span class="sxs-lookup"><span data-stu-id="fcea3-138">Scaling and scalability</span></span>
- <span data-ttu-id="fcea3-139">Résilience de la demande</span><span class="sxs-lookup"><span data-stu-id="fcea3-139">Application resiliency</span></span>
- <span data-ttu-id="fcea3-140">Supervision et intégrité</span><span class="sxs-lookup"><span data-stu-id="fcea3-140">Monitoring and health</span></span>
- <span data-ttu-id="fcea3-141">Identité et sécurité</span><span class="sxs-lookup"><span data-stu-id="fcea3-141">Identity and security</span></span>
- <span data-ttu-id="fcea3-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="fcea3-142">DevOps</span></span>

<span data-ttu-id="fcea3-143">Ce guide est disponible en format PDF et en ligne.</span><span class="sxs-lookup"><span data-stu-id="fcea3-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="fcea3-144">N’hésitez pas à transmettre ce document ou des liens vers sa version en ligne à votre équipe pour vous aider à assurer une compréhension commune de ces sujets.</span><span class="sxs-lookup"><span data-stu-id="fcea3-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="fcea3-145">La plupart de ces sujets bénéficient d’une compréhension cohérente des principes et des modèles sous-jacents, ainsi que des compromis impliqués dans les décisions liées à ces sujets.</span><span class="sxs-lookup"><span data-stu-id="fcea3-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="fcea3-146">Notre objectif avec ce document est d’équiper les équipes et leurs dirigeants avec les informations dont ils ont besoin pour prendre des décisions bien informées pour l’architecture, le développement et l’hébergement de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="fcea3-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="fcea3-147">Suivant</span><span class="sxs-lookup"><span data-stu-id="fcea3-147">Next</span></span>](introduction.md)
