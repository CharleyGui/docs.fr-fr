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
ms.openlocfilehash: 64f6bc9abb8105cdfa942c2aaca71994e8a91765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791415"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="e1715-102">ICorDebugThread3::CreateStackWalk, méthode</span><span class="sxs-lookup"><span data-stu-id="e1715-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="e1715-103">Crée un objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="e1715-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1715-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1715-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1715-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e1715-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="e1715-106">à Pointeur vers l’adresse de l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="e1715-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1715-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e1715-107">Return Value</span></span>  
 <span data-ttu-id="e1715-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e1715-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e1715-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1715-109">HRESULT</span></span>|<span data-ttu-id="e1715-110">Description</span><span class="sxs-lookup"><span data-stu-id="e1715-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1715-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1715-111">S_OK</span></span>|<span data-ttu-id="e1715-112">L’objet `ICorDebugStackWalk` a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="e1715-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="e1715-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1715-113">E_FAIL</span></span>|<span data-ttu-id="e1715-114">L’objet `ICorDebugStackWalk` n’a pas été créé.</span><span class="sxs-lookup"><span data-stu-id="e1715-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e1715-115">Exceptions</span><span class="sxs-lookup"><span data-stu-id="e1715-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1715-116">Notes</span><span class="sxs-lookup"><span data-stu-id="e1715-116">Remarks</span></span>  
 <span data-ttu-id="e1715-117">Si la méthode `CreateStackWalk` est réussie, le contexte de l’objet `ICorDebugStackWalk` retourné est défini sur le contexte actuel du thread.</span><span class="sxs-lookup"><span data-stu-id="e1715-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1715-118">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e1715-118">Requirements</span></span>  
 <span data-ttu-id="e1715-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1715-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1715-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1715-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1715-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1715-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1715-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1715-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1715-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1715-123">See also</span></span>

- [<span data-ttu-id="e1715-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e1715-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e1715-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="e1715-125">Debugging</span></span>](index.md)
