---
title: ICorDebugFunction2::GetVersionNumber, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: 88fb205235cfaf3566fbd74b05a4e9833058f4a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696095"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="4bfab-102">ICorDebugFunction2::GetVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="4bfab-102">ICorDebugFunction2::GetVersionNumber Method</span></span>

<span data-ttu-id="4bfab-103">Obtient la version modifier & continuer de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="4bfab-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bfab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bfab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bfab-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4bfab-105">Parameters</span></span>  

 `pnVersion`  
 <span data-ttu-id="4bfab-106">à Pointeur vers un entier qui est le numéro de version de la fonction représentée par cet objet ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="4bfab-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bfab-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="4bfab-107">Remarks</span></span>  

 <span data-ttu-id="4bfab-108">Le Runtime effectue le suivi du nombre de modifications apportées à chaque module pendant une session de débogage.</span><span class="sxs-lookup"><span data-stu-id="4bfab-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="4bfab-109">Le numéro de version d’une fonction est un nombre de fois supérieur au numéro de la modification qui a introduit la fonction.</span><span class="sxs-lookup"><span data-stu-id="4bfab-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="4bfab-110">La version d’origine de la fonction est la version 1.</span><span class="sxs-lookup"><span data-stu-id="4bfab-110">The function's original version is version 1.</span></span> <span data-ttu-id="4bfab-111">Le nombre est incrémenté pour un module chaque fois que [ICorDebugModule2 :: ApplyChanges](icordebugmodule2-applychanges-method.md) est appelé sur ce module.</span><span class="sxs-lookup"><span data-stu-id="4bfab-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="4bfab-112">Ainsi, si le corps d’une fonction a été remplacé dans le premier et le troisième appel à `ICorDebugModule2::ApplyChanges` , `GetVersionNumber` peut retourner la version 1, 2 ou 4 pour cette fonction, mais pas la version 3.</span><span class="sxs-lookup"><span data-stu-id="4bfab-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="4bfab-113">(Cette fonction n’aurait pas de version 3.)</span><span class="sxs-lookup"><span data-stu-id="4bfab-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="4bfab-114">Le numéro de version est suivi séparément pour chaque module.</span><span class="sxs-lookup"><span data-stu-id="4bfab-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="4bfab-115">Par conséquent, si vous effectuez quatre modifications sur le module 1 et aucune sur le module 2, la modification suivante du module 1 affecte un numéro de version 6 à toutes les fonctions modifiées dans le module 1.</span><span class="sxs-lookup"><span data-stu-id="4bfab-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="4bfab-116">Si la même modification touche le module 2, les fonctions du module 2 obtiennent le numéro de version 2.</span><span class="sxs-lookup"><span data-stu-id="4bfab-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="4bfab-117">Le numéro de version obtenu par la `GetVersionNumber` méthode peut être inférieur à celui obtenu par [ICorDebugFunction :: GetCurrentVersionNumber,](icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="4bfab-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="4bfab-118">La méthode [ICorDebugCode :: GetVersionNumber](icordebugcode-getversionnumber-method.md) effectue la même opération que `ICorDebugFunction2::GetVersionNumber` .</span><span class="sxs-lookup"><span data-stu-id="4bfab-118">The [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bfab-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4bfab-119">Requirements</span></span>  

 <span data-ttu-id="4bfab-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bfab-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bfab-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bfab-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bfab-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bfab-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bfab-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bfab-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
