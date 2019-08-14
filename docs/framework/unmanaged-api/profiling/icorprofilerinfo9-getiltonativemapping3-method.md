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
ms.openlocfilehash: 46ceef43806fda9956797935c5eeec61f865dc6e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973789"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="2e0c4-102">ICorProfilerInfo9:: GetILToNativeMapping3, méthode</span><span class="sxs-lookup"><span data-stu-id="2e0c4-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>
  
 <span data-ttu-id="2e0c4-103">À partir de l’adresse de début du code natif, retourne les informations de mappage natives à IL pour cette version JIT du code.</span><span class="sxs-lookup"><span data-stu-id="2e0c4-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="2e0c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e0c4-104">Syntax</span></span>  
  
```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e0c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e0c4-105">Parameters</span></span>  
 `pNativeCodeStartAddress` \
 <span data-ttu-id="2e0c4-106">dans Pointeur vers le début d’une fonction native.</span><span class="sxs-lookup"><span data-stu-id="2e0c4-106">[in] A pointer to the start of a native function.</span></span>

 `cMap` \
 <span data-ttu-id="2e0c4-107">[in] Taille maximale du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="2e0c4-107">[in] The maximum size of the `map` array.</span></span> 

 `pcMap` \
 <span data-ttu-id="2e0c4-108">à Nombre total de structures COR_DEBUG_IL_TO_NATIVE_MAP disponibles.</span><span class="sxs-lookup"><span data-stu-id="2e0c4-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

 `map` \
 <span data-ttu-id="2e0c4-109">à Tableau des structures [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , chacune spécifiant les décalages.</span><span class="sxs-lookup"><span data-stu-id="2e0c4-109">[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="2e0c4-110">Suite au retour de la méthode `GetILToNativeMapping3`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="2e0c4-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e0c4-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2e0c4-111">Remarks</span></span>  
 <span data-ttu-id="2e0c4-112">Lorsque la compilation à plusieurs niveaux est activée, une méthode peut avoir plusieurs corps de code natif.</span><span class="sxs-lookup"><span data-stu-id="2e0c4-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="2e0c4-113">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) retourne les adresses de démarrage de tous les corps de code natif.</span><span class="sxs-lookup"><span data-stu-id="2e0c4-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="2e0c4-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e0c4-114">Requirements</span></span>  
 <span data-ttu-id="2e0c4-115">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="2e0c4-115">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="2e0c4-116">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2e0c4-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e0c4-117">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e0c4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e0c4-118">**Versions du .NET Framework :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e0c4-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="2e0c4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e0c4-119">See also</span></span>
- [<span data-ttu-id="2e0c4-120">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="2e0c4-120">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

