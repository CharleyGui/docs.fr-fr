---
title: Choix entre .NET Core et .NET Framework pour les conteneurs Docker
description: Architecture des microservices .NET pour les applications .NET en conteneur | Choix entre .NET Core et .NET Framework pour les conteneurs Docker
ms.date: 09/11/2018
ms.openlocfilehash: b01aaf25f4071e8e4a07905a12ec9dd0d89a738d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849275"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="fe3ec-103">Choix entre .NET Core et .NET Framework pour les conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="fe3ec-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="fe3ec-104">Il existe deux frameworks pris en charge pour générer des applications Docker en conteneur côté serveur avec .NET : [.NET Framework et .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="fe3ec-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="fe3ec-105">Ils partagent de nombreux composants de plateforme .NET et vous permettent de partager du code entre les deux.</span><span class="sxs-lookup"><span data-stu-id="fe3ec-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="fe3ec-106">Toutefois, il existe des différences fondamentales entre eux et votre choix dépend de ce que vous souhaitez accomplir.</span><span class="sxs-lookup"><span data-stu-id="fe3ec-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="fe3ec-107">Cette section fournit des instructions pour éclairer le choix de chaque framework.</span><span class="sxs-lookup"><span data-stu-id="fe3ec-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fe3ec-108">[Précédent](../container-docker-introduction/docker-containers-images-registries.md)
>[Suivant](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="fe3ec-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
