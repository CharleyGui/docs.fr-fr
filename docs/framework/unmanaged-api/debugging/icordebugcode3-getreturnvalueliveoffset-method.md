---
title: ICorDebugCode3::GetReturnValueLiveOffset, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: dc03365b72a5f3613402faf1aed44b5683e9892c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777838"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="f267c-102">ICorDebugCode3::GetReturnValueLiveOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="f267c-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="f267c-103">Pour un offset IL spécifié, obtient les offsets natifs où un point d’arrêt doit être placé afin que le débogueur puisse obtenir la valeur de retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="f267c-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f267c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f267c-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f267c-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f267c-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="f267c-106">Offset IL.</span><span class="sxs-lookup"><span data-stu-id="f267c-106">The IL offset.</span></span> <span data-ttu-id="f267c-107">Il doit s’agir d’un site d’appel de fonction, sinon l’appel de fonction échoue.</span><span class="sxs-lookup"><span data-stu-id="f267c-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="f267c-108">Nombre d’octets disponibles pour stocker des `pOffsets`.</span><span class="sxs-lookup"><span data-stu-id="f267c-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="f267c-109">Pointeur vers le nombre d’offsets réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="f267c-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="f267c-110">En règle générale, sa valeur est 1, mais une instruction IL unique peut être mappée à plusieurs instructions `CALL` assembly.</span><span class="sxs-lookup"><span data-stu-id="f267c-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="f267c-111">Tableau d’offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="f267c-111">An array of native offsets.</span></span> <span data-ttu-id="f267c-112">En règle générale, `pOffsets` contient un offset unique, bien qu’une seule instruction IL puisse être mappée à plusieurs instructions d’assembly `CALL`.</span><span class="sxs-lookup"><span data-stu-id="f267c-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f267c-113">Notes</span><span class="sxs-lookup"><span data-stu-id="f267c-113">Remarks</span></span>  
 <span data-ttu-id="f267c-114">Cette méthode est utilisée avec la méthode [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) pour obtenir la valeur de retour d’une méthode qui retourne un type référence.</span><span class="sxs-lookup"><span data-stu-id="f267c-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="f267c-115">Le passage d’un offset IL à un site d’appel de fonction à cette méthode retourne un ou plusieurs offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="f267c-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="f267c-116">Le débogueur peut ensuite définir des points d’arrêt sur ces offsets natifs dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="f267c-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="f267c-117">Quand le débogueur atteint l’un des points d’arrêt, vous pouvez ensuite passer le même offset IL que celui que vous avez passé à cette méthode à la méthode [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) pour obtenir la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="f267c-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="f267c-118">Le débogueur doit ensuite effacer tous les points d’arrêt qu’il définit.</span><span class="sxs-lookup"><span data-stu-id="f267c-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f267c-119">Les méthodes `ICorDebugCode3::GetReturnValueLiveOffset` et [ICorDebugILFrame3 :: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) vous permettent d’obtenir des informations de valeur de retour pour les types référence uniquement.</span><span class="sxs-lookup"><span data-stu-id="f267c-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="f267c-120">La récupération d’informations de valeur de retour à partir de types valeur (autrement dit, tous les types qui dérivent de <xref:System.ValueType>) n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="f267c-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="f267c-121">La fonction retourne les valeurs de `HRESULT` indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f267c-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="f267c-122">Valeur de `HRESULT`</span><span class="sxs-lookup"><span data-stu-id="f267c-122">`HRESULT` value</span></span>|<span data-ttu-id="f267c-123">Description</span><span class="sxs-lookup"><span data-stu-id="f267c-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="f267c-124">Opération réussie.</span><span class="sxs-lookup"><span data-stu-id="f267c-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="f267c-125">Le site de décalage IL donné n’est pas une instruction d’appel, ou la fonction retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="f267c-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="f267c-126">L’offset IL donné est un appel approprié, mais le type de retour n’est pas pris en charge pour l’obtention d’une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="f267c-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="f267c-127">La méthode `ICorDebugCode3::GetReturnValueLiveOffset` est disponible uniquement sur les systèmes x86 et AMD64.</span><span class="sxs-lookup"><span data-stu-id="f267c-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f267c-128">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f267c-128">Requirements</span></span>  
 <span data-ttu-id="f267c-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f267c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f267c-130">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f267c-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f267c-131">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f267c-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f267c-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f267c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f267c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f267c-133">See also</span></span>

- [<span data-ttu-id="f267c-134">GetReturnValueForILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="f267c-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="f267c-135">ICorDebugCode3, interface</span><span class="sxs-lookup"><span data-stu-id="f267c-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
