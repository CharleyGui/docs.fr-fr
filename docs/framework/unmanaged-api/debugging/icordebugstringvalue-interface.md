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
ms.openlocfilehash: cd6c5726b9a938d04cf4eb018ec9851c81d9c745
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697049"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="08d7b-102">ICorDebugStringValue, interface</span><span class="sxs-lookup"><span data-stu-id="08d7b-102">ICorDebugStringValue Interface</span></span>

<span data-ttu-id="08d7b-103">Sous-classe de ICorDebugHeapValue qui s’applique aux valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="08d7b-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08d7b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="08d7b-104">Methods</span></span>  
  
|<span data-ttu-id="08d7b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="08d7b-105">Method</span></span>|<span data-ttu-id="08d7b-106">Description</span><span class="sxs-lookup"><span data-stu-id="08d7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08d7b-107">GetLength, méthode</span><span class="sxs-lookup"><span data-stu-id="08d7b-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="08d7b-108">Obtient le nombre de caractères de la chaîne référencée par ce `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="08d7b-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="08d7b-109">GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="08d7b-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="08d7b-110">Obtient la chaîne référencée par ce `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="08d7b-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d7b-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="08d7b-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08d7b-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="08d7b-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d7b-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08d7b-113">Requirements</span></span>  

 <span data-ttu-id="08d7b-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d7b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d7b-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08d7b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08d7b-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08d7b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08d7b-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d7b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d7b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08d7b-118">See also</span></span>

- [<span data-ttu-id="08d7b-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="08d7b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
