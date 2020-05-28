---
title: ASP.NET Core gRPC pour les développeurs WCF-gRPC pour les développeurs WCF
description: Introduction à la création de services gRPC dans ASP.NET Core 3,0 pour les développeurs WCF
ms.date: 09/02/2019
ms.openlocfilehash: 6e18ecfdb8fcbe20f71fd0a7c77076166451427a
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144355"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="86824-103">gRPC ASP.NET Core pour les développeurs WCF</span><span class="sxs-lookup"><span data-stu-id="86824-103">ASP.NET Core gRPC for WCF Developers</span></span>

![image de couverture](./media/cover.png)

<span data-ttu-id="86824-105">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="86824-105">PUBLISHED BY</span></span>

<span data-ttu-id="86824-106">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86824-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="86824-107">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="86824-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="86824-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="86824-108">One Microsoft Way</span></span>

<span data-ttu-id="86824-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="86824-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="86824-110">Copyright © 2019 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="86824-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="86824-111">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="86824-111">All rights reserved.</span></span> <span data-ttu-id="86824-112">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="86824-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="86824-113">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="86824-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="86824-114">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="86824-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="86824-115"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="86824-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="86824-116">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="86824-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="86824-117">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="86824-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="86824-118">Le logo de la baleine de l’arrimeur est une marque déposée de Dockr, Inc. utilisée par l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="86824-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="86824-119">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="86824-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="86824-120">Auteurs :</span><span class="sxs-lookup"><span data-stu-id="86824-120">Authors:</span></span>

> <span data-ttu-id="86824-121">**Mark Rendle** -directeur technique – rédacteur [visuel](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="86824-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="86824-122">**Miranda Steiner** -auteur technique</span><span class="sxs-lookup"><span data-stu-id="86824-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="86824-123">Éditeur :</span><span class="sxs-lookup"><span data-stu-id="86824-123">Editor:</span></span>

> <span data-ttu-id="86824-124">**Maira Wenzel** -SR. Content Developer-Microsoft</span><span class="sxs-lookup"><span data-stu-id="86824-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="86824-125">Introduction</span><span class="sxs-lookup"><span data-stu-id="86824-125">Introduction</span></span>

<span data-ttu-id="86824-126">gRPC est une infrastructure moderne pour la création de services en réseau et d’applications distribuées.</span><span class="sxs-lookup"><span data-stu-id="86824-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="86824-127">Imaginez les performances Windows Communication Foundation des liaisons NetTCP (WCF), combinées avec l’interopérabilité multiplateforme de SOAP.</span><span class="sxs-lookup"><span data-stu-id="86824-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="86824-128">gRPC s’appuie sur HTTP/2 et le protocole d’encodage de message Protobuf pour fournir une communication haute performance et à faible bande passante entre les applications et les services.</span><span class="sxs-lookup"><span data-stu-id="86824-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="86824-129">Il prend en charge la génération de code serveur et client dans les langages et plateformes de programmation les plus populaires, notamment .NET, Java, Python, node. js, Go et C++.</span><span class="sxs-lookup"><span data-stu-id="86824-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="86824-130">Avec la prise en charge de première classe de gRPC dans ASP.NET Core 3,0, en plus des outils et bibliothèques gRPC existants pour .NET 4. x, il s’agit d’une excellente alternative à WCF pour les équipes de développement souhaitant adopter .NET Core dans leurs organisations.</span><span class="sxs-lookup"><span data-stu-id="86824-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="86824-131">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="86824-131">Who should use this guide</span></span>

<span data-ttu-id="86824-132">Ce guide a été rédigé pour les développeurs qui travaillent dans .NET Framework ou .NET Core qui ont déjà utilisé WCF et qui cherchent à migrer leurs applications vers un environnement RPC moderne pour .NET Core 3,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="86824-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="86824-133">Plus généralement, si vous effectuez une mise à niveau ou si vous envisagez une mise à niveau vers .NET Core 3,0 et que vous souhaitez utiliser les outils intégrés gRPC, ce guide est également utile.</span><span class="sxs-lookup"><span data-stu-id="86824-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="86824-134">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="86824-134">How you can use this guide</span></span>

<span data-ttu-id="86824-135">Il s’agit d’une brève introduction à la création de services gRPC dans ASP.NET Core 3,0, avec une référence particulière à WCF en tant que plateforme analogue.</span><span class="sxs-lookup"><span data-stu-id="86824-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="86824-136">Il explique les principes de gRPC, en associant chaque concept aux fonctionnalités équivalentes de WCF, et fournit des conseils pour la migration d’une application WCF existante vers gRPC.</span><span class="sxs-lookup"><span data-stu-id="86824-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="86824-137">Elle est également utile pour les développeurs qui ont une expérience de WCF et qui cherchent à apprendre gRPC à créer de nouveaux services.</span><span class="sxs-lookup"><span data-stu-id="86824-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="86824-138">Vous pouvez utiliser les exemples d’applications comme modèle ou référence pour vos propres projets, et vous êtes libre de copier et réutiliser le code du livre ou de ses exemples.</span><span class="sxs-lookup"><span data-stu-id="86824-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="86824-139">N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités.</span><span class="sxs-lookup"><span data-stu-id="86824-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="86824-140">Faire en sorte que tout le monde travaille à partir d’un ensemble commun de termes et de principes sous-jacents permet d’assurer une application cohérente des modèles et des pratiques d’architecture.</span><span class="sxs-lookup"><span data-stu-id="86824-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="86824-141">Références</span><span class="sxs-lookup"><span data-stu-id="86824-141">References</span></span>

- <span data-ttu-id="86824-142">**site Web gRPC**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="86824-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="86824-143">**Choix entre .NET Core et .NET Framework pour les applications serveur**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="86824-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="86824-144">Suivant</span><span class="sxs-lookup"><span data-stu-id="86824-144">Next</span></span>](introduction.md)
