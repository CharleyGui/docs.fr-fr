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
ms.openlocfilehash: 9f521eb942f37b8cf1d00bcc672071a69692b876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396650"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="d0ad8-102">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="d0ad8-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="d0ad8-103">Étend les interfaces « ICorDebugValue » et « ICorDebugValue2 » pour assurer la prise en charge des tableaux d’une taille supérieure à 2 Go.</span><span class="sxs-lookup"><span data-stu-id="d0ad8-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0ad8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d0ad8-104">Methods</span></span>  
  
|<span data-ttu-id="d0ad8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d0ad8-105">Method</span></span>|<span data-ttu-id="d0ad8-106">Description</span><span class="sxs-lookup"><span data-stu-id="d0ad8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0ad8-107">GetSize64, méthode</span><span class="sxs-lookup"><span data-stu-id="d0ad8-107">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="d0ad8-108">Obtient la taille, en octets, de cet `ICorDebugValue3` objet.</span><span class="sxs-lookup"><span data-stu-id="d0ad8-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0ad8-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d0ad8-109">Remarks</span></span>  
 <span data-ttu-id="d0ad8-110">La méthode [ICorDebugValue ::](icordebugvalue3-getsize64-method.md) Desize retourne une taille d’objet comprise entre 0 et 2 147 483 647 octets.</span><span class="sxs-lookup"><span data-stu-id="d0ad8-110">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="d0ad8-111">Dans le .NET Framework 4,5, la taille des tableaux peut dépasser 2 Go.</span><span class="sxs-lookup"><span data-stu-id="d0ad8-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="d0ad8-112">L' `ICorDebugValue3` interface vous permet de déterminer la taille de ces tableaux.</span><span class="sxs-lookup"><span data-stu-id="d0ad8-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ad8-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d0ad8-113">Requirements</span></span>  
 <span data-ttu-id="d0ad8-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0ad8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0ad8-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0ad8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0ad8-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0ad8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0ad8-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ad8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ad8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0ad8-118">See also</span></span>

- [<span data-ttu-id="d0ad8-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d0ad8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d0ad8-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="d0ad8-120">Debugging</span></span>](index.md)
