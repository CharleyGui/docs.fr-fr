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
ms.openlocfilehash: cfa0950ca2ef4e969258c147b762fa95e52a82e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705812"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="7e227-102">ICorDebugGenericValue, interface</span><span class="sxs-lookup"><span data-stu-id="7e227-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="7e227-103">Sous-classe de « ICorDebugValue » qui s’applique à toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="7e227-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="7e227-104">Cette interface fournit les méthodes Get et Set pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="7e227-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e227-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7e227-105">Methods</span></span>  
  
|<span data-ttu-id="7e227-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="7e227-106">Method</span></span>|<span data-ttu-id="7e227-107">Description</span><span class="sxs-lookup"><span data-stu-id="7e227-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e227-108">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="7e227-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="7e227-109">Copie la valeur dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7e227-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="7e227-110">Méthode SetValue</span><span class="sxs-lookup"><span data-stu-id="7e227-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="7e227-111">Copie une nouvelle valeur à partir de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7e227-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e227-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="7e227-112">Remarks</span></span>  

 <span data-ttu-id="7e227-113">`ICorDebugGenericValue` est une sous-interface, car elle n’est pas accessible à distance.</span><span class="sxs-lookup"><span data-stu-id="7e227-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="7e227-114">Pour les types référence, la valeur est la référence plutôt que le contenu de la référence.</span><span class="sxs-lookup"><span data-stu-id="7e227-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="7e227-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="7e227-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e227-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="7e227-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e227-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7e227-117">Requirements</span></span>  

 <span data-ttu-id="7e227-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e227-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e227-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e227-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e227-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e227-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e227-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e227-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e227-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e227-122">See also</span></span>

- [<span data-ttu-id="7e227-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7e227-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
