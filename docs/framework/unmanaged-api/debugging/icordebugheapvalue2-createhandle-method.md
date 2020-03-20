---
title: ICorDebugHeapValue2::CreateHandle, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178876"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="90a28-102">ICorDebugHeapValue2::CreateHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="90a28-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="90a28-103">Crée une poignée du type spécifié pour la valeur de tas représentée par cet objet ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="90a28-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90a28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90a28-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90a28-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90a28-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="90a28-106">[dans] Une valeur du recensement CorDebugHandleType qui spécifie le type de poignée à créer.</span><span class="sxs-lookup"><span data-stu-id="90a28-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="90a28-107">[out] Un pointeur à l’adresse d’un objet ICorDebugHandleValue qui représente la nouvelle poignée pour cette valeur de tas.</span><span class="sxs-lookup"><span data-stu-id="90a28-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90a28-108">Notes </span><span class="sxs-lookup"><span data-stu-id="90a28-108">Remarks</span></span>  
 <span data-ttu-id="90a28-109">La poignée sera créée dans le domaine de l’application qui est associée à la valeur du tas, et deviendra invalide si le domaine d’application est déchargé.</span><span class="sxs-lookup"><span data-stu-id="90a28-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="90a28-110">Plusieurs appels à cette fonction pour la même valeur de tas créeront plusieurs poignées.</span><span class="sxs-lookup"><span data-stu-id="90a28-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="90a28-111">Étant donné que les poignées affectent la performance du éboueur, le débagénaire devrait se limiter à un nombre relativement faible de poignées (environ 256) qui sont actives à la fois.</span><span class="sxs-lookup"><span data-stu-id="90a28-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90a28-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="90a28-112">Requirements</span></span>  
 <span data-ttu-id="90a28-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90a28-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90a28-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90a28-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90a28-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90a28-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90a28-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90a28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
