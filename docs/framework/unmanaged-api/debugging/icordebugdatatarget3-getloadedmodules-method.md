---
title: ICorDebugDataTarget3::GetLoadedModules (méthode)
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: efbada02b7a24e0a7ed613b86b8a4a1a0b5b051a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713745"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="d56c2-102">ICorDebugDataTarget3::GetLoadedModules (méthode)</span><span class="sxs-lookup"><span data-stu-id="d56c2-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>

<span data-ttu-id="d56c2-103">Obtient la liste des modules qui ont été chargés jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="d56c2-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d56c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d56c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d56c2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d56c2-105">Parameters</span></span>  

 `cRequestedModules`  
 <span data-ttu-id="d56c2-106">[in] Nombre de modules pour lesquels des informations sont demandées.</span><span class="sxs-lookup"><span data-stu-id="d56c2-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="d56c2-107">[out] Pointeur vers le nombre de modules à propos desquels des informations ont été retournées.</span><span class="sxs-lookup"><span data-stu-id="d56c2-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="d56c2-108">à Pointeur vers un tableau d’objets [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) qui fournissent des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="d56c2-108">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d56c2-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="d56c2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d56c2-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d56c2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d56c2-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d56c2-111">Requirements</span></span>  

 <span data-ttu-id="d56c2-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d56c2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d56c2-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d56c2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d56c2-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d56c2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d56c2-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d56c2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56c2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d56c2-116">See also</span></span>

- [<span data-ttu-id="d56c2-117">ICorDebugDataTarget3 (interface)</span><span class="sxs-lookup"><span data-stu-id="d56c2-117">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="d56c2-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d56c2-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
