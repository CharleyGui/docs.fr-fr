---
title: ICorDebugValueBreakpoint::GetValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type:
- apiref
ms.openlocfilehash: 8b0ab22d4a782bb21e09d29c9121ef83782a4571
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722321"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="77c42-102">ICorDebugValueBreakpoint::GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="77c42-102">ICorDebugValueBreakpoint::GetValue Method</span></span>

<span data-ttu-id="77c42-103">Obtient un pointeur d’interface vers un objet « ICorDebugValue » qui représente la valeur de l’objet sur lequel le point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="77c42-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77c42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77c42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77c42-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="77c42-105">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="77c42-106">à Pointeur vers l’adresse d’un `ICorDebugValue` objet.</span><span class="sxs-lookup"><span data-stu-id="77c42-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77c42-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="77c42-107">Requirements</span></span>  

 <span data-ttu-id="77c42-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77c42-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77c42-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77c42-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77c42-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77c42-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77c42-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77c42-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c42-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77c42-112">See also</span></span>
