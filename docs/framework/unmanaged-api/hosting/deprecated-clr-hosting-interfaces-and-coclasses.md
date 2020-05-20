---
title: Interfaces d'hébergement du CLR et coclasses déconseillées
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 814f148b39045ad5454a23dfce8e7f9441f69041
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616409"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="aeeb2-102">Interfaces d'hébergement du CLR et coclasses déconseillées</span><span class="sxs-lookup"><span data-stu-id="aeeb2-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="aeeb2-103">Cette section décrit les interfaces que les hôtes non gérés peuvent utiliser pour intégrer le common language runtime (CLR) dans les versions .NET Framework 1,0 et 1,1 dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="aeeb2-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="aeeb2-104">Ces interfaces fournissent des méthodes permettant à un hôte de configurer et de charger le runtime dans un processus.</span><span class="sxs-lookup"><span data-stu-id="aeeb2-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aeeb2-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="aeeb2-105">In This Section</span></span>  
 <span data-ttu-id="aeeb2-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="aeeb2-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="aeeb2-107">Fournit des méthodes pour que l’hôte configure un <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="aeeb2-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="aeeb2-108">ICeeFileGen, classe</span><span class="sxs-lookup"><span data-stu-id="aeeb2-108">ICeeFileGen Class</span></span>](iceefilegen-class.md)  
 <span data-ttu-id="aeeb2-109">Déconseillé Fournit des fonctionnalités pour la création d’un fichier exécutable portable (PE) natif.</span><span class="sxs-lookup"><span data-stu-id="aeeb2-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="aeeb2-110">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="aeeb2-110">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)  
 <span data-ttu-id="aeeb2-111">Fournit des méthodes pour que l’hôte configure des paramètres CLR.</span><span class="sxs-lookup"><span data-stu-id="aeeb2-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aeeb2-112">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="aeeb2-112">Related Sections</span></span>  
 [<span data-ttu-id="aeeb2-113">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="aeeb2-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="aeeb2-114">Contient des rubriques qui décrivent les interfaces d’hébergement fournies avec le .NET Framework version 2,0 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="aeeb2-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
