---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 5c49d75432980d2f3af77ee040bc6eb20886b027
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861669"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="2df48-102">ICorProfilerInfo9 :: GetILToNativeMapping3, méthode</span><span class="sxs-lookup"><span data-stu-id="2df48-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="2df48-103">À partir de l’adresse de début du code natif, retourne les informations de mappage natives à IL pour cette version JIT du code.</span><span class="sxs-lookup"><span data-stu-id="2df48-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="2df48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2df48-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="2df48-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="2df48-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="2df48-106">\[dans] pointeur vers le début d’une fonction native.</span><span class="sxs-lookup"><span data-stu-id="2df48-106">\[in] A pointer to the start of a native function.</span></span>

- `cMap`

  <span data-ttu-id="2df48-107">\[dans] taille maximale du tableau de `map`.</span><span class="sxs-lookup"><span data-stu-id="2df48-107">\[in] The maximum size of the `map` array.</span></span>

- `pcMap`

  <span data-ttu-id="2df48-108">\[out] nombre total de structures COR_DEBUG_IL_TO_NATIVE_MAP disponibles.</span><span class="sxs-lookup"><span data-stu-id="2df48-108">\[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

- `map`

  <span data-ttu-id="2df48-109">\[out] tableau de structures [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , chacune spécifiant les décalages.</span><span class="sxs-lookup"><span data-stu-id="2df48-109">\[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="2df48-110">Suite au retour de la méthode `GetILToNativeMapping3`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="2df48-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="2df48-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2df48-111">Remarks</span></span>

<span data-ttu-id="2df48-112">Lorsque la compilation à plusieurs niveaux est activée, une méthode peut avoir plusieurs corps de code natif.</span><span class="sxs-lookup"><span data-stu-id="2df48-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="2df48-113">[ICorProfilerInfo9 :: GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) retourne les adresses de démarrage de tous les corps de code natif.</span><span class="sxs-lookup"><span data-stu-id="2df48-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="2df48-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2df48-114">Requirements</span></span>

<span data-ttu-id="2df48-115">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="2df48-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="2df48-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2df48-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="2df48-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2df48-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2df48-118">**Versions du .NET Framework :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df48-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2df48-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2df48-119">See also</span></span>

- [<span data-ttu-id="2df48-120">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="2df48-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
