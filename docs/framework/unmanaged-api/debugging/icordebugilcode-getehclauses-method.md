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
ms.openlocfilehash: ac9a4e4b54b302afeae4ede1dd574c15ded3ff12
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788600"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="e0231-102">ICorDebugILCode::GetEHClauses, méthode</span><span class="sxs-lookup"><span data-stu-id="e0231-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="e0231-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="e0231-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e0231-104">Retourne un pointeur vers une liste de clauses de gestion des exceptions qui sont définies pour ce langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="e0231-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0231-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0231-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0231-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e0231-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="e0231-107">[en entrée] La capacité de stockage du tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="e0231-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="e0231-108">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="e0231-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="e0231-109">[en sortie] Le nombre de clauses à propos desquelles des informations sont écrites dans le tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="e0231-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="e0231-110">clauses</span><span class="sxs-lookup"><span data-stu-id="e0231-110">clauses</span></span>  
 <span data-ttu-id="e0231-111">à Tableau d’objets [CorDebugEHClause](cordebugehclause-structure.md) qui contiennent des informations sur les clauses de gestion des exceptions définies pour ce langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="e0231-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0231-112">Notes</span><span class="sxs-lookup"><span data-stu-id="e0231-112">Remarks</span></span>  
 <span data-ttu-id="e0231-113">Si `cClauses` a la valeur 0 et que `pcClauses` est non**null**, `pcClauses` a pour valeur le nombre de clauses de gestion des exceptions disponibles.</span><span class="sxs-lookup"><span data-stu-id="e0231-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="e0231-114">Si `cClauses` est différent de zéro, il représente la capacité de stockage du tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="e0231-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="e0231-115">Quand la méthode se termine, `clauses` contient un maximum de `cClauses` éléments et `pcClauses` est défini avec le nombre de clauses réellement écrites dans le tableau `clauses`.</span><span class="sxs-lookup"><span data-stu-id="e0231-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0231-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e0231-116">Requirements</span></span>  
 <span data-ttu-id="e0231-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0231-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0231-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0231-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0231-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0231-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0231-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0231-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0231-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0231-121">See also</span></span>

- [<span data-ttu-id="e0231-122">ICorDebugILCode, interface</span><span class="sxs-lookup"><span data-stu-id="e0231-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="e0231-123">CorDebugEHClause, structure</span><span class="sxs-lookup"><span data-stu-id="e0231-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="e0231-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e0231-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
