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
ms.openlocfilehash: 4e368b2c63e8e43b5c392bec4b79daac8bae249d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678532"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="560ad-102">ICorDebugThread4::HadUnhandledException, méthode</span><span class="sxs-lookup"><span data-stu-id="560ad-102">ICorDebugThread4::HadUnhandledException Method</span></span>

<span data-ttu-id="560ad-103">Indique si le thread a déjà eu une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="560ad-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="560ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="560ad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="560ad-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="560ad-105">Parameters</span></span>  

 `ppBlockingObjectEnum`  
 <span data-ttu-id="560ad-106">à Pointeur vers l’adresse d’une énumération ordonnée de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="560ad-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="560ad-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="560ad-107">Return Value</span></span>  

 <span data-ttu-id="560ad-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="560ad-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="560ad-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="560ad-109">HRESULT</span></span>|<span data-ttu-id="560ad-110">Description</span><span class="sxs-lookup"><span data-stu-id="560ad-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="560ad-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="560ad-111">S_OK</span></span>|<span data-ttu-id="560ad-112">Le thread a rencontré une exception non gérée depuis sa création.</span><span class="sxs-lookup"><span data-stu-id="560ad-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="560ad-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="560ad-113">S_FALSE</span></span>|<span data-ttu-id="560ad-114">Le thread n’a jamais eu d’exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="560ad-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="560ad-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="560ad-115">Remarks</span></span>  

 <span data-ttu-id="560ad-116">Cette méthode indique si le thread a déjà eu une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="560ad-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="560ad-117">Au moment où le rappel d’exception non gérée est déclenché ou que l’attachement JIT natif est initié, il est garanti que cette méthode retourne S_OK.</span><span class="sxs-lookup"><span data-stu-id="560ad-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="560ad-118">Il n’y a aucune garantie que la méthode [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) retourne l’exception non gérée ; Toutefois, si le processus n’a pas encore été poursuivi après avoir obtenu le rappel d’exception non gérée ou en cas d’attachement JIT natif.</span><span class="sxs-lookup"><span data-stu-id="560ad-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="560ad-119">En outre, il est possible (quoique improbable) d’avoir plusieurs threads avec une exception non gérée au moment où l’attachement JIT natif est déclenché.</span><span class="sxs-lookup"><span data-stu-id="560ad-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="560ad-120">Dans ce cas, il n’existe aucun moyen de déterminer l’exception qui a déclenché l’attachement JIT.</span><span class="sxs-lookup"><span data-stu-id="560ad-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="560ad-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="560ad-121">Requirements</span></span>  

 <span data-ttu-id="560ad-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="560ad-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="560ad-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="560ad-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="560ad-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="560ad-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="560ad-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="560ad-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="560ad-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="560ad-126">See also</span></span>

- [<span data-ttu-id="560ad-127">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="560ad-127">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="560ad-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="560ad-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="560ad-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="560ad-129">Debugging</span></span>](index.md)
