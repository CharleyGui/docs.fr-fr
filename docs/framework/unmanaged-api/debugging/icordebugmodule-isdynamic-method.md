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
ms.openlocfilehash: 4517f266bbb500223214a6a8fe5881e8b29566c3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206885"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="8bcda-102">ICorDebugModule::IsDynamic, méthode</span><span class="sxs-lookup"><span data-stu-id="8bcda-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="8bcda-103">Obtient une valeur qui indique si ce module est dynamique.</span><span class="sxs-lookup"><span data-stu-id="8bcda-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bcda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bcda-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bcda-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8bcda-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="8bcda-106">[out] `true` Si ce module est dynamique ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="8bcda-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bcda-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="8bcda-107">Remarks</span></span>  
 <span data-ttu-id="8bcda-108">Un module dynamique peut ajouter de nouvelles classes et supprimer des classes existantes même après le chargement du module.</span><span class="sxs-lookup"><span data-stu-id="8bcda-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="8bcda-109">Les rappels [ICorDebugManagedCallback :: LoadClass](icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback :: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) informent le débogueur lorsqu’une classe a été ajoutée ou supprimée.</span><span class="sxs-lookup"><span data-stu-id="8bcda-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bcda-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8bcda-110">Requirements</span></span>  
 <span data-ttu-id="8bcda-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bcda-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bcda-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bcda-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bcda-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bcda-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bcda-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bcda-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
