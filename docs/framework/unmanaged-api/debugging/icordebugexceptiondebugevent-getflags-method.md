---
title: ICorDebugExceptionDebugEvent::GetFlags, méthode
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 5793d939c8497ef842f614048707f69faa8ac568
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976042"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="d8ed7-102">ICorDebugExceptionDebugEvent::GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="d8ed7-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="d8ed7-103">Obtient un indicateur qui précise si l'exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="d8ed7-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ed7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8ed7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8ed7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8ed7-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="d8ed7-106">à Pointeur vers une valeur [CorDebugExceptionFlags,](cordebugexceptionflags-enumeration.md) qui indique si l’exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="d8ed7-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ed7-107">Notes </span><span class="sxs-lookup"><span data-stu-id="d8ed7-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8ed7-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d8ed7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ed7-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d8ed7-109">Requirements</span></span>  
 <span data-ttu-id="d8ed7-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ed7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ed7-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8ed7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ed7-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ed7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ed7-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ed7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ed7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8ed7-114">See also</span></span>

- [<span data-ttu-id="d8ed7-115">ICorDebugExceptionDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="d8ed7-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="d8ed7-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d8ed7-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
