---
title: ICorDebugManagedCallback::ExitAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: 51beed47e7187d6fa22e60baed16598a8ad73adb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688989"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="13411-102">ICorDebugManagedCallback::ExitAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="13411-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>

<span data-ttu-id="13411-103">Notifie le débogueur qu’un domaine d’application s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="13411-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13411-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13411-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13411-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="13411-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="13411-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus qui contient le domaine d’application donné.</span><span class="sxs-lookup"><span data-stu-id="13411-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="13411-107">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="13411-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13411-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="13411-108">Requirements</span></span>  

 <span data-ttu-id="13411-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13411-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13411-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13411-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13411-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13411-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13411-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13411-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13411-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13411-113">See also</span></span>

- [<span data-ttu-id="13411-114">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="13411-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
