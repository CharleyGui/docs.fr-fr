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
ms.openlocfilehash: 8e4f745440936a39e22faf60d10a05a0bb110606
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975951"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="41c4f-102">ICorDebugExceptionObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="41c4f-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="41c4f-103">Étend l’interface « ICorDebugObjectValue » pour fournir des informations de trace de la pile à partir d’un objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="41c4f-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41c4f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="41c4f-104">Methods</span></span>  
  
|<span data-ttu-id="41c4f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="41c4f-105">Method</span></span>|<span data-ttu-id="41c4f-106">Description</span><span class="sxs-lookup"><span data-stu-id="41c4f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41c4f-107">EnumerateExceptionCallStack, méthode</span><span class="sxs-lookup"><span data-stu-id="41c4f-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="41c4f-108">Obtient un énumérateur de la pile des appels incorporée dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="41c4f-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c4f-109">Notes </span><span class="sxs-lookup"><span data-stu-id="41c4f-109">Remarks</span></span>  
 <span data-ttu-id="41c4f-110">L’appel à `QueryInterface` réussit pour les objets managés qui <xref:System.Exception?displayProperty=nameWithType>dérivent de.</span><span class="sxs-lookup"><span data-stu-id="41c4f-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c4f-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="41c4f-111">Requirements</span></span>  
 <span data-ttu-id="41c4f-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c4f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c4f-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41c4f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41c4f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41c4f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41c4f-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c4f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c4f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41c4f-116">See also</span></span>

- [<span data-ttu-id="41c4f-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="41c4f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="41c4f-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="41c4f-118">Debugging</span></span>](index.md)
