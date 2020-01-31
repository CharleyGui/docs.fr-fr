---
title: ICorDebugStringValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
ms.openlocfilehash: 6c232163f7c18086804eca7990a0890a507ef00b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791690"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="025c0-102">ICorDebugStringValue, interface</span><span class="sxs-lookup"><span data-stu-id="025c0-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="025c0-103">Sous-classe de ICorDebugHeapValue qui s’applique aux valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="025c0-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="025c0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="025c0-104">Methods</span></span>  
  
|<span data-ttu-id="025c0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="025c0-105">Method</span></span>|<span data-ttu-id="025c0-106">Description</span><span class="sxs-lookup"><span data-stu-id="025c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="025c0-107">GetLength, méthode</span><span class="sxs-lookup"><span data-stu-id="025c0-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="025c0-108">Obtient le nombre de caractères de la chaîne référencée par cette `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="025c0-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="025c0-109">GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="025c0-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="025c0-110">Obtient la chaîne référencée par cette `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="025c0-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="025c0-111">Notes</span><span class="sxs-lookup"><span data-stu-id="025c0-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="025c0-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="025c0-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="025c0-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="025c0-113">Requirements</span></span>  
 <span data-ttu-id="025c0-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="025c0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="025c0-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="025c0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="025c0-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="025c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="025c0-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="025c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025c0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="025c0-118">See also</span></span>

- [<span data-ttu-id="025c0-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="025c0-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
