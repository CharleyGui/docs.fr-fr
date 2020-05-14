---
title: ICorDebugVirtualUnwinder::Next, méthode
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 55f10a6148f0b11cf74492afe947d5921a1d1458
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396423"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="210c9-102">ICorDebugVirtualUnwinder::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="210c9-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="210c9-103">Avance jusqu'au contexte de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="210c9-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="210c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="210c9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="210c9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="210c9-105">Parameters</span></span>  
 <span data-ttu-id="210c9-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="210c9-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="210c9-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="210c9-107">Return Value</span></span>  
 <span data-ttu-id="210c9-108">`S_OK` en cas de réussite du déroulement ou `CORDBG_S_AT_END_OF_STACK` si le déroulement ne peut pas être effectué étant donné qu'il ne reste plus de frames.</span><span class="sxs-lookup"><span data-stu-id="210c9-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="210c9-109">Si un HRESULT indiquant un échec est retourné, les API ICorDebug retournent `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="210c9-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="210c9-110">Notes</span><span class="sxs-lookup"><span data-stu-id="210c9-110">Remarks</span></span>  
 <span data-ttu-id="210c9-111">L'explorateur de pile doit vérifier sa progression vers l'avant. Ainsi, un appel à `Next` doit retourner un HRESULT indiquant un échec ou `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="210c9-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="210c9-112">Si vous retournez `S_OK` indéfiniment, vous risquez de provoquer une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="210c9-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="210c9-113">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="210c9-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="210c9-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="210c9-114">Requirements</span></span>  
 <span data-ttu-id="210c9-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="210c9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="210c9-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="210c9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="210c9-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="210c9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="210c9-118">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="210c9-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="210c9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="210c9-119">See also</span></span>

- [<span data-ttu-id="210c9-120">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="210c9-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="210c9-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="210c9-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
