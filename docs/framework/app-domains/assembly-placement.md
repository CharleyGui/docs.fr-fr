---
title: Emplacement des assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6281a0f68fa0ce81b4763d8d0e8f17b47771d2ff
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053203"
---
# <a name="assembly-placement"></a><span data-ttu-id="46cd6-102">Emplacement des assemblys</span><span class="sxs-lookup"><span data-stu-id="46cd6-102">Assembly Placement</span></span>
<span data-ttu-id="46cd6-103">Pour la plupart des applications .NET Framework, vous localisez les assemblys qui composent une application dans le répertoire de l'application, dans un sous-répertoire de l'application ou dans le Global Assembly Cache (si l'assembly est partagé).</span><span class="sxs-lookup"><span data-stu-id="46cd6-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="46cd6-104">Vous pouvez effectuer des remplacements là où le common language runtime recherche un assembly à l’aide de l’élément [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="46cd6-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="46cd6-105">Si l’assembly n’a pas un nom fort, l’emplacement spécifié à l’aide de l’élément [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) est limité au répertoire ou à un sous-répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="46cd6-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="46cd6-106">Si l’assembly a un nom fort, l’élément [\<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) peut spécifier n’importe quel emplacement sur l’ordinateur ou sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="46cd6-106">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="46cd6-107">Des règles similaires sont appliquées pour localiser des assemblys lors de l'utilisation d'applications de code non managé ou de COM Interop : si l'assembly est partagé par plusieurs applications, il doit alors être installé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="46cd6-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="46cd6-108">Les assemblys utilisés avec du code non managé doivent être exportés en tant que bibliothèque de types et être inscrits.</span><span class="sxs-lookup"><span data-stu-id="46cd6-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="46cd6-109">Les assemblys utilisés par COM Interop doivent être inscrits dans le catalogue, même si cette inscription s'effectue dans certains cas automatiquement.</span><span class="sxs-lookup"><span data-stu-id="46cd6-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cd6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46cd6-110">See also</span></span>

- [<span data-ttu-id="46cd6-111">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="46cd6-111">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="46cd6-112">Configuration d'applications</span><span class="sxs-lookup"><span data-stu-id="46cd6-112">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="46cd6-113">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="46cd6-113">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="46cd6-114">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="46cd6-114">Assemblies in .NET</span></span>](index.md)
