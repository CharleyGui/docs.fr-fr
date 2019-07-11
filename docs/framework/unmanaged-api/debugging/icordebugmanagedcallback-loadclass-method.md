---
title: ICorDebugManagedCallback::LoadClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5619dea17b9a7140238fd559d2f6b1a5d190ac33
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761895"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="61005-102">ICorDebugManagedCallback::LoadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="61005-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="61005-103">Notifie le débogueur qu’une classe a été chargée.</span><span class="sxs-lookup"><span data-stu-id="61005-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61005-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61005-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61005-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61005-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="61005-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel la classe a été chargée.</span><span class="sxs-lookup"><span data-stu-id="61005-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="61005-107">[in] Pointeur vers un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="61005-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61005-108">Notes</span><span class="sxs-lookup"><span data-stu-id="61005-108">Remarks</span></span>  
 <span data-ttu-id="61005-109">Ce rappel se produit uniquement si le chargement de classe a été activé pour le module qui contient la classe.</span><span class="sxs-lookup"><span data-stu-id="61005-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="61005-110">Le chargement de classe est toujours activé pour les modules dynamiques.</span><span class="sxs-lookup"><span data-stu-id="61005-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="61005-111">Le `LoadClass` rappel fournit un bon moment pour lier des points d’arrêt pour les classes qui vient d’être générées dans les modules dynamiques.</span><span class="sxs-lookup"><span data-stu-id="61005-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61005-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="61005-112">Requirements</span></span>  
 <span data-ttu-id="61005-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61005-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61005-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61005-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61005-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61005-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61005-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61005-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61005-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61005-117">See also</span></span>

- [<span data-ttu-id="61005-118">UnloadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="61005-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="61005-119">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="61005-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
