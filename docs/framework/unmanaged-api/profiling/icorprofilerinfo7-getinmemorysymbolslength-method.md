---
title: 'ICorProfilerInfo7 :: GetInMemorySymbolsLength, méthode'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 46ffa5cb4fac6988240d32cb1939cc25bdf0a412
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686070"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="3cee5-102">ICorProfilerInfo7 :: GetInMemorySymbolsLength, méthode</span><span class="sxs-lookup"><span data-stu-id="3cee5-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>

<span data-ttu-id="3cee5-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="3cee5-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3cee5-104">Retourne la longueur d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="3cee5-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cee5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cee5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cee5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3cee5-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="3cee5-107">dans Identificateur du module contenant le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="3cee5-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="3cee5-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="3cee5-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="3cee5-109">à Pointeur vers une `DWORD` valeur qui, lorsque la méthode est retournée, contient la longueur du flux en octets.</span><span class="sxs-lookup"><span data-stu-id="3cee5-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cee5-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3cee5-110">Return Value</span></span>  

 <span data-ttu-id="3cee5-111">La méthode retourne `S_OK` si la longueur du flux de mémoire peut être déterminée, même si elle est égale à zéro (0).</span><span class="sxs-lookup"><span data-stu-id="3cee5-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="3cee5-112">La méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC` si la méthode a été créée à l’aide de <xref:System.Reflection.Emit?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3cee5-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cee5-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="3cee5-113">Remarks</span></span>  

 <span data-ttu-id="3cee5-114">Si le module contient des symboles en mémoire, la longueur du flux est placée dans `pCountSymbolBytes` .</span><span class="sxs-lookup"><span data-stu-id="3cee5-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="3cee5-115">Si le module n’a pas de symboles en mémoire, `*pCountSymbolBytes = 0` .</span><span class="sxs-lookup"><span data-stu-id="3cee5-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cee5-116">L’implémentation actuelle ne prend pas en charge la réflexion. Emit.</span><span class="sxs-lookup"><span data-stu-id="3cee5-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="3cee5-117">Si le module a été créé à l’aide de Reflection. Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="3cee5-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cee5-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3cee5-118">Requirements</span></span>  

 <span data-ttu-id="3cee5-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cee5-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cee5-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3cee5-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3cee5-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cee5-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cee5-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cee5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cee5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cee5-123">See also</span></span>

- [<span data-ttu-id="3cee5-124">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="3cee5-124">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
