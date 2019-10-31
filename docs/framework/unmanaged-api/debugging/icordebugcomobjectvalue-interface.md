---
title: Interface ICorDebugComObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: 4ff5c0d470e6eb84eb8b526f5e8f74e5e1a8118a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125489"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="eaabd-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="eaabd-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="eaabd-103">Fournit des méthodes pour récupérer des informations associées à un wrapper RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="eaabd-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eaabd-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="eaabd-104">Methods</span></span>  
  
|<span data-ttu-id="eaabd-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="eaabd-105">Method</span></span>|<span data-ttu-id="eaabd-106">Description</span><span class="sxs-lookup"><span data-stu-id="eaabd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eaabd-107">GetCachedInterfacePointers, méthode</span><span class="sxs-lookup"><span data-stu-id="eaabd-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="eaabd-108">Obtient les pointeurs d’interface bruts mis en cache sur le wrapper RCW actuel.</span><span class="sxs-lookup"><span data-stu-id="eaabd-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="eaabd-109">GetCachedInterfaceTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="eaabd-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="eaabd-110">Fournit un énumérateur pour les types d’interface dont la casse de l’objet actuel a été ou utilisée.</span><span class="sxs-lookup"><span data-stu-id="eaabd-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaabd-111">Notes</span><span class="sxs-lookup"><span data-stu-id="eaabd-111">Remarks</span></span>  
 <span data-ttu-id="eaabd-112">Pour vérifier si une instance d’une interface « ICorDebugValue » représente un wrapper RCW, un débogueur appelle `QueryInterface` sur « ICorDebugValue » avec `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="eaabd-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaabd-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="eaabd-113">Requirements</span></span>  
 <span data-ttu-id="eaabd-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaabd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaabd-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaabd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaabd-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaabd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaabd-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaabd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaabd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eaabd-118">See also</span></span>

- [<span data-ttu-id="eaabd-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="eaabd-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="eaabd-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="eaabd-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
