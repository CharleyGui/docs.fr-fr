---
title: ICorDebugDataTarget3::GetLoadedModules (méthode)
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 120b839b2b11c85f42bb1a0ae4701de0dea33879
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912834"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="752c4-102">ICorDebugDataTarget3::GetLoadedModules (méthode)</span><span class="sxs-lookup"><span data-stu-id="752c4-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="752c4-103">Obtient la liste des modules qui ont été chargés jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="752c4-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="752c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="752c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="752c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="752c4-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="752c4-106">[in] Nombre de modules pour lesquels des informations sont demandées.</span><span class="sxs-lookup"><span data-stu-id="752c4-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="752c4-107">[out] Pointeur vers le nombre de modules à propos desquels des informations ont été retournées.</span><span class="sxs-lookup"><span data-stu-id="752c4-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="752c4-108">à Pointeur vers un tableau d’objets [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) qui fournissent des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="752c4-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="752c4-109">Notes</span><span class="sxs-lookup"><span data-stu-id="752c4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="752c4-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="752c4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="752c4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="752c4-111">Requirements</span></span>  
 <span data-ttu-id="752c4-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="752c4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="752c4-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="752c4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="752c4-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="752c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="752c4-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="752c4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="752c4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="752c4-116">See also</span></span>

- [<span data-ttu-id="752c4-117">ICorDebugDataTarget3, interface</span><span class="sxs-lookup"><span data-stu-id="752c4-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="752c4-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="752c4-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
