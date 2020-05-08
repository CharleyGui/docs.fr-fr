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
ms.openlocfilehash: 8be4332da77c3fbf4229a3fbeb9ba835a7a13eee
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894792"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="4e32e-102">ICorDebugBlockingObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="4e32e-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="4e32e-103">Fournit un énumérateur pour une liste de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="4e32e-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="4e32e-104">Cette interface est une sous-classe de l'interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="4e32e-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e32e-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4e32e-105">Methods</span></span>  
  
|<span data-ttu-id="4e32e-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="4e32e-106">Method</span></span>|<span data-ttu-id="4e32e-107">Description</span><span class="sxs-lookup"><span data-stu-id="4e32e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e32e-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="4e32e-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="4e32e-109">Énumère une liste de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="4e32e-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e32e-110">Notes </span><span class="sxs-lookup"><span data-stu-id="4e32e-110">Remarks</span></span>  
 <span data-ttu-id="4e32e-111">Chaque structure `CorDebugBlockingObject` représente un objet qui bloque un thread.</span><span class="sxs-lookup"><span data-stu-id="4e32e-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e32e-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="4e32e-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e32e-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4e32e-113">Requirements</span></span>  
 <span data-ttu-id="4e32e-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e32e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e32e-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e32e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e32e-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e32e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e32e-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e32e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e32e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e32e-118">See also</span></span>

- [<span data-ttu-id="4e32e-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4e32e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4e32e-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="4e32e-120">Debugging</span></span>](index.md)
