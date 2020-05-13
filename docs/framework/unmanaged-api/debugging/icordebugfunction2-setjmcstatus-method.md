---
title: ICorDebugFunction2::SetJMCStatus, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 7da12554ba1db9a467aa03c01bfb3b584125b129
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213190"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="ede22-102">ICorDebugFunction2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="ede22-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="ede22-103">Marque la fonction représentée par ce ICorDebugFunction2 pour Uniquement mon code pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ede22-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ede22-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ede22-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ede22-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="ede22-106">dans Affectez la valeur à pour `true` marquer la fonction en tant que code utilisateur ; sinon, affectez à la valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="ede22-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="ede22-107">Valeurs de retour</span><span class="sxs-lookup"><span data-stu-id="ede22-107">Return Values</span></span>  
  
|<span data-ttu-id="ede22-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ede22-108">HRESULT</span></span>|<span data-ttu-id="ede22-109">Description</span><span class="sxs-lookup"><span data-stu-id="ede22-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ede22-110">La fonction a été marquée avec succès.</span><span class="sxs-lookup"><span data-stu-id="ede22-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="ede22-111">La fonction n’a pas pu être marquée comme code utilisateur, car elle ne peut pas être déboguée.</span><span class="sxs-lookup"><span data-stu-id="ede22-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ede22-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="ede22-112">Remarks</span></span>  
 <span data-ttu-id="ede22-113">Une Uniquement mon code pas à pas permet d’ignorer le code non-utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ede22-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="ede22-114">Le code utilisateur doit être un sous-ensemble du code pouvant être débogué.</span><span class="sxs-lookup"><span data-stu-id="ede22-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede22-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ede22-115">Requirements</span></span>  
 <span data-ttu-id="ede22-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede22-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede22-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ede22-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ede22-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ede22-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ede22-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede22-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
