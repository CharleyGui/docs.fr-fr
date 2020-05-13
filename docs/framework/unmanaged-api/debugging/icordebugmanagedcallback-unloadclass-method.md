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
ms.openlocfilehash: a7b71170f58ddfe0295da28b8c9fc73286b074e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212267"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="7106e-102">ICorDebugManagedCallback::UnloadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="7106e-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="7106e-103">Notifie le débogueur qu’une classe est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="7106e-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7106e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7106e-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7106e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7106e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7106e-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la classe.</span><span class="sxs-lookup"><span data-stu-id="7106e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="7106e-107">dans Pointeur vers un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="7106e-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7106e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="7106e-108">Remarks</span></span>  
 <span data-ttu-id="7106e-109">La classe ne doit pas être référencée après cet appel.</span><span class="sxs-lookup"><span data-stu-id="7106e-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7106e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7106e-110">Requirements</span></span>  
 <span data-ttu-id="7106e-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7106e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7106e-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7106e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7106e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7106e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7106e-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7106e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7106e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7106e-115">See also</span></span>

- [<span data-ttu-id="7106e-116">LoadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="7106e-116">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="7106e-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="7106e-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
