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
ms.openlocfilehash: cfa6df7a812559f05a4c57381a5007c9c90238e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709646"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="bbae9-102">ICorDebugModule2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="bbae9-102">ICorDebugModule2::SetJMCStatus Method</span></span>

<span data-ttu-id="bbae9-103">Affecte la valeur spécifiée à l’état Uniquement mon code (uniquement mon code) de toutes les méthodes de toutes les classes de ce ICorDebugModule2, à l’exception de celles du `pTokens` tableau, qu’il affecte à la valeur opposée.</span><span class="sxs-lookup"><span data-stu-id="bbae9-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbae9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbae9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbae9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bbae9-105">Parameters</span></span>  

 `bIsJustMycode`  
 <span data-ttu-id="bbae9-106">dans Affectez `true` la valeur si le code doit être débogué ; sinon, affectez à la valeur `false` .</span><span class="sxs-lookup"><span data-stu-id="bbae9-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="bbae9-107">[in] Taille du tableau `pTokens`.</span><span class="sxs-lookup"><span data-stu-id="bbae9-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="bbae9-108">dans Tableau de `mdToken` valeurs, dont chacune fait référence à une méthode dont l’état uniquement mon code est défini sur ! `bIsJustMycode` .</span><span class="sxs-lookup"><span data-stu-id="bbae9-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbae9-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="bbae9-109">Remarks</span></span>  

 <span data-ttu-id="bbae9-110">L’état uniquement mon code de chaque méthode spécifiée dans le `pTokens` tableau est défini sur le contraire de la `bIsJustMycode` valeur.</span><span class="sxs-lookup"><span data-stu-id="bbae9-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="bbae9-111">L’état de toutes les autres méthodes de ce module est défini sur la `bIsJustMycode` valeur.</span><span class="sxs-lookup"><span data-stu-id="bbae9-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="bbae9-112">La `SetJMCStatus` méthode efface tous les paramètres uniquement mon code précédents de ce module.</span><span class="sxs-lookup"><span data-stu-id="bbae9-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="bbae9-113">La `SetJMCStatus` méthode retourne un S_OK HRESULT si toutes les fonctions ont été correctement définies.</span><span class="sxs-lookup"><span data-stu-id="bbae9-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="bbae9-114">Elle retourne un CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT si certaines fonctions marquées ne `true` peuvent pas être déboguées.</span><span class="sxs-lookup"><span data-stu-id="bbae9-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbae9-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bbae9-115">Requirements</span></span>  

 <span data-ttu-id="bbae9-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbae9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbae9-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbae9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbae9-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbae9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbae9-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbae9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
