---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179063"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="c3b55-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="c3b55-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="c3b55-103">Obtient un enumérateur pour les types Windows Runtime en cache dans un domaine d’application basé sur leurs identifiants d’interface.</span><span class="sxs-lookup"><span data-stu-id="c3b55-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3b55-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b55-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3b55-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="c3b55-106">[dans] Le nombre de types requis.</span><span class="sxs-lookup"><span data-stu-id="c3b55-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="c3b55-107">[dans] Un pointeur vers un tableau qui contient les identifiants d’interface correspondant aux représentations gérées des types Windows Runtime à récupérer.</span><span class="sxs-lookup"><span data-stu-id="c3b55-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="c3b55-108">[out] Un pointeur à l’adresse d’un objet d’interface "ICorDebugTypeEnum" qui permet le recensement des représentations gérées `iidsToResolve`en cache des types Windows Runtime récupérés, en fonction des identifiants d’interface dans .</span><span class="sxs-lookup"><span data-stu-id="c3b55-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3b55-109">Notes </span><span class="sxs-lookup"><span data-stu-id="c3b55-109">Remarks</span></span>  
 <span data-ttu-id="c3b55-110">Si la méthode ne parvient pas à récupérer des informations pour un identifiant d’interface spécifique, l’entrée correspondante dans la collection "ICorDebugTypeEnum" aura un type d’erreurs dues à des problèmes de récupération de `ELEMENT_TYPE_END` données, ou `ELEMENT_TYPE_VOID` pour des identifiants d’interface inconnus.</span><span class="sxs-lookup"><span data-stu-id="c3b55-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b55-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c3b55-111">Requirements</span></span>  
 <span data-ttu-id="c3b55-112">**Plates-formes:** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="c3b55-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="c3b55-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3b55-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3b55-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3b55-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3b55-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b55-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b55-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3b55-116">See also</span></span>

- [<span data-ttu-id="c3b55-117">ICorDebugAppDomain3, interface</span><span class="sxs-lookup"><span data-stu-id="c3b55-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
