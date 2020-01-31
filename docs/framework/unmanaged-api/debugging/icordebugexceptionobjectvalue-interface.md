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
ms.openlocfilehash: fa154d0bb48f4ecd4fc6a50ce22fd13c592b7c40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782733"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="685ca-102">ICorDebugExceptionObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="685ca-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="685ca-103">Étend l’interface « ICorDebugObjectValue » pour fournir des informations de trace de la pile à partir d’un objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="685ca-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="685ca-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="685ca-104">Methods</span></span>  
  
|<span data-ttu-id="685ca-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="685ca-105">Method</span></span>|<span data-ttu-id="685ca-106">Description</span><span class="sxs-lookup"><span data-stu-id="685ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="685ca-107">EnumerateExceptionCallStack, méthode</span><span class="sxs-lookup"><span data-stu-id="685ca-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="685ca-108">Obtient un énumérateur de la pile des appels incorporée dans un objet exception.</span><span class="sxs-lookup"><span data-stu-id="685ca-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="685ca-109">Notes</span><span class="sxs-lookup"><span data-stu-id="685ca-109">Remarks</span></span>  
 <span data-ttu-id="685ca-110">L’appel à `QueryInterface` réussit pour les objets managés qui dérivent de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="685ca-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="685ca-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="685ca-111">Requirements</span></span>  
 <span data-ttu-id="685ca-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="685ca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="685ca-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="685ca-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="685ca-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="685ca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="685ca-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="685ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="685ca-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="685ca-116">See also</span></span>

- [<span data-ttu-id="685ca-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="685ca-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="685ca-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="685ca-118">Debugging</span></span>](index.md)
