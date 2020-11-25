---
title: ICorDebugBoxValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
ms.openlocfilehash: 6d58ae048382a78c422703d5c6caeb3bbc739849
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723166"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="715c1-102">ICorDebugBoxValue, interface</span><span class="sxs-lookup"><span data-stu-id="715c1-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="715c1-103">Sous-classe de « ICorDebugHeapValue » qui représente un objet de classe de valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="715c1-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="715c1-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="715c1-104">Methods</span></span>  
  
|<span data-ttu-id="715c1-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="715c1-105">Method</span></span>|<span data-ttu-id="715c1-106">Description</span><span class="sxs-lookup"><span data-stu-id="715c1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="715c1-107">GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="715c1-107">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="715c1-108">Obtient un pointeur d’interface vers l’instance « ICorDebugObjectValue » boxed.</span><span class="sxs-lookup"><span data-stu-id="715c1-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="715c1-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="715c1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="715c1-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="715c1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="715c1-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="715c1-111">Requirements</span></span>  

 <span data-ttu-id="715c1-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="715c1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="715c1-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="715c1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="715c1-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="715c1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="715c1-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="715c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="715c1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="715c1-116">See also</span></span>

- [<span data-ttu-id="715c1-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="715c1-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
