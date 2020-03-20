---
title: ICorDebugDataTarget2::EnumerateThreadIDs, méthode
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 120a970aac33b1ab06ae47335a959d2791f893ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178978"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="0f878-102">ICorDebugDataTarget2::EnumerateThreadIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="0f878-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="0f878-103">Retourne une liste des ID de threads actifs.</span><span class="sxs-lookup"><span data-stu-id="0f878-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f878-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f878-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f878-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f878-105">Parameters</span></span>  
 <span data-ttu-id="0f878-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="0f878-106">cThreadIDs</span></span>  
 <span data-ttu-id="0f878-107">[in] Nombre maximal de threads dont les ID peuvent être retournés.</span><span class="sxs-lookup"><span data-stu-id="0f878-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="0f878-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="0f878-108">pcThreadIds</span></span>  
 <span data-ttu-id="0f878-109">[out] Pointeur vers un `ULONG32` qui indique le nombre réel d'ID de threads ayant été écrits dans le tableau `pThreadIds`.</span><span class="sxs-lookup"><span data-stu-id="0f878-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="0f878-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="0f878-110">pThreadIDs</span></span>  
 <span data-ttu-id="0f878-111">Tableau d'identificateurs de threads.</span><span class="sxs-lookup"><span data-stu-id="0f878-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f878-112">Notes </span><span class="sxs-lookup"><span data-stu-id="0f878-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f878-113">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0f878-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f878-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0f878-114">Requirements</span></span>  
 <span data-ttu-id="0f878-115">**Plates-formes:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md). **En-tête:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f878-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f878-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f878-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f878-117">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f878-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f878-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f878-118">See also</span></span>

- [<span data-ttu-id="0f878-119">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="0f878-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="0f878-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0f878-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
