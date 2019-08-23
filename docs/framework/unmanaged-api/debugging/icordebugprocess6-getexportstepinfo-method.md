---
title: ICorDebugProcess6::GetExportStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18af0dde2d1acc65003558a04789de027bb9209f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967399"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="98e46-102">ICorDebugProcess6::GetExportStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="98e46-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="98e46-103">Fournit des informations sur les fonctions exportées du runtime pour faciliter l'exécution pas à pas du code managé.</span><span class="sxs-lookup"><span data-stu-id="98e46-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98e46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98e46-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="98e46-105">Parameters</span></span>  
 <span data-ttu-id="98e46-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="98e46-106">pszExportName</span></span>  
 <span data-ttu-id="98e46-107">[in] Nom d'une fonction exportée du runtime tel qu'écrit dans la table d'exportation PE.</span><span class="sxs-lookup"><span data-stu-id="98e46-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="98e46-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="98e46-108">invokeKind</span></span>  
 <span data-ttu-id="98e46-109">à Pointeur vers un membre de l’énumération [cordebugcodeinvokekind,](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) qui décrit comment la fonction exportée appellera le code managé.</span><span class="sxs-lookup"><span data-stu-id="98e46-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="98e46-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="98e46-110">invokePurpose</span></span>  
 <span data-ttu-id="98e46-111">à Pointeur vers un membre de l’énumération [cordebugcodeinvokepurpose,](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) qui décrit la raison pour laquelle la fonction exportée appellera du code managé.</span><span class="sxs-lookup"><span data-stu-id="98e46-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98e46-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="98e46-112">Return Value</span></span>  
 <span data-ttu-id="98e46-113">La méthode peut retourner les valeurs répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="98e46-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="98e46-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="98e46-114">Return value</span></span>|<span data-ttu-id="98e46-115">Description</span><span class="sxs-lookup"><span data-stu-id="98e46-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="98e46-116">L'appel de méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="98e46-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="98e46-117">`pInvokeKind`ou `pInvokePurpose` a la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="98e46-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="98e46-118">Autres valeurs `HRESULT` indiquant un échec.</span><span class="sxs-lookup"><span data-stu-id="98e46-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="98e46-119">Selon le cas</span><span class="sxs-lookup"><span data-stu-id="98e46-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98e46-120">Notes</span><span class="sxs-lookup"><span data-stu-id="98e46-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98e46-121">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="98e46-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e46-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="98e46-122">Requirements</span></span>  
 <span data-ttu-id="98e46-123">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e46-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e46-124">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98e46-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98e46-125">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98e46-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e46-126">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e46-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e46-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98e46-127">See also</span></span>

- [<span data-ttu-id="98e46-128">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="98e46-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="98e46-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="98e46-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
