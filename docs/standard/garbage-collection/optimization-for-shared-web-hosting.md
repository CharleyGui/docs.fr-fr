---
title: Optimisation de l'hébergement Web partagé
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 6398c6749028827e5e3ee79a5511ac0879facbef
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824465"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="82b8a-102">Optimisation de l'hébergement Web partagé</span><span class="sxs-lookup"><span data-stu-id="82b8a-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="82b8a-103">Si vous êtes l’administrateur d’un serveur qui est partagé via l’hébergement de plusieurs petits sites web, vous pouvez optimiser les performances et augmenter la capacité du site en ajoutant le paramètre `gcTrimCommitOnLowMemory` suivant au nœud `runtime` dans le fichier Aspnet.config dans le répertoire .NET :</span><span class="sxs-lookup"><span data-stu-id="82b8a-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="82b8a-104">Ce paramètre n’est recommandé que dans les scénarios d’hébergement web partagé.</span><span class="sxs-lookup"><span data-stu-id="82b8a-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="82b8a-105">Étant donné que le récupérateur de mémoire conserve de la mémoire pour les répartitions futures, l’espace alloué peut être supérieur à ce qui est strictement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="82b8a-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="82b8a-106">Vous pouvez réduire cet espace en cas de charge importante sur la mémoire système.</span><span class="sxs-lookup"><span data-stu-id="82b8a-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="82b8a-107">La réduction de cet espace alloué améliore les performances et développe la capacité à héberger plusieurs sites.</span><span class="sxs-lookup"><span data-stu-id="82b8a-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="82b8a-108">Lorsque le paramètre `gcTrimCommitOnLowMemory` est activé, le récupérateur de mémoire évalue la charge de la mémoire système et entre en mode de suppression lorsque la charge atteint 90 %.</span><span class="sxs-lookup"><span data-stu-id="82b8a-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="82b8a-109">Il conserve le mode de suppression jusqu'à ce que la charge soit inférieure à 85 %.</span><span class="sxs-lookup"><span data-stu-id="82b8a-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="82b8a-110">Lorsque les conditions le permettent, le récupérateur de mémoire peut décider que le paramètre `gcTrimCommitOnLowMemory` n’aidera pas l’application actuelle et l’ignorer.</span><span class="sxs-lookup"><span data-stu-id="82b8a-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82b8a-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="82b8a-111">Example</span></span>  
 <span data-ttu-id="82b8a-112">Le fragment XML suivant montre comment activer le paramètre `gcTrimCommitOnLowMemory`.</span><span class="sxs-lookup"><span data-stu-id="82b8a-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="82b8a-113">Les points de suspension indiquent d’autres paramètres dans le nœud `runtime`.</span><span class="sxs-lookup"><span data-stu-id="82b8a-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82b8a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82b8a-114">See also</span></span>

- [<span data-ttu-id="82b8a-115">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="82b8a-115">Garbage Collection</span></span>](index.md)
