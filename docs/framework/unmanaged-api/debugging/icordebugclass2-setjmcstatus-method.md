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
ms.openlocfilehash: 1db2c9b5e65ae150f05242172f5ea16db433bbb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717823"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="d2b32-102">ICorDebugClass2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="d2b32-102">ICorDebugClass2::SetJMCStatus Method</span></span>

<span data-ttu-id="d2b32-103">Pour chaque méthode de la classe, définit une valeur qui indique si la méthode est du code défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2b32-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2b32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2b32-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2b32-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2b32-105">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="d2b32-106">dans Affectez `true` la valeur pour indiquer que la méthode est du code défini par l’utilisateur ; sinon, affectez à la valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="d2b32-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2b32-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="d2b32-107">Remarks</span></span>  

 <span data-ttu-id="d2b32-108">Une exécution pas à pas juste-à-pas-code (uniquement mon code) ignore le code non défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2b32-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="d2b32-109">Le code défini par l’utilisateur doit être un sous-ensemble du code pouvant être débogué.</span><span class="sxs-lookup"><span data-stu-id="d2b32-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="d2b32-110">`SetJMCStatus` retourne une valeur HRESULT de S_FALSE si elle ne parvient pas à définir la valeur d’une méthode, même si elle définit correctement la valeur pour toutes les autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="d2b32-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2b32-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2b32-111">Requirements</span></span>  

 <span data-ttu-id="d2b32-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2b32-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2b32-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2b32-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2b32-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2b32-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2b32-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2b32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
