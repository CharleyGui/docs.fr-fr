---
title: ICorDebugModule2::SetJMCStatus, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d438123dcefb901098954845596c210e5b76cea6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764105"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="17cf1-102">ICorDebugModule2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="17cf1-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="17cf1-103">Définit l’état d’uniquement mon Code (JMC) de toutes les méthodes de toutes les classes dans ce ICorDebugModule2 à la valeur spécifiée, à l’exception de celles figurant dans le `pTokens` tableau, il définit la valeur opposée.</span><span class="sxs-lookup"><span data-stu-id="17cf1-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17cf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17cf1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17cf1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17cf1-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="17cf1-106">[in] La valeur `true` si le code doit être débogué ; sinon, la valeur est `false`.</span><span class="sxs-lookup"><span data-stu-id="17cf1-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="17cf1-107">[in] Taille du tableau `pTokens`.</span><span class="sxs-lookup"><span data-stu-id="17cf1-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="17cf1-108">[in] Un tableau de `mdToken` valeurs, chacune d’elles fait référence à une méthode qui auront leur état JMC défini sur !`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="17cf1-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17cf1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="17cf1-109">Remarks</span></span>  
 <span data-ttu-id="17cf1-110">L’état JMC de chaque méthode qui est spécifiée dans le `pTokens` tableau est défini à l’opposé de la `bIsJustMycode` valeur.</span><span class="sxs-lookup"><span data-stu-id="17cf1-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="17cf1-111">L’état de toutes les autres méthodes dans ce module est défini sur le `bIsJustMycode` valeur.</span><span class="sxs-lookup"><span data-stu-id="17cf1-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="17cf1-112">Le `SetJMCStatus` méthode efface tous les paramètres JMC précédents dans ce module.</span><span class="sxs-lookup"><span data-stu-id="17cf1-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="17cf1-113">Le `SetJMCStatus` méthode retourne une valeur S_OK HRESULT si toutes les fonctions ont été définies correctement.</span><span class="sxs-lookup"><span data-stu-id="17cf1-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="17cf1-114">Elle retourne un HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE si certaines fonctions sont marquées `true` ne sont pas pouvant être débogué.</span><span class="sxs-lookup"><span data-stu-id="17cf1-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17cf1-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17cf1-115">Requirements</span></span>  
 <span data-ttu-id="17cf1-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17cf1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17cf1-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17cf1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17cf1-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17cf1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17cf1-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17cf1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
