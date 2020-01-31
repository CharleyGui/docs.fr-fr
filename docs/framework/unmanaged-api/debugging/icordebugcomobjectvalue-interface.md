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
ms.openlocfilehash: ed5b39ed4b2a14c071bf23fb04efbad6834e8a9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783971"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="e4bdb-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="e4bdb-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="e4bdb-103">Fournit des méthodes pour récupérer des informations associées à un wrapper RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="e4bdb-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4bdb-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e4bdb-104">Methods</span></span>  
  
|<span data-ttu-id="e4bdb-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e4bdb-105">Method</span></span>|<span data-ttu-id="e4bdb-106">Description</span><span class="sxs-lookup"><span data-stu-id="e4bdb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4bdb-107">GetCachedInterfacePointers, méthode</span><span class="sxs-lookup"><span data-stu-id="e4bdb-107">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="e4bdb-108">Obtient les pointeurs d’interface bruts mis en cache sur le wrapper RCW actuel.</span><span class="sxs-lookup"><span data-stu-id="e4bdb-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="e4bdb-109">GetCachedInterfaceTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="e4bdb-109">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="e4bdb-110">Fournit un énumérateur pour les types d’interface dont la casse de l’objet actuel a été ou utilisée.</span><span class="sxs-lookup"><span data-stu-id="e4bdb-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4bdb-111">Notes</span><span class="sxs-lookup"><span data-stu-id="e4bdb-111">Remarks</span></span>  
 <span data-ttu-id="e4bdb-112">Pour vérifier si une instance d’une interface « ICorDebugValue » représente un wrapper RCW, un débogueur appelle `QueryInterface` sur « ICorDebugValue » avec `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="e4bdb-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4bdb-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e4bdb-113">Requirements</span></span>  
 <span data-ttu-id="e4bdb-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4bdb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4bdb-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4bdb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4bdb-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4bdb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4bdb-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4bdb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bdb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4bdb-118">See also</span></span>

- [<span data-ttu-id="e4bdb-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e4bdb-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e4bdb-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="e4bdb-120">Debugging</span></span>](index.md)
