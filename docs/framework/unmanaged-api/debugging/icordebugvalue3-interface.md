---
title: ICorDebugValue3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4bf3605331e6900fd890e49bb3f71f4ca4409c7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377591"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="2f6c1-102">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="2f6c1-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="2f6c1-103">Étend les interfaces de « ICorDebugValue » et « ICorDebugValue2 » pour prendre en charge pour les tableaux qui sont supérieures à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f6c1-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2f6c1-104">Methods</span></span>  
  
|<span data-ttu-id="2f6c1-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2f6c1-105">Method</span></span>|<span data-ttu-id="2f6c1-106">Description</span><span class="sxs-lookup"><span data-stu-id="2f6c1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f6c1-107">GetSize64, méthode</span><span class="sxs-lookup"><span data-stu-id="2f6c1-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="2f6c1-108">Obtient la taille, en octets, de ce `ICorDebugValue3` objet.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f6c1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="2f6c1-109">Remarks</span></span>  
 <span data-ttu-id="2f6c1-110">Le [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) méthode retourne une taille de l’objet qui est compris entre 0 et 2 147 483 647 octets.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="2f6c1-111">Dans le .NET Framework 4.5, la taille des tableaux peut dépasser 2 Go.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="2f6c1-112">Le `ICorDebugValue3` interface vous permet de déterminer la taille de ces tableaux.</span><span class="sxs-lookup"><span data-stu-id="2f6c1-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f6c1-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2f6c1-113">Requirements</span></span>  
 <span data-ttu-id="2f6c1-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f6c1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f6c1-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f6c1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f6c1-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f6c1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f6c1-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f6c1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6c1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f6c1-118">See also</span></span>

- [<span data-ttu-id="2f6c1-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2f6c1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2f6c1-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="2f6c1-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
