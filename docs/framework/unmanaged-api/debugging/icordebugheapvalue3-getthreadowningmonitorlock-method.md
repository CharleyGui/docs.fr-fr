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
ms.openlocfilehash: fef0902aedbcd8572d2dc67fae7927f754af4489
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723309"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="3037b-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock, méthode</span><span class="sxs-lookup"><span data-stu-id="3037b-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>

<span data-ttu-id="3037b-103">Retourne le thread managé qui détient le verrou du moniteur sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="3037b-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3037b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3037b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3037b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3037b-105">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="3037b-106">à Thread managé qui possède le verrou du moniteur sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="3037b-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="3037b-107">à Nombre de fois que ce thread doit libérer le verrou avant qu’il ne soit plus propriétaire.</span><span class="sxs-lookup"><span data-stu-id="3037b-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3037b-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3037b-108">Return Value</span></span>  

 <span data-ttu-id="3037b-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3037b-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3037b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3037b-110">HRESULT</span></span>|<span data-ttu-id="3037b-111">Description</span><span class="sxs-lookup"><span data-stu-id="3037b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3037b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3037b-112">S_OK</span></span>|<span data-ttu-id="3037b-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="3037b-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="3037b-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3037b-114">S_FALSE</span></span>|<span data-ttu-id="3037b-115">Aucun thread managé ne possède le verrou du moniteur sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="3037b-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="3037b-116">Exceptions</span><span class="sxs-lookup"><span data-stu-id="3037b-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3037b-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="3037b-117">Remarks</span></span>  

 <span data-ttu-id="3037b-118">Si un thread managé possède le verrou du moniteur sur cet objet :</span><span class="sxs-lookup"><span data-stu-id="3037b-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="3037b-119">La méthode retourne S_OK.</span><span class="sxs-lookup"><span data-stu-id="3037b-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="3037b-120">L’objet thread est valide jusqu’à ce que le thread se termine.</span><span class="sxs-lookup"><span data-stu-id="3037b-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="3037b-121">Si aucun thread managé n’est propriétaire du verrou du moniteur sur cet objet, `ppThread` et que `pAcquisitionCount` la méthode retourne S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="3037b-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="3037b-122">Si `ppThread` ou `pAcquisitionCount` n’est pas un pointeur valide, le résultat n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="3037b-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="3037b-123">Si une erreur se produit et qu’il est impossible de déterminer le thread qui, le cas échéant, détient le verrou du moniteur sur cet objet, la méthode retourne un HRESULT qui indique un échec.</span><span class="sxs-lookup"><span data-stu-id="3037b-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3037b-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3037b-124">Requirements</span></span>  

 <span data-ttu-id="3037b-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3037b-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3037b-126">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3037b-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3037b-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3037b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3037b-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3037b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3037b-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3037b-129">See also</span></span>

- [<span data-ttu-id="3037b-130">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3037b-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3037b-131">Débogage</span><span class="sxs-lookup"><span data-stu-id="3037b-131">Debugging</span></span>](index.md)
