---
title: Emplacement des assemblys
description: Passez en revue les instructions relatives à l’emplacement des assemblys .NET dans les répertoires (par exemple, dans le Global Assembly Cache ou dans le répertoire ou sous-répertoire de l’application).
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 15ff6edf5887062b0cce918b39beef6c9b618ca2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271550"
---
# <a name="assembly-placement"></a><span data-ttu-id="99240-103">Emplacement des assemblys</span><span class="sxs-lookup"><span data-stu-id="99240-103">Assembly Placement</span></span>

<span data-ttu-id="99240-104">Pour la plupart des applications .NET Framework, vous localisez les assemblys qui composent une application dans le répertoire de l'application, dans un sous-répertoire de l'application ou dans le Global Assembly Cache (si l'assembly est partagé).</span><span class="sxs-lookup"><span data-stu-id="99240-104">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="99240-105">Vous pouvez substituer l’emplacement où le common language runtime recherche un assembly à l’aide de l' [ \<codeBase> élément](../configure-apps/file-schema/runtime/codebase-element.md) dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="99240-105">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="99240-106">Si l’assembly n’a pas de nom fort, l’emplacement spécifié à l’aide de l' [ \<codeBase> élément](../configure-apps/file-schema/runtime/codebase-element.md) est limité au répertoire ou à un sous-répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="99240-106">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="99240-107">Si l’assembly a un nom fort, l' [ \<codeBase> élément](../configure-apps/file-schema/runtime/codebase-element.md) peut spécifier n’importe quel emplacement sur l’ordinateur ou sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="99240-107">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="99240-108">Des règles similaires sont appliquées pour localiser des assemblys lors de l'utilisation d'applications de code non managé ou de COM Interop : si l'assembly est partagé par plusieurs applications, il doit alors être installé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="99240-108">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="99240-109">Les assemblys utilisés avec du code non managé doivent être exportés en tant que bibliothèque de types et être inscrits.</span><span class="sxs-lookup"><span data-stu-id="99240-109">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="99240-110">Les assemblys utilisés par COM Interop doivent être inscrits dans le catalogue, même si cette inscription s'effectue dans certains cas automatiquement.</span><span class="sxs-lookup"><span data-stu-id="99240-110">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99240-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99240-111">See also</span></span>

- [<span data-ttu-id="99240-112">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="99240-112">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="99240-113">Configuration d’applications</span><span class="sxs-lookup"><span data-stu-id="99240-113">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="99240-114">Interopérabilité avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="99240-114">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="99240-115">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="99240-115">Assemblies in .NET</span></span>](index.md)
