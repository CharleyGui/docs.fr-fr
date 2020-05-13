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
ms.openlocfilehash: 611091d39da6d7f646457457f20ce1eaf37db361
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213203"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="4179c-102">ICorDebugFunction2, interface</span><span class="sxs-lookup"><span data-stu-id="4179c-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="4179c-103">Étend logiquement l’interface ICorDebugFunction pour assurer la prise en charge de Uniquement mon code le débogage pas à pas, ce qui ignore le code non-utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4179c-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4179c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4179c-104">Methods</span></span>  
  
|<span data-ttu-id="4179c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4179c-105">Method</span></span>|<span data-ttu-id="4179c-106">Description</span><span class="sxs-lookup"><span data-stu-id="4179c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4179c-107">EnumerateNativeCode, méthode</span><span class="sxs-lookup"><span data-stu-id="4179c-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="4179c-108">(Pas encore implémenté.) Obtient un pointeur d’interface vers un ICorDebugCodeEnum qui contient les instructions de code natif dans la fonction référencée par cet objet ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="4179c-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="4179c-109">GetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="4179c-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="4179c-110">Obtient une valeur qui indique si cette fonction est marquée en tant que code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4179c-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="4179c-111">GetVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="4179c-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="4179c-112">Obtient la version modifier & continuer de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="4179c-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="4179c-113">SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="4179c-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="4179c-114">Marque cette fonction pour Uniquement mon code pas à pas.</span><span class="sxs-lookup"><span data-stu-id="4179c-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4179c-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="4179c-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4179c-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="4179c-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4179c-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4179c-117">Requirements</span></span>  
 <span data-ttu-id="4179c-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4179c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4179c-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4179c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4179c-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4179c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4179c-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4179c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4179c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4179c-122">See also</span></span>

- [<span data-ttu-id="4179c-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4179c-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
