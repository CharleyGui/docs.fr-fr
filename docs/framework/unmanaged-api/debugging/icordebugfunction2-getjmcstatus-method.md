---
title: ICorDebugFunction2::GetJMCStatus, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 360434fe6e08804d8c80c4ea36d585209cc6761a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137821"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="2331c-102">ICorDebugFunction2::GetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="2331c-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="2331c-103">Obtient une valeur qui indique si la fonction représentée par cet objet ICorDebugFunction2 est marquée en tant que code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2331c-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2331c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2331c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2331c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2331c-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="2331c-106">à Pointeur vers une valeur booléenne qui est `true`, si cette fonction est marquée en tant que code utilisateur ; dans le cas contraire, la valeur est `false`.</span><span class="sxs-lookup"><span data-stu-id="2331c-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2331c-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2331c-107">Remarks</span></span>  
 <span data-ttu-id="2331c-108">Si la fonction représentée par cette `ICorDebugFunction2` ne peut pas être déboguée, `pbIsJustMyCode` sera toujours `false`.</span><span class="sxs-lookup"><span data-stu-id="2331c-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2331c-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="2331c-109">Requirements</span></span>  
 <span data-ttu-id="2331c-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2331c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2331c-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2331c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2331c-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2331c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2331c-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2331c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
