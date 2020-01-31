---
title: ICorDebugValueBreakpoint, interface
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
ms.openlocfilehash: e1bb5a6fd0550f7c25d46fa31ca11a10cec54986
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791075"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="ffc6e-102">ICorDebugValueBreakpoint, interface</span><span class="sxs-lookup"><span data-stu-id="ffc6e-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="ffc6e-103">Étend l’interface ICorDebugBreakpoint pour fournir l’accès à des valeurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ffc6e-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffc6e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ffc6e-104">Methods</span></span>  
  
|<span data-ttu-id="ffc6e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ffc6e-105">Method</span></span>|<span data-ttu-id="ffc6e-106">Description</span><span class="sxs-lookup"><span data-stu-id="ffc6e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffc6e-107">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="ffc6e-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="ffc6e-108">Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente la valeur de l’objet sur lequel le point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="ffc6e-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffc6e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ffc6e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffc6e-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ffc6e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffc6e-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ffc6e-111">Requirements</span></span>  
 <span data-ttu-id="ffc6e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffc6e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffc6e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffc6e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffc6e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffc6e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffc6e-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffc6e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc6e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffc6e-116">See also</span></span>

- [<span data-ttu-id="ffc6e-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ffc6e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
