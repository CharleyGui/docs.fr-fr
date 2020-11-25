---
title: ICorDebugILCode::GetEHClauses, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: 38936a57944e9a0920c374f473c4cbe8e8d70abb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728665"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="38e28-102">ICorDebugILCode::GetEHClauses, méthode</span><span class="sxs-lookup"><span data-stu-id="38e28-102">ICorDebugILCode::GetEHClauses Method</span></span>

<span data-ttu-id="38e28-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="38e28-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="38e28-104">Retourne un pointeur vers une liste de clauses de gestion des exceptions qui sont définies pour ce langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="38e28-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e28-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38e28-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38e28-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38e28-106">Parameters</span></span>  

 `cClauses`  
 <span data-ttu-id="38e28-107">[en entrée] La capacité de stockage du tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="38e28-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="38e28-108">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="38e28-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="38e28-109">[en sortie] Le nombre de clauses à propos desquelles des informations sont écrites dans le tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="38e28-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="38e28-110">clauses</span><span class="sxs-lookup"><span data-stu-id="38e28-110">clauses</span></span>  
 <span data-ttu-id="38e28-111">à Tableau d’objets [CorDebugEHClause](cordebugehclause-structure.md) qui contiennent des informations sur les clauses de gestion des exceptions définies pour ce langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="38e28-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38e28-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="38e28-112">Remarks</span></span>  

 <span data-ttu-id="38e28-113">Si `cClauses` a la valeur 0 et que `pcClauses` est non **null**, `pcClauses` a pour valeur le nombre de clauses de gestion des exceptions disponibles.</span><span class="sxs-lookup"><span data-stu-id="38e28-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="38e28-114">Si `cClauses` est différent de zéro, il représente la capacité de stockage du tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="38e28-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="38e28-115">Quand la méthode se termine, `clauses` contient un maximum de `cClauses` éléments et `pcClauses` est défini avec le nombre de clauses réellement écrites dans le tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="38e28-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e28-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="38e28-116">Requirements</span></span>  

 <span data-ttu-id="38e28-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38e28-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e28-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38e28-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38e28-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38e28-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38e28-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38e28-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e28-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38e28-121">See also</span></span>

- [<span data-ttu-id="38e28-122">ICorDebugILCode, interface</span><span class="sxs-lookup"><span data-stu-id="38e28-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="38e28-123">CorDebugEHClause, structure</span><span class="sxs-lookup"><span data-stu-id="38e28-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="38e28-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="38e28-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
