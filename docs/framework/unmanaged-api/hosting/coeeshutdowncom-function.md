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
ms.openlocfilehash: 4e85a9a98bf0550fa906f8b905c73890948f4ac1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124940"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="55c93-102">CoEEShutDownCOM, fonction</span><span class="sxs-lookup"><span data-stu-id="55c93-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="55c93-103">Force le common language runtime (CLR) à libérer tous les pointeurs d’interface qu’il contient dans les wrappers RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="55c93-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="55c93-104">Cela a pour effet de libérer tous les caches RCW.</span><span class="sxs-lookup"><span data-stu-id="55c93-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="55c93-105">Cette fonction globale est dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55c93-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="55c93-106">Utilisez plutôt le point d’entrée pour un Runtime spécifique.</span><span class="sxs-lookup"><span data-stu-id="55c93-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55c93-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55c93-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="55c93-108">Notes</span><span class="sxs-lookup"><span data-stu-id="55c93-108">Remarks</span></span>  
 <span data-ttu-id="55c93-109">La fonction `CoEEShutDownCOM` libère d’abord tous les wrappers RCW dans tous les contextes et dans tous les caches, puis supprime toutes les notifications de destruction existantes dans le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="55c93-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="55c93-110">Aucun déchargement de DLL ne se produit.</span><span class="sxs-lookup"><span data-stu-id="55c93-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="55c93-111">Cette fonction affecte tous les runtimes chargés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="55c93-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="55c93-112">À partir du .NET Framework 4, appelez le point d’entrée de cette fonction sur le runtime spécifique que vous souhaitez affecter.</span><span class="sxs-lookup"><span data-stu-id="55c93-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="55c93-113">Pour accéder au point d’entrée, appelez la méthode [ICLRRuntimeInfo :: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) et spécifiez « CoEEShutDownCOM, ».</span><span class="sxs-lookup"><span data-stu-id="55c93-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55c93-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="55c93-114">Requirements</span></span>  
 <span data-ttu-id="55c93-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55c93-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55c93-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="55c93-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55c93-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="55c93-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55c93-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55c93-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c93-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55c93-119">See also</span></span>

- [<span data-ttu-id="55c93-120">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="55c93-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
