---
title: ICorDebugModuleBreakpoint, interface
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
ms.openlocfilehash: df3ad3fa4ef4eeee7e23ca1629da7a8b8ce09711
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792926"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="4abc8-102">ICorDebugModuleBreakpoint, interface</span><span class="sxs-lookup"><span data-stu-id="4abc8-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="4abc8-103">Fournit l’accès à des modules spécifiques.</span><span class="sxs-lookup"><span data-stu-id="4abc8-103">Provides access to specific modules.</span></span> <span data-ttu-id="4abc8-104">Cette interface est une sous-classe de l’interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="4abc8-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4abc8-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4abc8-105">Methods</span></span>  
  
|<span data-ttu-id="4abc8-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="4abc8-106">Method</span></span>|<span data-ttu-id="4abc8-107">Description</span><span class="sxs-lookup"><span data-stu-id="4abc8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4abc8-108">GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="4abc8-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="4abc8-109">Obtient un pointeur d’interface vers un ICorDebugModule qui référence le module dans lequel ce point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="4abc8-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4abc8-110">Notes</span><span class="sxs-lookup"><span data-stu-id="4abc8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4abc8-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="4abc8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4abc8-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4abc8-112">Requirements</span></span>  
 <span data-ttu-id="4abc8-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4abc8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4abc8-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4abc8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4abc8-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4abc8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4abc8-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4abc8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abc8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4abc8-117">See also</span></span>

- [<span data-ttu-id="4abc8-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4abc8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
