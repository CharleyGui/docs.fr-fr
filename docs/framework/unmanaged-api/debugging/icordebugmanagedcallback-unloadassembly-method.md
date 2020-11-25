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
ms.openlocfilehash: e89b425afb63de8ef496fe545873ce33e5ff828c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724011"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="30b25-102">ICorDebugManagedCallback::UnloadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="30b25-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>

<span data-ttu-id="30b25-103">Notifie le débogueur qu’un assembly de common language runtime a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="30b25-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30b25-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30b25-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30b25-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="30b25-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contenait l’assembly.</span><span class="sxs-lookup"><span data-stu-id="30b25-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="30b25-107">dans Pointeur vers un objet ICorDebugAssembly qui représente l’assembly.</span><span class="sxs-lookup"><span data-stu-id="30b25-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30b25-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="30b25-108">Remarks</span></span>  

 <span data-ttu-id="30b25-109">L’assembly ne doit pas être utilisé après ce rappel.</span><span class="sxs-lookup"><span data-stu-id="30b25-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b25-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="30b25-110">Requirements</span></span>  

 <span data-ttu-id="30b25-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30b25-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b25-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30b25-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30b25-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30b25-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30b25-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b25-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b25-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30b25-115">See also</span></span>

- [<span data-ttu-id="30b25-116">LoadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="30b25-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="30b25-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="30b25-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
