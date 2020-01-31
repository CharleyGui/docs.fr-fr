---
title: ICorDebugExceptionDebugEvent::GetFlags, méthode
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782917"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="254c7-102">ICorDebugExceptionDebugEvent::GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="254c7-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="254c7-103">Obtient un indicateur qui précise si l'exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="254c7-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="254c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="254c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="254c7-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="254c7-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="254c7-106">à Pointeur vers une valeur [CorDebugExceptionFlags,](cordebugexceptionflags-enumeration.md) qui indique si l’exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="254c7-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="254c7-107">Notes</span><span class="sxs-lookup"><span data-stu-id="254c7-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="254c7-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="254c7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="254c7-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="254c7-109">Requirements</span></span>  
 <span data-ttu-id="254c7-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="254c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="254c7-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="254c7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="254c7-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="254c7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="254c7-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="254c7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="254c7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="254c7-114">See also</span></span>

- [<span data-ttu-id="254c7-115">ICorDebugExceptionDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="254c7-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="254c7-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="254c7-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
