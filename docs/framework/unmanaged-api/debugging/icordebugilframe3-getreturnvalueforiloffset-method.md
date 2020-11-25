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
ms.openlocfilehash: 11207298b071527151535144330790df767c2101
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724999"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="95c86-102">ICorDebugILFrame3::GetReturnValueForILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="95c86-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>

<span data-ttu-id="95c86-103">Obtient un objet « ICorDebugValue » qui encapsule la valeur de retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="95c86-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95c86-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95c86-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95c86-105">Parameters</span></span>  

 `ILOffset`  
 <span data-ttu-id="95c86-106">Offset IL.</span><span class="sxs-lookup"><span data-stu-id="95c86-106">The IL offset.</span></span> <span data-ttu-id="95c86-107">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="95c86-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="95c86-108">Pointeur vers l’adresse d’un objet d’interface « ICorDebugValue » qui fournit des informations sur la valeur de retour d’un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="95c86-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95c86-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="95c86-109">Remarks</span></span>  

 <span data-ttu-id="95c86-110">Cette méthode est utilisée avec la méthode [ICorDebugCode3 :: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pour obtenir la valeur de retour d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="95c86-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="95c86-111">Elle est particulièrement utile dans le cas des méthodes dont les valeurs de retour sont ignorées, comme dans les deux exemples de code suivants.</span><span class="sxs-lookup"><span data-stu-id="95c86-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="95c86-112">Le premier exemple appelle la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> méthode, mais ignore la valeur de retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="95c86-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="95c86-113">Le deuxième exemple illustre un problème bien plus courant lors du débogage.</span><span class="sxs-lookup"><span data-stu-id="95c86-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="95c86-114">Étant donné qu’une méthode est utilisée en tant qu’argument dans un appel de méthode, sa valeur de retour est accessible uniquement lorsque le débogueur parcourt la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="95c86-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="95c86-115">Dans de nombreux cas, en particulier lorsque la méthode appelée est définie dans une bibliothèque externe, ce n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="95c86-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="95c86-116">Si vous transmettez à la méthode [ICorDebugCode3 :: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) un offset il à un site d’appel de fonction, elle retourne un ou plusieurs offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="95c86-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="95c86-117">Le débogueur peut ensuite définir des points d’arrêt sur ces offsets natifs dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="95c86-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="95c86-118">Quand le débogueur atteint l’un des points d’arrêt, vous pouvez ensuite passer le même offset IL que celui que vous avez passé à cette méthode pour obtenir la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="95c86-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="95c86-119">Le débogueur doit ensuite effacer tous les points d’arrêt qu’il définit.</span><span class="sxs-lookup"><span data-stu-id="95c86-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="95c86-120">La [méthode ICorDebugCode3 :: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) et les `ICorDebugILFrame3::GetReturnValueForILOffset` méthodes vous permettent d’obtenir des informations de valeur de retour pour les types référence uniquement.</span><span class="sxs-lookup"><span data-stu-id="95c86-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="95c86-121">La récupération des informations de valeur de retour à partir des types valeur (autrement dit, tous les types qui dérivent de <xref:System.ValueType> ) n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="95c86-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="95c86-122">Le décalage IL spécifié par le `ILOffset` paramètre doit se trouver sur un site d’appel de fonction, et le programme débogué doit être arrêté à un point d’arrêt défini au niveau de l’offset natif retourné par la méthode [ICorDebugCode3 :: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pour le même offset il.</span><span class="sxs-lookup"><span data-stu-id="95c86-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="95c86-123">Si le programme débogué n’est pas arrêté à l’emplacement approprié pour l’offset IL spécifié, l’API échoue.</span><span class="sxs-lookup"><span data-stu-id="95c86-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="95c86-124">Si l’appel de fonction ne retourne pas de valeur, l’API échoue.</span><span class="sxs-lookup"><span data-stu-id="95c86-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="95c86-125">La `ICorDebugILFrame3::GetReturnValueForILOffset` méthode est disponible uniquement sur les systèmes x86 et amd64.</span><span class="sxs-lookup"><span data-stu-id="95c86-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c86-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95c86-126">Requirements</span></span>  

 <span data-ttu-id="95c86-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c86-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c86-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95c86-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95c86-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95c86-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95c86-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c86-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c86-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95c86-131">See also</span></span>

- [<span data-ttu-id="95c86-132">GetReturnValueLiveOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="95c86-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="95c86-133">ICorDebugILFrame3, interface</span><span class="sxs-lookup"><span data-stu-id="95c86-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
