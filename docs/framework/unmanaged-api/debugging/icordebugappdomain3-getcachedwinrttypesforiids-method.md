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
ms.openlocfilehash: 0369cc6d98736542b764e5914d733a9341753b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088876"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="3bd0c-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="3bd0c-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="3bd0c-103">Obtient un énumérateur pour les types de Windows Runtime mis en cache dans un domaine d’application en fonction de leurs identificateurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="3bd0c-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bd0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bd0c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bd0c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3bd0c-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="3bd0c-106">dans Nombre de types requis.</span><span class="sxs-lookup"><span data-stu-id="3bd0c-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="3bd0c-107">dans Pointeur vers un tableau qui contient les identificateurs d’interface correspondant aux représentations managées des types de Windows Runtime à récupérer.</span><span class="sxs-lookup"><span data-stu-id="3bd0c-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="3bd0c-108">à Pointeur vers l’adresse d’un objet d’interface « ICorDebugTypeEnum » qui permet l’énumération des représentations managées mises en cache des types de Windows Runtime récupérés, en fonction des identificateurs d’interface dans `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="3bd0c-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bd0c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="3bd0c-109">Remarks</span></span>  
 <span data-ttu-id="3bd0c-110">Si la méthode ne parvient pas à récupérer des informations pour un identificateur d’interface spécifique, l’entrée correspondante dans la collection « ICorDebugTypeEnum » aura un type de `ELEMENT_TYPE_END` pour les erreurs dues à des problèmes de récupération de données, ou `ELEMENT_TYPE_VOID` pour des identificateurs d’interface inconnus.</span><span class="sxs-lookup"><span data-stu-id="3bd0c-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bd0c-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="3bd0c-111">Requirements</span></span>  
 <span data-ttu-id="3bd0c-112">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="3bd0c-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="3bd0c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bd0c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bd0c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bd0c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bd0c-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bd0c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd0c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bd0c-116">See also</span></span>

- [<span data-ttu-id="3bd0c-117">ICorDebugAppDomain3, interface</span><span class="sxs-lookup"><span data-stu-id="3bd0c-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
