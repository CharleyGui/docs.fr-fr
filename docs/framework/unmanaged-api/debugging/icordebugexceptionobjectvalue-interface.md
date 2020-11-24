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
ms.openlocfilehash: 6a0c33799b2b2aaa48e3b18b7b4bb37643508bd4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678881"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="36bd6-102">ICorDebugExceptionObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="36bd6-102">ICorDebugExceptionObjectValue Interface</span></span>

<span data-ttu-id="36bd6-103">Étend l’interface « ICorDebugObjectValue » pour fournir des informations de trace de la pile à partir d’un objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="36bd6-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36bd6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="36bd6-104">Methods</span></span>  
  
|<span data-ttu-id="36bd6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="36bd6-105">Method</span></span>|<span data-ttu-id="36bd6-106">Description</span><span class="sxs-lookup"><span data-stu-id="36bd6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36bd6-107">EnumerateExceptionCallStack, méthode</span><span class="sxs-lookup"><span data-stu-id="36bd6-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="36bd6-108">Obtient un énumérateur de la pile des appels incorporée dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="36bd6-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36bd6-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="36bd6-109">Remarks</span></span>  

 <span data-ttu-id="36bd6-110">L’appel à `QueryInterface` réussit pour les objets managés qui dérivent de <xref:System.Exception?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="36bd6-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36bd6-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="36bd6-111">Requirements</span></span>  

 <span data-ttu-id="36bd6-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36bd6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36bd6-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36bd6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36bd6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36bd6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36bd6-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36bd6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bd6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36bd6-116">See also</span></span>

- [<span data-ttu-id="36bd6-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="36bd6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="36bd6-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="36bd6-118">Debugging</span></span>](index.md)
