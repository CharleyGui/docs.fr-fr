---
title: ICorDebugBlockingObjectEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: 221acf9bea714728a81b9f15c8165c1f9eba16a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719201"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="83e64-102">ICorDebugBlockingObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="83e64-102">ICorDebugBlockingObjectEnum Interface</span></span>

<span data-ttu-id="83e64-103">Fournit un énumérateur pour une liste de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="83e64-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="83e64-104">Cette interface est une sous-classe de l'interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="83e64-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83e64-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="83e64-105">Methods</span></span>  
  
|<span data-ttu-id="83e64-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="83e64-106">Method</span></span>|<span data-ttu-id="83e64-107">Description</span><span class="sxs-lookup"><span data-stu-id="83e64-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83e64-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="83e64-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="83e64-109">Énumère une liste de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="83e64-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83e64-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="83e64-110">Remarks</span></span>  

 <span data-ttu-id="83e64-111">Chaque structure `CorDebugBlockingObject` représente un objet qui bloque un thread.</span><span class="sxs-lookup"><span data-stu-id="83e64-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83e64-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="83e64-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e64-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="83e64-113">Requirements</span></span>  

 <span data-ttu-id="83e64-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e64-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e64-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83e64-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83e64-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83e64-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83e64-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e64-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e64-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83e64-118">See also</span></span>

- [<span data-ttu-id="83e64-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="83e64-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="83e64-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="83e64-120">Debugging</span></span>](index.md)
