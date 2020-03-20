---
title: ICorDebugProcess6::GetExportStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178530"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="461f2-102">ICorDebugProcess6::GetExportStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="461f2-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="461f2-103">Fournit des informations sur les fonctions exportées du runtime pour faciliter l'exécution pas à pas du code managé.</span><span class="sxs-lookup"><span data-stu-id="461f2-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="461f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="461f2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="461f2-105">Parameters</span></span>  
 <span data-ttu-id="461f2-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="461f2-106">pszExportName</span></span>  
 <span data-ttu-id="461f2-107">[in] Nom d'une fonction exportée du runtime tel qu'écrit dans la table d'exportation PE.</span><span class="sxs-lookup"><span data-stu-id="461f2-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="461f2-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="461f2-108">invokeKind</span></span>  
 <span data-ttu-id="461f2-109">[out] Un pointeur à un membre du [coscétation CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) qui décrit comment la fonction exportée invoquera le code géré.</span><span class="sxs-lookup"><span data-stu-id="461f2-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="461f2-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="461f2-110">invokePurpose</span></span>  
 <span data-ttu-id="461f2-111">[out] Un pointeur à un membre du [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) énumération qui décrit pourquoi la fonction exportée appellera le code géré.</span><span class="sxs-lookup"><span data-stu-id="461f2-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="461f2-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="461f2-112">Return Value</span></span>  
 <span data-ttu-id="461f2-113">La méthode peut retourner les valeurs répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="461f2-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="461f2-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="461f2-114">Return value</span></span>|<span data-ttu-id="461f2-115">Description</span><span class="sxs-lookup"><span data-stu-id="461f2-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="461f2-116">L'appel de méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="461f2-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="461f2-117">`pInvokeKind`ou `pInvokePurpose` est **nul**.</span><span class="sxs-lookup"><span data-stu-id="461f2-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="461f2-118">Autres valeurs `HRESULT` indiquant un échec.</span><span class="sxs-lookup"><span data-stu-id="461f2-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="461f2-119">Selon le cas</span><span class="sxs-lookup"><span data-stu-id="461f2-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="461f2-120">Notes </span><span class="sxs-lookup"><span data-stu-id="461f2-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="461f2-121">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="461f2-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="461f2-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="461f2-122">Requirements</span></span>  
 <span data-ttu-id="461f2-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="461f2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="461f2-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="461f2-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="461f2-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="461f2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="461f2-126">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="461f2-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461f2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="461f2-127">See also</span></span>

- [<span data-ttu-id="461f2-128">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="461f2-128">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="461f2-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="461f2-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
