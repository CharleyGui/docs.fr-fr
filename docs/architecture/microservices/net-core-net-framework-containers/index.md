---
title: Choix entre .NET Core et .NET Framework pour les conteneurs Docker
description: Architecture des microservices .NET pour les applications .NET en conteneur | Choix entre .NET Core et .NET Framework pour les conteneurs Docker
ms.date: 09/11/2018
ms.openlocfilehash: 771d23cf4610e5778f0a144386754ce10d6ae144
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296518"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="f21ec-103">Choix entre .NET Core et .NET Framework pour les conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="f21ec-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="f21ec-104">Il existe deux frameworks pris en charge pour générer des applications Docker en conteneur côté serveur avec .NET : [.NET Framework et .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="f21ec-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="f21ec-105">Ils partagent de nombreux composants de plateforme .NET et vous permettent de partager du code entre les deux.</span><span class="sxs-lookup"><span data-stu-id="f21ec-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="f21ec-106">Toutefois, il existe des différences fondamentales entre eux et votre choix dépend de ce que vous souhaitez accomplir.</span><span class="sxs-lookup"><span data-stu-id="f21ec-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="f21ec-107">Cette section fournit des instructions pour éclairer le choix de chaque framework.</span><span class="sxs-lookup"><span data-stu-id="f21ec-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f21ec-108">[Précédent](../container-docker-introduction/docker-containers-images-registries.md)
>[Suivant](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="f21ec-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
