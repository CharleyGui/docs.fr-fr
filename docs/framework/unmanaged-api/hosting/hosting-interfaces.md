---
title: Interfaces d'hébergement
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: 43b401885bb4de69a06496874f11cec6cdf04b22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126973"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="16185-102">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="16185-102">Hosting Interfaces</span></span>
<span data-ttu-id="16185-103">Cette section décrit les interfaces que les hôtes non managés peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="16185-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="16185-104">Les interfaces d’hébergement .NET Framework version 2,0 remplacent les interfaces .NET Framework version 1,0 et 1,1.</span><span class="sxs-lookup"><span data-stu-id="16185-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="16185-105">Il existe des différences significatives entre les deux ensembles d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="16185-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="16185-106">Leur combinaison peut entraîner un comportement inattendu et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="16185-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="16185-107">Les versions 3,0 et 3,5 de .NET Framework utilisent les interfaces d’hébergement .NET Framework version 2,0 et n’introduisent pas de fonctionnalités d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="16185-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="16185-108">Les interfaces d’hébergement .NET Framework 4 remplacent les interfaces .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="16185-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="16185-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="16185-109">In This Section</span></span>  
 [<span data-ttu-id="16185-110">Coclasses et interfaces d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="16185-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="16185-111">Décrit les interfaces d’hébergement introduites dans les versions 1,0 et 1,1 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16185-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="16185-112">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="16185-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="16185-113">Décrit les interfaces d’hébergement introduites dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16185-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="16185-114">Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="16185-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="16185-115">Décrit les interfaces d’hébergement introduites dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="16185-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="16185-116">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="16185-116">Related Sections</span></span>  
 [<span data-ttu-id="16185-117">Coclasses d’hébergement</span><span class="sxs-lookup"><span data-stu-id="16185-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="16185-118">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="16185-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="16185-119">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="16185-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="16185-120">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="16185-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="16185-121">Hébergement</span><span class="sxs-lookup"><span data-stu-id="16185-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 <span data-ttu-id="16185-122">[Hôtes du runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="16185-122">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
