---
title: ICorDebugModule::IsDynamic, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 5774b40178ce0d7c2ef5d063a37b9011fc2630df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127947"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="63f31-102">ICorDebugModule::IsDynamic, méthode</span><span class="sxs-lookup"><span data-stu-id="63f31-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="63f31-103">Obtient une valeur qui indique si ce module est dynamique.</span><span class="sxs-lookup"><span data-stu-id="63f31-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63f31-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63f31-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63f31-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="63f31-106">[out] `true` si ce module est dynamique ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="63f31-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63f31-107">Notes</span><span class="sxs-lookup"><span data-stu-id="63f31-107">Remarks</span></span>  
 <span data-ttu-id="63f31-108">Un module dynamique peut ajouter de nouvelles classes et supprimer des classes existantes même après le chargement du module.</span><span class="sxs-lookup"><span data-stu-id="63f31-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="63f31-109">Les rappels [ICorDebugManagedCallback :: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback :: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) informent le débogueur lorsqu’une classe a été ajoutée ou supprimée.</span><span class="sxs-lookup"><span data-stu-id="63f31-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f31-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="63f31-110">Requirements</span></span>  
 <span data-ttu-id="63f31-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63f31-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63f31-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63f31-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63f31-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63f31-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63f31-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63f31-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
