---
title: ICorDebugThread4::GetBlockingObjects, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: 39833b689f28437b4241d9cb15fb4a92b2f9bcc3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791375"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="f34f1-102">ICorDebugThread4::GetBlockingObjects, méthode</span><span class="sxs-lookup"><span data-stu-id="f34f1-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="f34f1-103">Fournit une énumération ordonnée des structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) qui fournissent des informations sur le blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="f34f1-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f34f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f34f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="f34f1-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f34f1-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="f34f1-106">à Pointeur vers une énumération ordonnée de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f34f1-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f34f1-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f34f1-107">Remarks</span></span>  
 <span data-ttu-id="f34f1-108">Le premier élément de l’énumération retournée correspond à la première structure qui bloque le thread.</span><span class="sxs-lookup"><span data-stu-id="f34f1-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="f34f1-109">Le deuxième élément correspond à un élément bloquant qui est rencontré lors de l’exécution d’un appel de procédure asynchrone (APC) lorsqu’il est bloqué sur le premier, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="f34f1-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="f34f1-110">L’énumération est valide uniquement pour la durée de l’état synchronisé actuel.</span><span class="sxs-lookup"><span data-stu-id="f34f1-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="f34f1-111">Cette méthode doit être appelée lorsque l’élément débogué est dans un état synchronisé.</span><span class="sxs-lookup"><span data-stu-id="f34f1-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="f34f1-112">Si `ppBlockingObjectEnum` n’est pas un pointeur valide, le résultat n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="f34f1-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="f34f1-113">Si un thread est bloqué et que l’erreur ne peut pas être déterminée, la méthode retourne un HRESULT qui indique un échec ; Sinon, elle retourne S_OK.</span><span class="sxs-lookup"><span data-stu-id="f34f1-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f34f1-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f34f1-114">Requirements</span></span>  
 <span data-ttu-id="f34f1-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f34f1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f34f1-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f34f1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f34f1-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f34f1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f34f1-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f34f1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34f1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f34f1-119">See also</span></span>

- [<span data-ttu-id="f34f1-120">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="f34f1-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="f34f1-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f34f1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f34f1-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="f34f1-122">Debugging</span></span>](index.md)
