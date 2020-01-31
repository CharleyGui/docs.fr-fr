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
ms.openlocfilehash: 8b259636a8bd28abd3bba12c4a05dda3c13557e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784888"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="917a3-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="917a3-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="917a3-103">Obtient un énumérateur pour les types de Windows Runtime mis en cache dans un domaine d’application en fonction de leurs identificateurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="917a3-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="917a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="917a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="917a3-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="917a3-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="917a3-106">dans Nombre de types requis.</span><span class="sxs-lookup"><span data-stu-id="917a3-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="917a3-107">dans Pointeur vers un tableau qui contient les identificateurs d’interface correspondant aux représentations managées des types de Windows Runtime à récupérer.</span><span class="sxs-lookup"><span data-stu-id="917a3-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="917a3-108">à Pointeur vers l’adresse d’un objet d’interface « ICorDebugTypeEnum » qui permet l’énumération des représentations managées mises en cache des types de Windows Runtime récupérés, en fonction des identificateurs d’interface dans `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="917a3-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="917a3-109">Notes</span><span class="sxs-lookup"><span data-stu-id="917a3-109">Remarks</span></span>  
 <span data-ttu-id="917a3-110">Si la méthode ne parvient pas à récupérer des informations pour un identificateur d’interface spécifique, l’entrée correspondante dans la collection « ICorDebugTypeEnum » aura un type de `ELEMENT_TYPE_END` pour les erreurs dues à des problèmes de récupération de données, ou `ELEMENT_TYPE_VOID` pour des identificateurs d’interface inconnus.</span><span class="sxs-lookup"><span data-stu-id="917a3-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="917a3-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="917a3-111">Requirements</span></span>  
 <span data-ttu-id="917a3-112">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="917a3-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="917a3-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="917a3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="917a3-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="917a3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="917a3-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="917a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="917a3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="917a3-116">See also</span></span>

- [<span data-ttu-id="917a3-117">ICorDebugAppDomain3, interface</span><span class="sxs-lookup"><span data-stu-id="917a3-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
