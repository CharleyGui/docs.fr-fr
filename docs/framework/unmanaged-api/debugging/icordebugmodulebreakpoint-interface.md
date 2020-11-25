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
ms.openlocfilehash: 14f2b6822744070e649cf9a6722272992c0bf1c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709516"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="2da03-102">ICorDebugModuleBreakpoint, interface</span><span class="sxs-lookup"><span data-stu-id="2da03-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="2da03-103">Fournit l’accès à des modules spécifiques.</span><span class="sxs-lookup"><span data-stu-id="2da03-103">Provides access to specific modules.</span></span> <span data-ttu-id="2da03-104">Cette interface est une sous-classe de l’interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="2da03-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2da03-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2da03-105">Methods</span></span>  
  
|<span data-ttu-id="2da03-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="2da03-106">Method</span></span>|<span data-ttu-id="2da03-107">Description</span><span class="sxs-lookup"><span data-stu-id="2da03-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2da03-108">GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="2da03-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="2da03-109">Obtient un pointeur d’interface vers un ICorDebugModule qui référence le module dans lequel ce point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="2da03-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2da03-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="2da03-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2da03-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="2da03-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2da03-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2da03-112">Requirements</span></span>  

 <span data-ttu-id="2da03-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2da03-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2da03-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2da03-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2da03-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2da03-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2da03-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2da03-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da03-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2da03-117">See also</span></span>

- [<span data-ttu-id="2da03-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2da03-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
