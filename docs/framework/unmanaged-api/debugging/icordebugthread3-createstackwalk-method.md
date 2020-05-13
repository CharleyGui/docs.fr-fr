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
ms.openlocfilehash: f2850e6c9cbb2250a08ab4a0e34c69e377d3a23d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375847"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="73458-102">ICorDebugThread3::CreateStackWalk, méthode</span><span class="sxs-lookup"><span data-stu-id="73458-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="73458-103">Crée un objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="73458-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73458-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73458-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73458-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73458-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="73458-106">à Pointeur vers l’adresse de l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="73458-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73458-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="73458-107">Return Value</span></span>  
 <span data-ttu-id="73458-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="73458-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="73458-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73458-109">HRESULT</span></span>|<span data-ttu-id="73458-110">Description</span><span class="sxs-lookup"><span data-stu-id="73458-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73458-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="73458-111">S_OK</span></span>|<span data-ttu-id="73458-112">L' `ICorDebugStackWalk` objet a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="73458-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="73458-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73458-113">E_FAIL</span></span>|<span data-ttu-id="73458-114">L' `ICorDebugStackWalk` objet n’a pas été créé.</span><span class="sxs-lookup"><span data-stu-id="73458-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="73458-115">Exceptions</span><span class="sxs-lookup"><span data-stu-id="73458-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73458-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="73458-116">Remarks</span></span>  
 <span data-ttu-id="73458-117">Si la `CreateStackWalk` méthode est réussie, le `ICorDebugStackWalk` contexte de l’objet retourné est défini sur le contexte actuel du thread.</span><span class="sxs-lookup"><span data-stu-id="73458-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73458-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="73458-118">Requirements</span></span>  
 <span data-ttu-id="73458-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73458-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73458-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73458-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73458-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73458-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73458-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73458-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73458-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73458-123">See also</span></span>

- [<span data-ttu-id="73458-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="73458-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="73458-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="73458-125">Debugging</span></span>](index.md)
