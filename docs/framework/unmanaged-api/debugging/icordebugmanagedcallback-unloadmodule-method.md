---
title: ICorDebugManagedCallback::UnloadModule, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: 4b44a16d143c1daea1ea6c36eb096ab9a937b272
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210040"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="0ba9d-102">ICorDebugManagedCallback::UnloadModule, méthode</span><span class="sxs-lookup"><span data-stu-id="0ba9d-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="0ba9d-103">Notifie le débogueur qu’un module de common language runtime (DLL) a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="0ba9d-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ba9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ba9d-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ba9d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0ba9d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0ba9d-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contenait le module.</span><span class="sxs-lookup"><span data-stu-id="0ba9d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="0ba9d-107">dans Pointeur vers un objet ICorDebugModule qui représente le module.</span><span class="sxs-lookup"><span data-stu-id="0ba9d-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ba9d-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0ba9d-108">Remarks</span></span>  
 <span data-ttu-id="0ba9d-109">Le module ne doit pas être utilisé après cet appel.</span><span class="sxs-lookup"><span data-stu-id="0ba9d-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ba9d-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0ba9d-110">Requirements</span></span>  
 <span data-ttu-id="0ba9d-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ba9d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ba9d-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ba9d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ba9d-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ba9d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ba9d-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ba9d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba9d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ba9d-115">See also</span></span>

- [<span data-ttu-id="0ba9d-116">LoadModule, méthode</span><span class="sxs-lookup"><span data-stu-id="0ba9d-116">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="0ba9d-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="0ba9d-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
