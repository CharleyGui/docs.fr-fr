---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 431a546fb4a3b92b379e273553f0caf540ba1473
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449730"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="55826-102">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="55826-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="55826-103">Sous-classe de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) qui fournit des méthodes pour demander des informations sur les fonctions avec plusieurs versions de code natif.</span><span class="sxs-lookup"><span data-stu-id="55826-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="55826-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="55826-104">Methods</span></span>  

| <span data-ttu-id="55826-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="55826-105">Method</span></span>|<span data-ttu-id="55826-106">Description</span><span class="sxs-lookup"><span data-stu-id="55826-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="55826-107">Méthode GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="55826-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="55826-108">Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement.</span><span class="sxs-lookup"><span data-stu-id="55826-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="55826-109">Méthode GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="55826-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="55826-110">À partir de l’adresse de début du code natif, retourne les informations de mappage natives à IL pour cette version JIT du code.</span><span class="sxs-lookup"><span data-stu-id="55826-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="55826-111">Méthode GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="55826-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="55826-112">À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code.</span><span class="sxs-lookup"><span data-stu-id="55826-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="55826-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="55826-113">Requirements</span></span>  
<span data-ttu-id="55826-114">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="55826-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
<span data-ttu-id="55826-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55826-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="55826-116">**Versions de .net :** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55826-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="55826-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55826-117">See also</span></span>

- [<span data-ttu-id="55826-118">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="55826-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
