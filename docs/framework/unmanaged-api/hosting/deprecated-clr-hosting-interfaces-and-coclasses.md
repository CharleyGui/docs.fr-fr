---
title: Interfaces d'hébergement du CLR et coclasses déconseillées
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 8b90a33e2a0e6780a2ce908ff7ab251e94fbce90
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673096"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="6474a-102">Interfaces d'hébergement du CLR et coclasses déconseillées</span><span class="sxs-lookup"><span data-stu-id="6474a-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>

<span data-ttu-id="6474a-103">Cette section décrit les interfaces que les hôtes non gérés peuvent utiliser pour intégrer le common language runtime (CLR) dans les versions .NET Framework 1,0 et 1,1 dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="6474a-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="6474a-104">Ces interfaces fournissent des méthodes permettant à un hôte de configurer et de charger le runtime dans un processus.</span><span class="sxs-lookup"><span data-stu-id="6474a-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6474a-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6474a-105">In This Section</span></span>  

 <span data-ttu-id="6474a-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="6474a-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="6474a-107">Fournit des méthodes pour que l’hôte configure un <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="6474a-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="6474a-108">ICeeFileGen, classe</span><span class="sxs-lookup"><span data-stu-id="6474a-108">ICeeFileGen Class</span></span>](iceefilegen-class.md)  
 <span data-ttu-id="6474a-109">Déconseillé Fournit des fonctionnalités pour la création d’un fichier exécutable portable (PE) natif.</span><span class="sxs-lookup"><span data-stu-id="6474a-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="6474a-110">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="6474a-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)  
 <span data-ttu-id="6474a-111">Fournit des méthodes pour que l’hôte configure des paramètres CLR.</span><span class="sxs-lookup"><span data-stu-id="6474a-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6474a-112">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="6474a-112">Related Sections</span></span>  

 [<span data-ttu-id="6474a-113">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="6474a-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="6474a-114">Contient des rubriques qui décrivent les interfaces d’hébergement fournies avec le .NET Framework version 2,0 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6474a-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
