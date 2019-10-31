---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: ec265525d01dab0669939569501fce91b500a900
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127492"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="f664d-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock, méthode</span><span class="sxs-lookup"><span data-stu-id="f664d-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="f664d-103">Retourne le thread managé qui détient le verrou du moniteur sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="f664d-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f664d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f664d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f664d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f664d-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="f664d-106">à Thread managé qui possède le verrou du moniteur sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="f664d-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="f664d-107">à Nombre de fois que ce thread doit libérer le verrou avant qu’il ne soit plus propriétaire.</span><span class="sxs-lookup"><span data-stu-id="f664d-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f664d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f664d-108">Return Value</span></span>  
 <span data-ttu-id="f664d-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f664d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f664d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f664d-110">HRESULT</span></span>|<span data-ttu-id="f664d-111">Description</span><span class="sxs-lookup"><span data-stu-id="f664d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f664d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f664d-112">S_OK</span></span>|<span data-ttu-id="f664d-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="f664d-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f664d-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f664d-114">S_FALSE</span></span>|<span data-ttu-id="f664d-115">Aucun thread managé ne possède le verrou du moniteur sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="f664d-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f664d-116">Exceptions</span><span class="sxs-lookup"><span data-stu-id="f664d-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f664d-117">Notes</span><span class="sxs-lookup"><span data-stu-id="f664d-117">Remarks</span></span>  
 <span data-ttu-id="f664d-118">Si un thread managé possède le verrou du moniteur sur cet objet :</span><span class="sxs-lookup"><span data-stu-id="f664d-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="f664d-119">La méthode retourne S_OK.</span><span class="sxs-lookup"><span data-stu-id="f664d-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="f664d-120">L’objet thread est valide jusqu’à ce que le thread se termine.</span><span class="sxs-lookup"><span data-stu-id="f664d-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="f664d-121">Si aucun thread managé ne possède le verrou du moniteur sur cet objet, les `ppThread` et les `pAcquisitionCount` sont inchangés, et la méthode retourne S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="f664d-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="f664d-122">Si `ppThread` ou `pAcquisitionCount` n’est pas un pointeur valide, le résultat n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="f664d-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="f664d-123">Si une erreur se produit et qu’il est impossible de déterminer le thread qui, le cas échéant, détient le verrou du moniteur sur cet objet, la méthode retourne un HRESULT qui indique un échec.</span><span class="sxs-lookup"><span data-stu-id="f664d-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f664d-124">spécifications</span><span class="sxs-lookup"><span data-stu-id="f664d-124">Requirements</span></span>  
 <span data-ttu-id="f664d-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f664d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f664d-126">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f664d-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f664d-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f664d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f664d-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f664d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f664d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f664d-129">See also</span></span>

- [<span data-ttu-id="f664d-130">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f664d-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f664d-131">Débogage</span><span class="sxs-lookup"><span data-stu-id="f664d-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
