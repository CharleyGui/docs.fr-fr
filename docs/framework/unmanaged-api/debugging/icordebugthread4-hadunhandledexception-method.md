---
title: ICorDebugThread4::HadUnhandledException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bbc3379ff9523564f4eae7da96fca2247601fcd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765155"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="8a9ef-102">ICorDebugThread4::HadUnhandledException, méthode</span><span class="sxs-lookup"><span data-stu-id="8a9ef-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="8a9ef-103">Indique si le thread a déjà eu une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a9ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a9ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a9ef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a9ef-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="8a9ef-106">[out] Un pointeur vers l’adresse d’une énumération ordonnée de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a9ef-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8a9ef-107">Return Value</span></span>  
 <span data-ttu-id="8a9ef-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8a9ef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a9ef-109">HRESULT</span></span>|<span data-ttu-id="8a9ef-110">Description</span><span class="sxs-lookup"><span data-stu-id="8a9ef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a9ef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a9ef-111">S_OK</span></span>|<span data-ttu-id="8a9ef-112">Le thread a eu une exception non gérée depuis sa création.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="8a9ef-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8a9ef-113">S_FALSE</span></span>|<span data-ttu-id="8a9ef-114">Le thread n’a jamais été une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a9ef-115">Notes</span><span class="sxs-lookup"><span data-stu-id="8a9ef-115">Remarks</span></span>  
 <span data-ttu-id="8a9ef-116">Cette méthode indique si le thread a déjà eu une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="8a9ef-117">Au moment où le rappel d’exception non gérée est déclenché ou natif JIT-attach est lancée, cette méthode renvoie toujours S_OK.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="8a9ef-118">Il n’existe aucune garantie que le [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) méthode retournera l’exception non gérée ; Cependant, cette opération si le processus n’a pas encore repris après avoir obtenu le rappel d’exception non gérée ou en cas de JIT natif.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="8a9ef-119">En outre, il est possible (bien qu’improbable) d’avoir plusieurs threads avec une exception non gérée au moment de JIT natif est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="8a9ef-120">Dans ce cas il n’existe aucun moyen pour déterminer quelle exception a déclenché la JIT-attach.</span><span class="sxs-lookup"><span data-stu-id="8a9ef-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a9ef-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a9ef-121">Requirements</span></span>  
 <span data-ttu-id="8a9ef-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a9ef-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a9ef-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a9ef-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a9ef-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a9ef-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a9ef-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a9ef-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9ef-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a9ef-126">See also</span></span>

- [<span data-ttu-id="8a9ef-127">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="8a9ef-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="8a9ef-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8a9ef-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8a9ef-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="8a9ef-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
