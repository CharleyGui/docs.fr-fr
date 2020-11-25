---
title: ICorDebugFunction2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: d9e84a70d72db1338c80140ce3350774bfae4bca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726273"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="8dbac-102">ICorDebugFunction2, interface</span><span class="sxs-lookup"><span data-stu-id="8dbac-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="8dbac-103">Étend logiquement l’interface ICorDebugFunction pour assurer la prise en charge de Uniquement mon code le débogage pas à pas, ce qui ignore le code non-utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8dbac-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8dbac-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8dbac-104">Methods</span></span>  
  
|<span data-ttu-id="8dbac-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="8dbac-105">Method</span></span>|<span data-ttu-id="8dbac-106">Description</span><span class="sxs-lookup"><span data-stu-id="8dbac-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8dbac-107">EnumerateNativeCode, méthode</span><span class="sxs-lookup"><span data-stu-id="8dbac-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="8dbac-108">(Pas encore implémenté.) Obtient un pointeur d’interface vers un ICorDebugCodeEnum qui contient les instructions de code natif dans la fonction référencée par cet objet ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="8dbac-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="8dbac-109">GetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="8dbac-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="8dbac-110">Obtient une valeur qui indique si cette fonction est marquée en tant que code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8dbac-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="8dbac-111">GetVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="8dbac-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="8dbac-112">Obtient la version modifier & continuer de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="8dbac-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="8dbac-113">SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="8dbac-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="8dbac-114">Marque cette fonction pour Uniquement mon code pas à pas.</span><span class="sxs-lookup"><span data-stu-id="8dbac-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dbac-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="8dbac-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8dbac-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="8dbac-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dbac-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8dbac-117">Requirements</span></span>  

 <span data-ttu-id="8dbac-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dbac-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dbac-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8dbac-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8dbac-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8dbac-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8dbac-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dbac-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dbac-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dbac-122">See also</span></span>

- [<span data-ttu-id="8dbac-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8dbac-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
