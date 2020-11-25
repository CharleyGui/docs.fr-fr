---
title: ICorDebugManagedCallback::NameChange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 0307ad5794d641833c2da1a1674e455ebff24861
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726520"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="6fe40-102">ICorDebugManagedCallback::NameChange, méthode</span><span class="sxs-lookup"><span data-stu-id="6fe40-102">ICorDebugManagedCallback::NameChange Method</span></span>

<span data-ttu-id="6fe40-103">Notifie le débogueur que le nom d’un domaine d’application ou d’un thread a changé.</span><span class="sxs-lookup"><span data-stu-id="6fe40-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fe40-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fe40-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6fe40-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="6fe40-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dont le nom a été modifié ou qui contient le thread qui a subi un changement de nom.</span><span class="sxs-lookup"><span data-stu-id="6fe40-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6fe40-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread dont le nom a été modifié.</span><span class="sxs-lookup"><span data-stu-id="6fe40-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fe40-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6fe40-108">Requirements</span></span>  

 <span data-ttu-id="6fe40-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fe40-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fe40-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fe40-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fe40-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fe40-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fe40-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fe40-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe40-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fe40-113">See also</span></span>

- [<span data-ttu-id="6fe40-114">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="6fe40-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
