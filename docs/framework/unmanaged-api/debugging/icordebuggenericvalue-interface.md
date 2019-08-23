---
title: ICorDebugGenericValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36c2ed5529151a7ea18ccaffc2202ad6c69bcbd9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910228"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="5a7ac-102">ICorDebugGenericValue, interface</span><span class="sxs-lookup"><span data-stu-id="5a7ac-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="5a7ac-103">Sous-classe de «ICorDebugValue» qui s’applique à toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="5a7ac-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="5a7ac-104">Cette interface fournit les méthodes Get et Set pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="5a7ac-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a7ac-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5a7ac-105">Methods</span></span>  
  
|<span data-ttu-id="5a7ac-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="5a7ac-106">Method</span></span>|<span data-ttu-id="5a7ac-107">Description</span><span class="sxs-lookup"><span data-stu-id="5a7ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a7ac-108">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="5a7ac-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="5a7ac-109">Copie la valeur dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5a7ac-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="5a7ac-110">SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="5a7ac-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="5a7ac-111">Copie une nouvelle valeur à partir de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5a7ac-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a7ac-112">Notes</span><span class="sxs-lookup"><span data-stu-id="5a7ac-112">Remarks</span></span>  
 <span data-ttu-id="5a7ac-113">`ICorDebugGenericValue`est une sous-interface, car elle n’est pas accessible à distance.</span><span class="sxs-lookup"><span data-stu-id="5a7ac-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="5a7ac-114">Pour les types référence, la valeur est la référence plutôt que le contenu de la référence.</span><span class="sxs-lookup"><span data-stu-id="5a7ac-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="5a7ac-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="5a7ac-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a7ac-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="5a7ac-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a7ac-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5a7ac-117">Requirements</span></span>  
 <span data-ttu-id="5a7ac-118">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a7ac-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a7ac-119">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5a7ac-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a7ac-120">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a7ac-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a7ac-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a7ac-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a7ac-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a7ac-122">See also</span></span>

- [<span data-ttu-id="5a7ac-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5a7ac-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
