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
ms.openlocfilehash: 7026d135b02563b6c718be4096d2c5cad9d33cec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212280"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="c2f21-102">ICorDebugModuleBreakpoint, interface</span><span class="sxs-lookup"><span data-stu-id="c2f21-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="c2f21-103">Fournit l’accès à des modules spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c2f21-103">Provides access to specific modules.</span></span> <span data-ttu-id="c2f21-104">Cette interface est une sous-classe de l’interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="c2f21-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2f21-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c2f21-105">Methods</span></span>  
  
|<span data-ttu-id="c2f21-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="c2f21-106">Method</span></span>|<span data-ttu-id="c2f21-107">Description</span><span class="sxs-lookup"><span data-stu-id="c2f21-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2f21-108">GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="c2f21-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="c2f21-109">Obtient un pointeur d’interface vers un ICorDebugModule qui référence le module dans lequel ce point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="c2f21-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2f21-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="c2f21-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2f21-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="c2f21-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2f21-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c2f21-112">Requirements</span></span>  
 <span data-ttu-id="c2f21-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f21-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2f21-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2f21-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2f21-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2f21-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2f21-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f21-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f21-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2f21-117">See also</span></span>

- [<span data-ttu-id="c2f21-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c2f21-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
