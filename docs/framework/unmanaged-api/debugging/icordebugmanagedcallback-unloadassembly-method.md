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
ms.openlocfilehash: 07996a78d7f559de587c8a3eb2babfc06675169d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212644"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="be4f5-102">ICorDebugManagedCallback::UnloadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="be4f5-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="be4f5-103">Notifie le débogueur qu’un assembly de common language runtime a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="be4f5-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be4f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be4f5-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be4f5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be4f5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="be4f5-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contenait l’assembly.</span><span class="sxs-lookup"><span data-stu-id="be4f5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="be4f5-107">dans Pointeur vers un objet ICorDebugAssembly qui représente l’assembly.</span><span class="sxs-lookup"><span data-stu-id="be4f5-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be4f5-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="be4f5-108">Remarks</span></span>  
 <span data-ttu-id="be4f5-109">L’assembly ne doit pas être utilisé après ce rappel.</span><span class="sxs-lookup"><span data-stu-id="be4f5-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be4f5-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="be4f5-110">Requirements</span></span>  
 <span data-ttu-id="be4f5-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be4f5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be4f5-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be4f5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be4f5-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be4f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be4f5-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be4f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be4f5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be4f5-115">See also</span></span>

- [<span data-ttu-id="be4f5-116">LoadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="be4f5-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="be4f5-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="be4f5-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
