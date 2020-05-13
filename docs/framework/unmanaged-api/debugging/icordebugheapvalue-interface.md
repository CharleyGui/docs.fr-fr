---
title: ICorDebugHeapValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: 36a485413490045ca49b99fca4fe5d43edc37114
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213008"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="c5aa3-102">ICorDebugHeapValue, interface</span><span class="sxs-lookup"><span data-stu-id="c5aa3-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="c5aa3-103">Sous-classe de « ICorDebugValue » qui représente un objet qui a été collecté par le garbage collector common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c5aa3-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5aa3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c5aa3-104">Methods</span></span>  
  
|<span data-ttu-id="c5aa3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="c5aa3-105">Method</span></span>|<span data-ttu-id="c5aa3-106">Description</span><span class="sxs-lookup"><span data-stu-id="c5aa3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5aa3-107">CreateRelocBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="c5aa3-107">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="c5aa3-108">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="c5aa3-108">Not implemented.</span></span>|  
|[<span data-ttu-id="c5aa3-109">IsValid, méthode</span><span class="sxs-lookup"><span data-stu-id="c5aa3-109">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="c5aa3-110">Obtient une valeur qui indique si l’objet représenté par ce `ICorDebugHeapValue` est valide ou a été récupéré par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="c5aa3-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="c5aa3-111">Cette méthode est déconseillée dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5aa3-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5aa3-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="c5aa3-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5aa3-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="c5aa3-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5aa3-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c5aa3-114">Requirements</span></span>  
 <span data-ttu-id="c5aa3-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5aa3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5aa3-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5aa3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5aa3-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5aa3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5aa3-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5aa3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5aa3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5aa3-119">See also</span></span>

- [<span data-ttu-id="c5aa3-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c5aa3-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
