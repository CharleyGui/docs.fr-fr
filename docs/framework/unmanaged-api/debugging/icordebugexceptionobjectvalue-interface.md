---
title: ICorDebugExceptionObjectValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
ms.openlocfilehash: a5762079861f04e1869b206c3200c3a024c1b77a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091007"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="1df0e-102">ICorDebugExceptionObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="1df0e-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="1df0e-103">Étend l’interface « ICorDebugObjectValue » pour fournir des informations de trace de la pile à partir d’un objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="1df0e-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1df0e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1df0e-104">Methods</span></span>  
  
|<span data-ttu-id="1df0e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1df0e-105">Method</span></span>|<span data-ttu-id="1df0e-106">Description</span><span class="sxs-lookup"><span data-stu-id="1df0e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1df0e-107">EnumerateExceptionCallStack, méthode</span><span class="sxs-lookup"><span data-stu-id="1df0e-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="1df0e-108">Obtient un énumérateur de la pile des appels incorporée dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="1df0e-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1df0e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1df0e-109">Remarks</span></span>  
 <span data-ttu-id="1df0e-110">L’appel à `QueryInterface` réussit pour les objets managés qui dérivent de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1df0e-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1df0e-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="1df0e-111">Requirements</span></span>  
 <span data-ttu-id="1df0e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1df0e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1df0e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1df0e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1df0e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1df0e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1df0e-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1df0e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df0e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1df0e-116">See also</span></span>

- [<span data-ttu-id="1df0e-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1df0e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1df0e-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="1df0e-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
