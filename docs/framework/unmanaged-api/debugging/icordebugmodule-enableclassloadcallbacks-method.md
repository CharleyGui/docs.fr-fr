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
ms.openlocfilehash: d552b694787b5d9f0d5adc399eda6f75df93c385
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793019"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="143b6-102">ICorDebugModule::EnableClassLoadCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="143b6-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="143b6-103">Contrôle si les rappels [ICorDebugManagedCallback :: LoadClass](icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback :: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.</span><span class="sxs-lookup"><span data-stu-id="143b6-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="143b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="143b6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="143b6-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="143b6-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="143b6-106">dans Définissez cette valeur sur `true` pour permettre au common language runtime (CLR) d’appeler les méthodes `ICorDebugManagedCallback::LoadClass` et `ICorDebugManagedCallback::UnloadClass` lorsque leurs événements associés se produisent.</span><span class="sxs-lookup"><span data-stu-id="143b6-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="143b6-107">La valeur par défaut est `false` pour les modules non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="143b6-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="143b6-108">La valeur est toujours `true` pour les modules dynamiques et ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="143b6-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="143b6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="143b6-109">Remarks</span></span>  
 <span data-ttu-id="143b6-110">Les rappels d' `ICorDebugManagedCallback::LoadClass` et de `ICorDebugManagedCallback::UnloadClass` sont toujours activés pour les modules dynamiques et ne peuvent pas être désactivés.</span><span class="sxs-lookup"><span data-stu-id="143b6-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="143b6-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="143b6-111">Requirements</span></span>  
 <span data-ttu-id="143b6-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="143b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="143b6-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="143b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="143b6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="143b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="143b6-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="143b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="143b6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="143b6-116">See also</span></span>
