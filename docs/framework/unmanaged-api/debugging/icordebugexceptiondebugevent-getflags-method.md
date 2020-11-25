---
title: ICorDebugExceptionDebugEvent::GetFlags, méthode
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 02a20b54b7fecc711bda010c6916fe036cf20dd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729601"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="a1790-102">ICorDebugExceptionDebugEvent::GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="a1790-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>

<span data-ttu-id="a1790-103">Obtient un indicateur qui précise si l'exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="a1790-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1790-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1790-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1790-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1790-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="a1790-106">à Pointeur vers une valeur [CorDebugExceptionFlags,](cordebugexceptionflags-enumeration.md) qui indique si l’exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="a1790-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1790-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a1790-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1790-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a1790-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1790-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1790-109">Requirements</span></span>  

 <span data-ttu-id="a1790-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1790-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1790-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1790-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1790-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1790-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1790-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1790-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1790-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1790-114">See also</span></span>

- [<span data-ttu-id="a1790-115">ICorDebugExceptionDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="a1790-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="a1790-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a1790-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
