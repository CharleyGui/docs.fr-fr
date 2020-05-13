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
ms.openlocfilehash: 5537a48fd085ce98de855fa1ec0913e2637e58e0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376192"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="f5792-102">ICorDebugStringValue, interface</span><span class="sxs-lookup"><span data-stu-id="f5792-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="f5792-103">Sous-classe de ICorDebugHeapValue qui s’applique aux valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f5792-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5792-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f5792-104">Methods</span></span>  
  
|<span data-ttu-id="f5792-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f5792-105">Method</span></span>|<span data-ttu-id="f5792-106">Description</span><span class="sxs-lookup"><span data-stu-id="f5792-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5792-107">GetLength, méthode</span><span class="sxs-lookup"><span data-stu-id="f5792-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="f5792-108">Obtient le nombre de caractères de la chaîne référencée par ce `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="f5792-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="f5792-109">GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="f5792-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="f5792-110">Obtient la chaîne référencée par ce `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="f5792-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5792-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f5792-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5792-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="f5792-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5792-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f5792-113">Requirements</span></span>  
 <span data-ttu-id="f5792-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5792-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5792-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5792-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5792-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5792-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5792-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5792-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5792-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5792-118">See also</span></span>

- [<span data-ttu-id="f5792-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f5792-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
