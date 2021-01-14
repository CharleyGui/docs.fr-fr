---
title: Choix entre .NET 5 et .NET Framework pour les conteneurs de l’ancrage
description: Architecture des microservices .NET pour les applications .NET en conteneur | Choix entre .NET 5 et .NET Framework pour les conteneurs de l’ancrage
ms.date: 01/13/2021
ms.openlocfilehash: 5c7ea1be02722fce7c5784afa89c18defbe4eeaf
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188645"
---
# <a name="choosing-between-net-and-net-framework-for-docker-containers"></a><span data-ttu-id="da3c8-103">Choix entre .NET et .NET Framework pour les conteneurs de l’ancrage</span><span class="sxs-lookup"><span data-stu-id="da3c8-103">Choosing Between .NET and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="da3c8-104">Il existe deux Frameworks pris en charge pour la création d’applications d’ancrage conteneur côté serveur avec .NET : [.NET Framework et .net 5](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="da3c8-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET 5](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="da3c8-105">Ils partagent de nombreux composants de plateforme .NET et vous permettent de partager du code entre les deux.</span><span class="sxs-lookup"><span data-stu-id="da3c8-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="da3c8-106">Toutefois, il existe des différences fondamentales entre eux et votre choix dépend de ce que vous souhaitez accomplir.</span><span class="sxs-lookup"><span data-stu-id="da3c8-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="da3c8-107">Cette section fournit des instructions pour éclairer le choix de chaque framework.</span><span class="sxs-lookup"><span data-stu-id="da3c8-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="da3c8-108">[Précédent](../container-docker-introduction/docker-containers-images-registries.md) 
> [Suivant](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="da3c8-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
