---
title: Interfaces d'hébergement
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: f82301da1813b8d50deebf4452d8c07809c186c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721801"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="5d809-102">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="5d809-102">Hosting Interfaces</span></span>

<span data-ttu-id="5d809-103">Cette section décrit les interfaces que les hôtes non managés peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="5d809-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="5d809-104">Les interfaces d’hébergement .NET Framework version 2,0 remplacent les interfaces .NET Framework version 1,0 et 1,1.</span><span class="sxs-lookup"><span data-stu-id="5d809-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="5d809-105">Il existe des différences significatives entre les deux ensembles d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="5d809-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="5d809-106">Leur combinaison peut entraîner un comportement inattendu et n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="5d809-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="5d809-107">Les versions 3,0 et 3,5 de .NET Framework utilisent les interfaces d’hébergement .NET Framework version 2,0 et n’introduisent pas de fonctionnalités d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="5d809-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="5d809-108">Les interfaces d’hébergement .NET Framework 4 remplacent les interfaces .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="5d809-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="5d809-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5d809-109">In This Section</span></span>  

 [<span data-ttu-id="5d809-110">Interfaces d'hébergement du CLR et coclasses déconseillées</span><span class="sxs-lookup"><span data-stu-id="5d809-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="5d809-111">Décrit les interfaces d’hébergement introduites dans les versions 1,0 et 1,1 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d809-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="5d809-112">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="5d809-112">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="5d809-113">Décrit les interfaces d’hébergement introduites dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d809-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="5d809-114">Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="5d809-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="5d809-115">Décrit les interfaces d’hébergement introduites dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5d809-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5d809-116">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="5d809-116">Related Sections</span></span>  

 [<span data-ttu-id="5d809-117">Hébergement des coclasses</span><span class="sxs-lookup"><span data-stu-id="5d809-117">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="5d809-118">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="5d809-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="5d809-119">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="5d809-119">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="5d809-120">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="5d809-120">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="5d809-121">Hébergement</span><span class="sxs-lookup"><span data-stu-id="5d809-121">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="5d809-122">[Hôtes du runtime](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5d809-122">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
