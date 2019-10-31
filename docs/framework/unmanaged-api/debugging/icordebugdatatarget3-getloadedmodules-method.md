---
title: ICorDebugDataTarget3::GetLoadedModules (méthode)
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: 6ee2215e2b3e3bd911158b3fc801361fc4e22db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136684"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="047d8-102">ICorDebugDataTarget3::GetLoadedModules (méthode)</span><span class="sxs-lookup"><span data-stu-id="047d8-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="047d8-103">Obtient la liste des modules qui ont été chargés jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="047d8-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="047d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="047d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="047d8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="047d8-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="047d8-106">[in] Nombre de modules pour lesquels des informations sont demandées.</span><span class="sxs-lookup"><span data-stu-id="047d8-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="047d8-107">[out] Pointeur vers le nombre de modules à propos desquels des informations ont été retournées.</span><span class="sxs-lookup"><span data-stu-id="047d8-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="047d8-108">à Pointeur vers un tableau d’objets [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) qui fournissent des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="047d8-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="047d8-109">Notes</span><span class="sxs-lookup"><span data-stu-id="047d8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="047d8-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="047d8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="047d8-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="047d8-111">Requirements</span></span>  
 <span data-ttu-id="047d8-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="047d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="047d8-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="047d8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="047d8-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="047d8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="047d8-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="047d8-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047d8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="047d8-116">See also</span></span>

- [<span data-ttu-id="047d8-117">ICorDebugDataTarget3, interface</span><span class="sxs-lookup"><span data-stu-id="047d8-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="047d8-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="047d8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
