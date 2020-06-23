---
title: Utilisation de composants de service avec le Global Assembly Cache
description: Utilisez les composants de service (composants COM+ de code managé) avec le Global Assembly Cache dans .NET. Vérifiez si les services CLR et COM+ peuvent gérer des composants non-GAC.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 6b7371865b7b1cedda0ee03b2cc28c74b5c3da0b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104475"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="cb74b-104">Utilisation de composants de service avec le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="cb74b-104">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="cb74b-105">Les composants pris en charge (composants COM+ de code managé) doivent être placés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="cb74b-105">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="cb74b-106">Dans certains scénarios, le Common Language Runtime et les services COM+ peuvent gérer des composants pris en charge qui ne sont pas dans le Global Assembly Cache ; dans d’autres scénarios, cela est impossible.</span><span class="sxs-lookup"><span data-stu-id="cb74b-106">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="cb74b-107">Les scénarios suivants illustrent ce principe :</span><span class="sxs-lookup"><span data-stu-id="cb74b-107">The following scenarios illustrate this:</span></span>  
  
- <span data-ttu-id="cb74b-108">Pour les composants pris en charge dans une application serveur COM+, l’assembly contenant les composants doit être dans le Global Assembly Cache, car Dllhost.exe ne s’exécute pas dans le même répertoire que celui qui contient les composants pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cb74b-108">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
- <span data-ttu-id="cb74b-109">Pour les composants pris en charge dans une application bibliothèque COM+, le runtime et les services COM+ peuvent résoudre la référence à l’assembly contenant les composants en effectuant une recherche dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="cb74b-109">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="cb74b-110">Dans ce cas, l’assembly ne devra pas se trouver dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="cb74b-110">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
- <span data-ttu-id="cb74b-111">Pour les composants pris en charge dans une application ASP.NET, la situation est différente.</span><span class="sxs-lookup"><span data-stu-id="cb74b-111">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="cb74b-112">Si vous placez l’assembly contenant les composants pris en charge dans le répertoire bin de la base de l’application, et que vous utilisez l’inscription à la demande, l’assembly sera mis en mémoire fantôme dans le cache de téléchargement, car ASP.NET tire parti des possibilités de mémoire fantôme du runtime.</span><span class="sxs-lookup"><span data-stu-id="cb74b-112">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb74b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb74b-113">See also</span></span>

- [<span data-ttu-id="cb74b-114">Utilisation d'assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="cb74b-114">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="cb74b-115">Gacutil.exe (Outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="cb74b-115">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
