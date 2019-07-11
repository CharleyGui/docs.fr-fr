---
title: ICorDebugThread::CreateStepper, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95a00e8646589e7897636c1698b7c2647cd233fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771803"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="883c1-102">ICorDebugThread::CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="883c1-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="883c1-103">Crée un objet ICorDebugStepper qui permet l’exécution pas à pas via le frame actif de ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="883c1-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="883c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="883c1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="883c1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="883c1-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="883c1-106">[out] Un pointeur vers l’adresse d’un `ICorDebugStepper` objet qui permet l’exécution pas à pas via le frame actif de ce thread.</span><span class="sxs-lookup"><span data-stu-id="883c1-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="883c1-107">Notes</span><span class="sxs-lookup"><span data-stu-id="883c1-107">Remarks</span></span>  
 <span data-ttu-id="883c1-108">Le frame actif peut être le code non managé.</span><span class="sxs-lookup"><span data-stu-id="883c1-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="883c1-109">Le `ICorDebugStepper` interface doit être utilisée pour effectuer l’exécution pas à pas réelle.</span><span class="sxs-lookup"><span data-stu-id="883c1-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="883c1-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="883c1-110">Requirements</span></span>  
 <span data-ttu-id="883c1-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="883c1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="883c1-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="883c1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="883c1-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="883c1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="883c1-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="883c1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
