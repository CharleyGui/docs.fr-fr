---
title: ICorDebugManagedCallback::UnloadClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: f2f19987d22502acbe06bd5e5c14b0d6c17cbe24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781583"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="ee5a2-102">ICorDebugManagedCallback::UnloadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="ee5a2-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="ee5a2-103">Notifie le débogueur qu’une classe est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="ee5a2-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee5a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee5a2-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee5a2-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="ee5a2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ee5a2-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la classe.</span><span class="sxs-lookup"><span data-stu-id="ee5a2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="ee5a2-107">dans Pointeur vers un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="ee5a2-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee5a2-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ee5a2-108">Remarks</span></span>  
 <span data-ttu-id="ee5a2-109">La classe ne doit pas être référencée après cet appel.</span><span class="sxs-lookup"><span data-stu-id="ee5a2-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee5a2-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ee5a2-110">Requirements</span></span>  
 <span data-ttu-id="ee5a2-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee5a2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee5a2-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee5a2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee5a2-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee5a2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee5a2-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee5a2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5a2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee5a2-115">See also</span></span>

- [<span data-ttu-id="ee5a2-116">LoadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="ee5a2-116">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="ee5a2-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ee5a2-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
