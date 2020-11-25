---
title: ICorDebugThread::GetAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
ms.openlocfilehash: 882176f381a7c5bc4a0297021b89a96948a1cea8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728067"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="03121-102">ICorDebugThread::GetAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="03121-102">ICorDebugThread::GetAppDomain Method</span></span>

<span data-ttu-id="03121-103">Obtient un pointeur d’interface vers le domaine d’application dans lequel ce ICorDebugThread est actuellement en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="03121-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03121-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03121-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03121-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="03121-105">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="03121-106">à Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel ce thread est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="03121-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03121-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="03121-107">Requirements</span></span>  

 <span data-ttu-id="03121-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03121-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03121-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03121-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03121-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03121-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03121-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03121-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
