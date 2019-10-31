---
title: ICorDebugManagedCallback::LoadModule, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: d13c5be314dc39f3e7b42a8d6b13f6a25751067d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130715"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="c3dc1-102">ICorDebugManagedCallback::LoadModule, méthode</span><span class="sxs-lookup"><span data-stu-id="c3dc1-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="c3dc1-103">Notifie le débogueur qu’un module common language runtime (CLR) a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="c3dc1-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3dc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3dc1-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3dc1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3dc1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c3dc1-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel le module a été chargé.</span><span class="sxs-lookup"><span data-stu-id="c3dc1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="c3dc1-107">dans Pointeur vers un objet ICorDebugModule qui représente le module CLR.</span><span class="sxs-lookup"><span data-stu-id="c3dc1-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3dc1-108">Notes</span><span class="sxs-lookup"><span data-stu-id="c3dc1-108">Remarks</span></span>  
 <span data-ttu-id="c3dc1-109">Le rappel `LoadModule` fournit un moment approprié pour examiner les métadonnées du module, définir des indicateurs de compilateur juste-à-temps (JIT) ou activer ou désactiver les rappels de chargement de classe pour le module.</span><span class="sxs-lookup"><span data-stu-id="c3dc1-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3dc1-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="c3dc1-110">Requirements</span></span>  
 <span data-ttu-id="c3dc1-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3dc1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3dc1-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3dc1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3dc1-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3dc1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3dc1-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3dc1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3dc1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3dc1-115">See also</span></span>

- [<span data-ttu-id="c3dc1-116">UnloadModule, méthode</span><span class="sxs-lookup"><span data-stu-id="c3dc1-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="c3dc1-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c3dc1-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
