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
ms.openlocfilehash: be1e1cd0d38ad71de43478af5565bb1ac98a8c0d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778000"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="8ef03-102">ICorDebugBlockingObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="8ef03-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="8ef03-103">Fournit un énumérateur pour une liste de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="8ef03-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="8ef03-104">Cette interface est une sous-classe de l'interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="8ef03-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ef03-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8ef03-105">Methods</span></span>  
  
|<span data-ttu-id="8ef03-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="8ef03-106">Method</span></span>|<span data-ttu-id="8ef03-107">Description</span><span class="sxs-lookup"><span data-stu-id="8ef03-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ef03-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="8ef03-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="8ef03-109">Énumère une liste de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="8ef03-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ef03-110">Notes</span><span class="sxs-lookup"><span data-stu-id="8ef03-110">Remarks</span></span>  
 <span data-ttu-id="8ef03-111">Chaque structure `CorDebugBlockingObject` représente un objet qui bloque un thread.</span><span class="sxs-lookup"><span data-stu-id="8ef03-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ef03-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="8ef03-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef03-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="8ef03-113">Requirements</span></span>  
 <span data-ttu-id="8ef03-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef03-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef03-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ef03-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ef03-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ef03-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ef03-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef03-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef03-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ef03-118">See also</span></span>

- [<span data-ttu-id="8ef03-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8ef03-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8ef03-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="8ef03-120">Debugging</span></span>](index.md)
