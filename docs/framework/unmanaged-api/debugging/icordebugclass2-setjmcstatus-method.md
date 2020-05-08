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
ms.openlocfilehash: 9fb2f960098e970b4d3d9f0be499f4d9fda6558e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893897"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="9f0fb-102">ICorDebugClass2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="9f0fb-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="9f0fb-103">Pour chaque méthode de la classe, définit une valeur qui indique si la méthode est du code défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9f0fb-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f0fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f0fb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f0fb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9f0fb-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="9f0fb-106">dans Affectez `true` la valeur pour indiquer que la méthode est du code défini par l’utilisateur ; Sinon, affectez `false`à la valeur.</span><span class="sxs-lookup"><span data-stu-id="9f0fb-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f0fb-107">Notes </span><span class="sxs-lookup"><span data-stu-id="9f0fb-107">Remarks</span></span>  
 <span data-ttu-id="9f0fb-108">Une exécution pas à pas juste-à-pas-code (uniquement mon code) ignore le code non défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9f0fb-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="9f0fb-109">Le code défini par l’utilisateur doit être un sous-ensemble du code pouvant être débogué.</span><span class="sxs-lookup"><span data-stu-id="9f0fb-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="9f0fb-110">`SetJMCStatus`retourne une valeur HRESULT de S_FALSE si elle ne parvient pas à définir la valeur d’une méthode, même si elle définit correctement la valeur pour toutes les autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="9f0fb-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f0fb-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9f0fb-111">Requirements</span></span>  
 <span data-ttu-id="9f0fb-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f0fb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f0fb-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f0fb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f0fb-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f0fb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f0fb-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f0fb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
