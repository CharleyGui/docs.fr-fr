---
title: ICorDebugILFrame3::GetReturnValueForILOffset, méthode
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178813"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="57024-102">ICorDebugILFrame3::GetReturnValueForILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="57024-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="57024-103">Obtient un objet "ICorDebugValue" qui résume la valeur de retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="57024-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57024-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57024-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57024-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="57024-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="57024-106">L’IL compensé.</span><span class="sxs-lookup"><span data-stu-id="57024-106">The IL offset.</span></span> <span data-ttu-id="57024-107">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="57024-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="57024-108">Un pointeur à l’adresse d’un objet d’interface "ICorDebugValue" qui fournit des informations sur la valeur de retour d’un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="57024-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57024-109">Notes </span><span class="sxs-lookup"><span data-stu-id="57024-109">Remarks</span></span>  
 <span data-ttu-id="57024-110">Cette méthode est utilisée avec la méthode [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pour obtenir la valeur de retour d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="57024-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="57024-111">Il est particulièrement utile dans le cas de méthodes dont les valeurs de retour sont ignorées, comme dans les deux exemples de code suivants.</span><span class="sxs-lookup"><span data-stu-id="57024-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="57024-112">Le premier exemple <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> appelle la méthode, mais ignore la valeur de retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="57024-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="57024-113">Le deuxième exemple illustre un problème beaucoup plus fréquent dans le débogage.</span><span class="sxs-lookup"><span data-stu-id="57024-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="57024-114">Étant donné qu’une méthode est utilisée comme argument dans un appel de méthode, sa valeur de retour n’est accessible que lorsque le débbuggeur passe par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="57024-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="57024-115">Dans de nombreux cas, en particulier lorsque la méthode appelée est définie dans une bibliothèque externe, ce n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="57024-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="57024-116">Si vous passez la méthode [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) méthode un décalage IL à un site d’appel de fonction, il retourne un ou plusieurs décalages natifs.</span><span class="sxs-lookup"><span data-stu-id="57024-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="57024-117">Le débbuggeur peut alors définir des points d’arrêt sur ces décalages indigènes dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="57024-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="57024-118">Lorsque le débbuggeur frappe l’un des points d’arrêt, vous pouvez alors passer le même décalage IL que vous avez passé à cette méthode pour obtenir la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="57024-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="57024-119">Le débbuggeur doit alors effacer tous les points d’arrêt qu’il a fixés.</span><span class="sxs-lookup"><span data-stu-id="57024-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="57024-120">La [méthode ICorDebugCode3::GetReturnValueLiveOffset Méthode](icordebugcode3-getreturnvalueliveoffset-method.md) et `ICorDebugILFrame3::GetReturnValueForILOffset` les méthodes vous permettent d’obtenir des informations de valeur de retour pour les types de référence seulement.</span><span class="sxs-lookup"><span data-stu-id="57024-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="57024-121">La récupération des informations sur la valeur de retour provenant <xref:System.ValueType>de types de valeurs (c’est-à-dire tous les types qui dérivent) n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="57024-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="57024-122">Le décalage IL `ILOffset` spécifié par le paramètre doit être à un site d’appel de fonction, et le débbuggee doit être arrêté à un point d’arrêt fixé à la compensation indigène retourné par [l’ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) méthode pour le même décalage IL.</span><span class="sxs-lookup"><span data-stu-id="57024-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="57024-123">Si le débbuggee n’est pas arrêté à l’endroit correct pour le décalage IL spécifié, l’API échouera.</span><span class="sxs-lookup"><span data-stu-id="57024-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="57024-124">Si l’appel de fonction ne retourne pas une valeur, l’API échouera.</span><span class="sxs-lookup"><span data-stu-id="57024-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="57024-125">La `ICorDebugILFrame3::GetReturnValueForILOffset` méthode n’est disponible que sur les systèmes x86 et AMD64.</span><span class="sxs-lookup"><span data-stu-id="57024-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57024-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="57024-126">Requirements</span></span>  
 <span data-ttu-id="57024-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57024-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57024-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57024-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57024-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57024-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57024-130">**.NET Versions-cadre:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57024-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57024-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57024-131">See also</span></span>

- [<span data-ttu-id="57024-132">GetReturnValueLiveOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="57024-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="57024-133">ICorDebugILFrame3, interface</span><span class="sxs-lookup"><span data-stu-id="57024-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
