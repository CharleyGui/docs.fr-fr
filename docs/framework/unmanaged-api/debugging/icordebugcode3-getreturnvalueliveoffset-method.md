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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178938"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="ef83b-102">ICorDebugCode3::GetReturnValueLiveOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="ef83b-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="ef83b-103">Pour un décalage IL spécifié, obtient les décalages natifs où un point d’arrêt doit être placé de sorte que le débbuggeur peut obtenir la valeur de retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="ef83b-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef83b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef83b-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef83b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef83b-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="ef83b-106">L’IL compensé.</span><span class="sxs-lookup"><span data-stu-id="ef83b-106">The IL offset.</span></span> <span data-ttu-id="ef83b-107">Il doit s’agir d’un site d’appel de fonction ou l’appel de fonction échouera.</span><span class="sxs-lookup"><span data-stu-id="ef83b-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="ef83b-108">Le nombre d’octets `pOffsets`disponibles pour stocker .</span><span class="sxs-lookup"><span data-stu-id="ef83b-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="ef83b-109">Un pointeur sur le nombre de compensations effectivement retourné.</span><span class="sxs-lookup"><span data-stu-id="ef83b-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="ef83b-110">Habituellement, sa valeur est de 1, mais `CALL` une seule instruction IL peut cartographier à plusieurs instructions d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="ef83b-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="ef83b-111">Un éventail de décalages indigènes.</span><span class="sxs-lookup"><span data-stu-id="ef83b-111">An array of native offsets.</span></span> <span data-ttu-id="ef83b-112">Typiquement, `pOffsets` contient un décalage unique, bien qu’une seule `CALL` instruction d’IL puisse cartographier à plusieurs instructions d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="ef83b-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef83b-113">Notes </span><span class="sxs-lookup"><span data-stu-id="ef83b-113">Remarks</span></span>  
 <span data-ttu-id="ef83b-114">Cette méthode est utilisée avec la méthode [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) méthode pour obtenir la valeur de retour d’une méthode qui renvoie un type de référence.</span><span class="sxs-lookup"><span data-stu-id="ef83b-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="ef83b-115">Le passage d’un décalage IL à un site d’appel de fonction à cette méthode renvoie un ou plusieurs décalages indigènes.</span><span class="sxs-lookup"><span data-stu-id="ef83b-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="ef83b-116">Le débbuggeur peut alors définir des points d’arrêt sur ces décalages indigènes dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="ef83b-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="ef83b-117">Lorsque le débbuggeur frappe l’un des points d’arrêt, vous pouvez alors passer le même décalage IL que vous avez passé à cette méthode à [l’ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) méthode pour obtenir la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="ef83b-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="ef83b-118">Le débbuggeur doit alors effacer tous les points d’arrêt qu’il a fixés.</span><span class="sxs-lookup"><span data-stu-id="ef83b-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ef83b-119">Les `ICorDebugCode3::GetReturnValueLiveOffset` méthodes et [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) vous permettent d’obtenir des informations de valeur de retour pour les types de référence seulement.</span><span class="sxs-lookup"><span data-stu-id="ef83b-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="ef83b-120">La récupération des informations sur la valeur de retour provenant <xref:System.ValueType>de types de valeurs (c’est-à-dire tous les types qui dérivent) n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ef83b-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="ef83b-121">La fonction `HRESULT` renvoie les valeurs indiquées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="ef83b-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="ef83b-122">Valeur `HRESULT`</span><span class="sxs-lookup"><span data-stu-id="ef83b-122">`HRESULT` value</span></span>|<span data-ttu-id="ef83b-123">Description</span><span class="sxs-lookup"><span data-stu-id="ef83b-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="ef83b-124">Réussite.</span><span class="sxs-lookup"><span data-stu-id="ef83b-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="ef83b-125">Le site de compensation IL donné n’est `void`pas une instruction d’appel, ou la fonction revient .</span><span class="sxs-lookup"><span data-stu-id="ef83b-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="ef83b-126">Le décalage DONNÉ IL est un appel approprié, mais le type de retour n’est pas pris en compte pour obtenir une valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="ef83b-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="ef83b-127">La `ICorDebugCode3::GetReturnValueLiveOffset` méthode n’est disponible que sur les systèmes x86 et AMD64.</span><span class="sxs-lookup"><span data-stu-id="ef83b-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef83b-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ef83b-128">Requirements</span></span>  
 <span data-ttu-id="ef83b-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef83b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef83b-130">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef83b-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef83b-131">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef83b-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef83b-132">**.NET Versions-cadre:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef83b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef83b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef83b-133">See also</span></span>

- [<span data-ttu-id="ef83b-134">GetReturnValueForILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="ef83b-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="ef83b-135">ICorDebugCode3, interface</span><span class="sxs-lookup"><span data-stu-id="ef83b-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
