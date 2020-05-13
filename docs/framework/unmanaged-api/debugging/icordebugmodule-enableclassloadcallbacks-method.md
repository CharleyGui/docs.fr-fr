---
title: ICorDebugModule::EnableClassLoadCallbacks, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: 1ca3adf30ad633fcfb10a4b43a435698d2899597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213528"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="c04ff-102">ICorDebugModule::EnableClassLoadCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="c04ff-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="c04ff-103">Contrôle si les rappels [ICorDebugManagedCallback :: LoadClass](icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback :: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.</span><span class="sxs-lookup"><span data-stu-id="c04ff-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c04ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c04ff-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c04ff-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c04ff-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="c04ff-106">dans Définissez cette valeur sur `true` pour permettre au Common Language Runtime (CLR) d’appeler les `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` méthodes et lorsque leurs événements associés se produisent.</span><span class="sxs-lookup"><span data-stu-id="c04ff-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="c04ff-107">La valeur par défaut est `false` pour les modules non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="c04ff-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="c04ff-108">La valeur est toujours `true` pour les modules dynamiques et ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="c04ff-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c04ff-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c04ff-109">Remarks</span></span>  
 <span data-ttu-id="c04ff-110">Les `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` rappels et sont toujours activés pour les modules dynamiques et ne peuvent pas être désactivés.</span><span class="sxs-lookup"><span data-stu-id="c04ff-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c04ff-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c04ff-111">Requirements</span></span>  
 <span data-ttu-id="c04ff-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c04ff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c04ff-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c04ff-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c04ff-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c04ff-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c04ff-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c04ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04ff-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c04ff-116">See also</span></span>
