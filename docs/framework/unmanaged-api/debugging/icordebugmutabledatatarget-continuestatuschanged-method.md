---
title: ICorDebugMutableDataTarget::ContinueStatusChanged, méthode
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: c918bb60fba5bc1ec3f0f7c58b103d05a3c7ddfd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792873"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="c2f2c-102">ICorDebugMutableDataTarget::ContinueStatusChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="c2f2c-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="c2f2c-103">Modifie l'état de continuation de l'événement de débogage en suspens sur le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2f2c-104">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2f2c-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="c2f2c-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="c2f2c-106">Identificateur de thread défini par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="c2f2c-107">Valeur [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui représente le nouvel état de continuation demandé.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2f2c-108">Notes</span><span class="sxs-lookup"><span data-stu-id="c2f2c-108">Remarks</span></span>  
 <span data-ttu-id="c2f2c-109">Le débogueur appelle la méthode `ContinueStatusChanged` quand il appelle une méthode ICorDebug qui nécessite une gestion potentiellement anormale de l'événement de débogage actif.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="c2f2c-110">Par exemple, si une exception est en suspens et que le débogueur demande une opération susceptible d’annuler l’exception (comme [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) ou `FuncEval`), cette API permet de demander l’annulation de l’exception.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2f2c-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="c2f2c-111">Requirements</span></span>  
 <span data-ttu-id="c2f2c-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f2c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2f2c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2f2c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2f2c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2f2c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2f2c-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f2c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f2c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2f2c-116">See also</span></span>

- [<span data-ttu-id="c2f2c-117">ICorDebugMutableDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="c2f2c-117">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="c2f2c-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c2f2c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
