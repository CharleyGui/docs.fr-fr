---
title: ICorDebugThread3::CreateStackWalk, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: ca5db8c8570cedd9b0412b71058d453112a1831c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140126"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="985a0-102">ICorDebugThread3::CreateStackWalk, méthode</span><span class="sxs-lookup"><span data-stu-id="985a0-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="985a0-103">Crée un objet [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="985a0-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="985a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="985a0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="985a0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="985a0-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="985a0-106">à Pointeur vers l’adresse de l’objet [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="985a0-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="985a0-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="985a0-107">Return Value</span></span>  
 <span data-ttu-id="985a0-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="985a0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="985a0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="985a0-109">HRESULT</span></span>|<span data-ttu-id="985a0-110">Description</span><span class="sxs-lookup"><span data-stu-id="985a0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="985a0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="985a0-111">S_OK</span></span>|<span data-ttu-id="985a0-112">L’objet `ICorDebugStackWalk` a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="985a0-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="985a0-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="985a0-113">E_FAIL</span></span>|<span data-ttu-id="985a0-114">L’objet `ICorDebugStackWalk` n’a pas été créé.</span><span class="sxs-lookup"><span data-stu-id="985a0-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="985a0-115">Exceptions</span><span class="sxs-lookup"><span data-stu-id="985a0-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="985a0-116">Notes</span><span class="sxs-lookup"><span data-stu-id="985a0-116">Remarks</span></span>  
 <span data-ttu-id="985a0-117">Si la méthode `CreateStackWalk` est réussie, le contexte de l’objet `ICorDebugStackWalk` retourné est défini sur le contexte actuel du thread.</span><span class="sxs-lookup"><span data-stu-id="985a0-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="985a0-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="985a0-118">Requirements</span></span>  
 <span data-ttu-id="985a0-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="985a0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="985a0-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="985a0-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="985a0-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="985a0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="985a0-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="985a0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985a0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="985a0-123">See also</span></span>

- [<span data-ttu-id="985a0-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="985a0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="985a0-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="985a0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
