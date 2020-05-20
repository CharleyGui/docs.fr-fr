---
title: Interfaces d'hébergement
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: d1668f52ff305ec36fb520c7828c822537da0d02
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616097"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="c2258-102">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="c2258-102">Hosting Interfaces</span></span>
<span data-ttu-id="c2258-103">Cette section décrit les interfaces que les hôtes non managés peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="c2258-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="c2258-104">Les interfaces d’hébergement .NET Framework version 2,0 remplacent les interfaces .NET Framework version 1,0 et 1,1.</span><span class="sxs-lookup"><span data-stu-id="c2258-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="c2258-105">Il existe des différences significatives entre les deux ensembles d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="c2258-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="c2258-106">Leur combinaison peut entraîner un comportement inattendu et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="c2258-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="c2258-107">Les versions 3,0 et 3,5 de .NET Framework utilisent les interfaces d’hébergement .NET Framework version 2,0 et n’introduisent pas de fonctionnalités d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="c2258-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="c2258-108">Les interfaces d’hébergement .NET Framework 4 remplacent les interfaces .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c2258-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="c2258-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c2258-109">In This Section</span></span>  
 [<span data-ttu-id="c2258-110">Interfaces d'hébergement du CLR et coclasses déconseillées</span><span class="sxs-lookup"><span data-stu-id="c2258-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="c2258-111">Décrit les interfaces d’hébergement introduites dans les versions 1,0 et 1,1 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2258-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="c2258-112">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="c2258-112">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="c2258-113">Décrit les interfaces d’hébergement introduites dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2258-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="c2258-114">Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="c2258-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="c2258-115">Décrit les interfaces d’hébergement introduites dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c2258-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c2258-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="c2258-116">Related Sections</span></span>  
 [<span data-ttu-id="c2258-117">Hébergement des coclasses</span><span class="sxs-lookup"><span data-stu-id="c2258-117">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="c2258-118">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="c2258-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="c2258-119">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="c2258-119">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="c2258-120">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="c2258-120">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="c2258-121">Hébergement</span><span class="sxs-lookup"><span data-stu-id="c2258-121">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="c2258-122">[Hôtes du runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c2258-122">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
