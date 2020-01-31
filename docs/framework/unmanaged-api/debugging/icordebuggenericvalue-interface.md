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
ms.openlocfilehash: e60d4b128bf03ff81863e0c95815b2c204807583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794469"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="29872-102">ICorDebugGenericValue, interface</span><span class="sxs-lookup"><span data-stu-id="29872-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="29872-103">Sous-classe de « ICorDebugValue » qui s’applique à toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="29872-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="29872-104">Cette interface fournit les méthodes Get et Set pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="29872-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29872-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="29872-105">Methods</span></span>  
  
|<span data-ttu-id="29872-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="29872-106">Method</span></span>|<span data-ttu-id="29872-107">Description</span><span class="sxs-lookup"><span data-stu-id="29872-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29872-108">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="29872-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="29872-109">Copie la valeur dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="29872-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="29872-110">SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="29872-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="29872-111">Copie une nouvelle valeur à partir de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="29872-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29872-112">Notes</span><span class="sxs-lookup"><span data-stu-id="29872-112">Remarks</span></span>  
 <span data-ttu-id="29872-113">`ICorDebugGenericValue` est une sous-interface, car elle n’est pas accessible à distance.</span><span class="sxs-lookup"><span data-stu-id="29872-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="29872-114">Pour les types référence, la valeur est la référence plutôt que le contenu de la référence.</span><span class="sxs-lookup"><span data-stu-id="29872-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="29872-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="29872-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29872-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="29872-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29872-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="29872-117">Requirements</span></span>  
 <span data-ttu-id="29872-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29872-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29872-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29872-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29872-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29872-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29872-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29872-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29872-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29872-122">See also</span></span>

- [<span data-ttu-id="29872-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="29872-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
