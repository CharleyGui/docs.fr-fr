---
title: ICorDebugClass2::SetJMCStatus, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23f248625753c15a4798ea69a1eb3b377b79f95d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747755"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="1e7f9-102">ICorDebugClass2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="1e7f9-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="1e7f9-103">Pour chaque méthode de la classe, définit une valeur qui indique si la méthode est un code défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1e7f9-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e7f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e7f9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e7f9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1e7f9-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="1e7f9-106">[in] La valeur `true` pour indiquer que la méthode est défini par l’utilisateur de code ; sinon, la valeur est `false`.</span><span class="sxs-lookup"><span data-stu-id="1e7f9-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e7f9-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1e7f9-107">Remarks</span></span>  
 <span data-ttu-id="1e7f9-108">Un juste mon code (JMC) ignorera le code non défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1e7f9-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="1e7f9-109">Code défini par l’utilisateur doit être un sous-ensemble de code pouvant être débogué.</span><span class="sxs-lookup"><span data-stu-id="1e7f9-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="1e7f9-110">`SetJMCStatus` Retourne une valeur HRESULT de S_FALSE si elle ne parvient pas à définir la valeur de n’importe quelle méthode, même si la valeur pour toutes les autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="1e7f9-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e7f9-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1e7f9-111">Requirements</span></span>  
 <span data-ttu-id="1e7f9-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e7f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e7f9-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e7f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e7f9-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e7f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e7f9-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e7f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
