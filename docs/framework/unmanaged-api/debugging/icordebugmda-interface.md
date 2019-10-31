---
title: ICorDebugMDA, interface
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 4201fe23bf54388510088e21471edce91809e94c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129796"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="daa2e-102">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="daa2e-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="daa2e-103">Représente un message d'Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="daa2e-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="daa2e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="daa2e-104">Methods</span></span>  
  
|<span data-ttu-id="daa2e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="daa2e-105">Method</span></span>|<span data-ttu-id="daa2e-106">Description</span><span class="sxs-lookup"><span data-stu-id="daa2e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="daa2e-107">GetDescription, méthode</span><span class="sxs-lookup"><span data-stu-id="daa2e-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="daa2e-108">Obtient une chaîne contenant une description de cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="daa2e-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="daa2e-109">GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="daa2e-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="daa2e-110">Obtient les indicateurs associés à cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="daa2e-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="daa2e-111">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="daa2e-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="daa2e-112">Obtient une chaîne contenant le nom de cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="daa2e-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="daa2e-113">GetOSThreadId, méthode</span><span class="sxs-lookup"><span data-stu-id="daa2e-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="daa2e-114">Obtient l’identificateur de thread de système d’exploitation sur lequel cet Assistant Débogage managé s’exécute.</span><span class="sxs-lookup"><span data-stu-id="daa2e-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="daa2e-115">GetXML, méthode</span><span class="sxs-lookup"><span data-stu-id="daa2e-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="daa2e-116">Obtient le flux de données XML complet associé à cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="daa2e-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daa2e-117">Notes</span><span class="sxs-lookup"><span data-stu-id="daa2e-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="daa2e-118">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="daa2e-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daa2e-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="daa2e-119">Requirements</span></span>  
 <span data-ttu-id="daa2e-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daa2e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daa2e-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="daa2e-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daa2e-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daa2e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daa2e-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daa2e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa2e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daa2e-124">See also</span></span>

- [<span data-ttu-id="daa2e-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="daa2e-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="daa2e-126">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="daa2e-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
