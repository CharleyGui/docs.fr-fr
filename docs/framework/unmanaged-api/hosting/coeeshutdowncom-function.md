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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74548df512f68761b006e064a6db968e82b03813
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779121"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="66b15-102">CoEEShutDownCOM, fonction</span><span class="sxs-lookup"><span data-stu-id="66b15-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="66b15-103">Force le common language runtime (CLR) pour libérer tous les pointeurs d’interface qu’il conserve dans callable wrappers RCW (runtime).</span><span class="sxs-lookup"><span data-stu-id="66b15-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="66b15-104">Cela a pour effet de libérer tous les caches de wrapper RCW.</span><span class="sxs-lookup"><span data-stu-id="66b15-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="66b15-105">Cette fonction globale est déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="66b15-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="66b15-106">Au lieu de cela, utilisez le point d’entrée pour une exécution spécifique.</span><span class="sxs-lookup"><span data-stu-id="66b15-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b15-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66b15-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="66b15-108">Notes</span><span class="sxs-lookup"><span data-stu-id="66b15-108">Remarks</span></span>  
 <span data-ttu-id="66b15-109">Le `CoEEShutDownCOM` fonction libère tout d’abord tous les wrappers RCW dans tous les contextes et dans tous les caches et la supprime ensuite toute notification de destruction existante dans le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="66b15-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="66b15-110">Aucun déchargement de DLL se produit.</span><span class="sxs-lookup"><span data-stu-id="66b15-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="66b15-111">Cette fonction affecte tous les runtimes chargés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="66b15-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="66b15-112">À compter de .NET Framework 4, appelez le point d’entrée pour cette fonction sur le runtime spécifique que vous souhaitez affecter.</span><span class="sxs-lookup"><span data-stu-id="66b15-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="66b15-113">Pour obtenir le point d’entrée, appelez le [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) (méthode) et spécifiez « CoEEShutDownCOM ».</span><span class="sxs-lookup"><span data-stu-id="66b15-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66b15-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66b15-114">Requirements</span></span>  
 <span data-ttu-id="66b15-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66b15-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66b15-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66b15-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66b15-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66b15-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66b15-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66b15-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b15-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66b15-119">See also</span></span>

- [<span data-ttu-id="66b15-120">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="66b15-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
