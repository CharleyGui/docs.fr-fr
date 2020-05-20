---
title: CoEEShutDownCOM, fonction
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
ms.openlocfilehash: 3eb8bffee9d30a89c39a900e600ebf171456b9f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616786"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="735f4-102">CoEEShutDownCOM, fonction</span><span class="sxs-lookup"><span data-stu-id="735f4-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="735f4-103">Force le common language runtime (CLR) à libérer tous les pointeurs d’interface qu’il contient dans les wrappers RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="735f4-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="735f4-104">Cela a pour effet de libérer tous les caches RCW.</span><span class="sxs-lookup"><span data-stu-id="735f4-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="735f4-105">Cette fonction globale est dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="735f4-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="735f4-106">Utilisez plutôt le point d’entrée pour un Runtime spécifique.</span><span class="sxs-lookup"><span data-stu-id="735f4-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="735f4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="735f4-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="735f4-108">Notes</span><span class="sxs-lookup"><span data-stu-id="735f4-108">Remarks</span></span>  
 <span data-ttu-id="735f4-109">La `CoEEShutDownCOM` fonction libère d’abord tous les RCW dans tous les contextes et dans tous les caches, puis supprime toutes les notifications de destruction existantes dans le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="735f4-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="735f4-110">Aucun déchargement de DLL ne se produit.</span><span class="sxs-lookup"><span data-stu-id="735f4-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="735f4-111">Cette fonction affecte tous les runtimes chargés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="735f4-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="735f4-112">À partir du .NET Framework 4, appelez le point d’entrée de cette fonction sur le runtime spécifique que vous souhaitez affecter.</span><span class="sxs-lookup"><span data-stu-id="735f4-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="735f4-113">Pour accéder au point d’entrée, appelez la méthode [ICLRRuntimeInfo :: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) et spécifiez « CoEEShutDownCOM, ».</span><span class="sxs-lookup"><span data-stu-id="735f4-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="735f4-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="735f4-114">Requirements</span></span>  
 <span data-ttu-id="735f4-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="735f4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="735f4-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="735f4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="735f4-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="735f4-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="735f4-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="735f4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="735f4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="735f4-119">See also</span></span>

- [<span data-ttu-id="735f4-120">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="735f4-120">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
