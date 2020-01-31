---
title: ICorDebugManagedCallback::UnloadAssembly, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 06c08499298656c8314d72667d9dac88c8d11e6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788340"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="32ec0-102">ICorDebugManagedCallback::UnloadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="32ec0-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="32ec0-103">Notifie le débogueur qu’un assembly de common language runtime a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="32ec0-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ec0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32ec0-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32ec0-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="32ec0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="32ec0-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contenait l’assembly.</span><span class="sxs-lookup"><span data-stu-id="32ec0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="32ec0-107">dans Pointeur vers un objet ICorDebugAssembly qui représente l’assembly.</span><span class="sxs-lookup"><span data-stu-id="32ec0-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32ec0-108">Notes</span><span class="sxs-lookup"><span data-stu-id="32ec0-108">Remarks</span></span>  
 <span data-ttu-id="32ec0-109">L’assembly ne doit pas être utilisé après ce rappel.</span><span class="sxs-lookup"><span data-stu-id="32ec0-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ec0-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="32ec0-110">Requirements</span></span>  
 <span data-ttu-id="32ec0-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32ec0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32ec0-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32ec0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32ec0-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32ec0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32ec0-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32ec0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ec0-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32ec0-115">See also</span></span>

- [<span data-ttu-id="32ec0-116">LoadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="32ec0-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="32ec0-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="32ec0-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
