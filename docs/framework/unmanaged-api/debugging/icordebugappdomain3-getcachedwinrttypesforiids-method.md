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
ms.openlocfilehash: 2aff86fb63b87869ed13028bd7344afe11363f51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723179"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="01f36-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="01f36-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>

<span data-ttu-id="01f36-103">Obtient un énumérateur pour les types de Windows Runtime mis en cache dans un domaine d’application en fonction de leurs identificateurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="01f36-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01f36-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f36-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01f36-105">Parameters</span></span>  

 `cReqTypes`  
 <span data-ttu-id="01f36-106">dans Nombre de types requis.</span><span class="sxs-lookup"><span data-stu-id="01f36-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="01f36-107">dans Pointeur vers un tableau qui contient les identificateurs d’interface correspondant aux représentations managées des types de Windows Runtime à récupérer.</span><span class="sxs-lookup"><span data-stu-id="01f36-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="01f36-108">à Pointeur vers l’adresse d’un objet d’interface « ICorDebugTypeEnum » qui permet l’énumération des représentations managées mises en cache des types de Windows Runtime récupérés, en fonction des identificateurs d’interface dans `iidsToResolve` .</span><span class="sxs-lookup"><span data-stu-id="01f36-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01f36-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="01f36-109">Remarks</span></span>  

 <span data-ttu-id="01f36-110">Si la méthode ne parvient pas à récupérer des informations pour un identificateur d’interface spécifique, l’entrée correspondante dans la collection « ICorDebugTypeEnum » aura un type d' `ELEMENT_TYPE_END` erreurs en raison des problèmes de récupération de données ou `ELEMENT_TYPE_VOID` des identificateurs d’interface inconnus.</span><span class="sxs-lookup"><span data-stu-id="01f36-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f36-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="01f36-111">Requirements</span></span>  

 <span data-ttu-id="01f36-112">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="01f36-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="01f36-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01f36-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01f36-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01f36-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01f36-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f36-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f36-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01f36-116">See also</span></span>

- [<span data-ttu-id="01f36-117">ICorDebugAppDomain3, interface</span><span class="sxs-lookup"><span data-stu-id="01f36-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
