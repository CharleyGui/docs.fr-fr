---
title: ASP.NET Core gRPC pour les développeurs WCF-gRPC pour les développeurs WCF
description: À ÉCRIRE
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6a5b4f6d0b47a272f7a753e22bfd61b06202944a
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919375"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="ff102-103">gRPC ASP.NET Core pour les développeurs WCF</span><span class="sxs-lookup"><span data-stu-id="ff102-103">ASP.NET Core gRPC for WCF Developers</span></span>

![image de couverture](./media/cover.png)

<span data-ttu-id="ff102-105">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="ff102-105">PUBLISHED BY</span></span>

<span data-ttu-id="ff102-106">Division Développeur Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ff102-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="ff102-107">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="ff102-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="ff102-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="ff102-108">One Microsoft Way</span></span>

<span data-ttu-id="ff102-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="ff102-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="ff102-110">Copyright © 2019 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="ff102-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="ff102-111">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="ff102-111">All rights reserved.</span></span> <span data-ttu-id="ff102-112">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="ff102-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="ff102-113">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="ff102-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="ff102-114">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="ff102-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="ff102-115">Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs.</span><span class="sxs-lookup"><span data-stu-id="ff102-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="ff102-116">Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.</span><span class="sxs-lookup"><span data-stu-id="ff102-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="ff102-117">Microsoft et les marques commerciales mentionnées dans la page web « Marques » à l’adresse https://www.microsoft.com sont des marques du groupe de sociétés Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ff102-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="ff102-118">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="ff102-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="ff102-119">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="ff102-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="ff102-120">Auteur :</span><span class="sxs-lookup"><span data-stu-id="ff102-120">Author:</span></span>

> <span data-ttu-id="ff102-121">**Mark Rendle** -directeur technique – rédacteur [visuel](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="ff102-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="ff102-122">**Miranda Steiner** -auteur technique</span><span class="sxs-lookup"><span data-stu-id="ff102-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="ff102-123">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="ff102-123">Editors:</span></span>

> <span data-ttu-id="ff102-124">Développeur de contenu **Maira Wenzel** -SR-Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff102-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="ff102-125">Introduction</span><span class="sxs-lookup"><span data-stu-id="ff102-125">Introduction</span></span>

<span data-ttu-id="ff102-126">TODO</span><span class="sxs-lookup"><span data-stu-id="ff102-126">TODO</span></span>

## <a name="purpose"></a><span data-ttu-id="ff102-127">Fonction</span><span class="sxs-lookup"><span data-stu-id="ff102-127">Purpose</span></span>

<span data-ttu-id="ff102-128">TODO</span><span class="sxs-lookup"><span data-stu-id="ff102-128">TODO</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="ff102-129">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="ff102-129">Who should use this guide</span></span>

<span data-ttu-id="ff102-130">**METTRE À JOUR**</span><span class="sxs-lookup"><span data-stu-id="ff102-130">**UPDATE THIS**</span></span>

<span data-ttu-id="ff102-131">Ce guide est destiné aux développeurs WCF, aux responsables du développement et aux architectes qui souhaitent migrer des solutions WCF sur .NET Framework 4 et versions antérieures vers ASP.NET Core 3,0 à l’aide des services gRPC.</span><span class="sxs-lookup"><span data-stu-id="ff102-131">The audience for this guide is WCF developers, development leads, and architects who are interested in migrating WCF solutions on .NET Framework 4 and earlier to ASP.NET Core 3.0 using gRPC services.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="ff102-132">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="ff102-132">How you can use this guide</span></span>

<span data-ttu-id="ff102-133">**METTRE À JOUR**</span><span class="sxs-lookup"><span data-stu-id="ff102-133">**UPDATE THIS**</span></span>

<span data-ttu-id="ff102-134">Il s’agit d’une brève introduction à la création de services gRPC dans ASP.NET Core 3,0 avec une référence particulière à WCF en tant que plateforme analogue.</span><span class="sxs-lookup"><span data-stu-id="ff102-134">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="ff102-135">Il explique les principes de gRPC, en associant chaque concept aux fonctionnalités équivalentes de WCF, et fournit des conseils pour la migration d’une application WCF existante vers gRPC.</span><span class="sxs-lookup"><span data-stu-id="ff102-135">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="ff102-136">Elle est également utile pour les développeurs qui ont une expérience de WCF et qui cherchent à apprendre gRPC à créer de nouveaux services.</span><span class="sxs-lookup"><span data-stu-id="ff102-136">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="ff102-137">L’exemple d’application peut être utilisé comme modèle ou référence pour vos propres projets, et vous êtes libre de copier et réutiliser le code du livre ou de ses exemples.</span><span class="sxs-lookup"><span data-stu-id="ff102-137">The sample application can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="ff102-138">N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités.</span><span class="sxs-lookup"><span data-stu-id="ff102-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="ff102-139">Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.</span><span class="sxs-lookup"><span data-stu-id="ff102-139">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="ff102-140">Références</span><span class="sxs-lookup"><span data-stu-id="ff102-140">References</span></span>

- <span data-ttu-id="ff102-141">**site Web gRPC**</span><span class="sxs-lookup"><span data-stu-id="ff102-141">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="ff102-142">**Choix entre .NET Core et .NET Framework pour les applications serveur**</span><span class="sxs-lookup"><span data-stu-id="ff102-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="ff102-143">Suivant</span><span class="sxs-lookup"><span data-stu-id="ff102-143">Next</span></span>](introduction.md)
