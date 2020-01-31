---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 371e85ce8f5d7b420a30ac842ec658949e47d30e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861643"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="9dd0c-102">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="9dd0c-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="9dd0c-103">Sous-classe de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) qui fournit des méthodes pour demander des informations sur les fonctions avec plusieurs versions de code natif.</span><span class="sxs-lookup"><span data-stu-id="9dd0c-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="9dd0c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9dd0c-104">Methods</span></span>  

| <span data-ttu-id="9dd0c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9dd0c-105">Method</span></span>|<span data-ttu-id="9dd0c-106">Description</span><span class="sxs-lookup"><span data-stu-id="9dd0c-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="9dd0c-107">Méthode GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="9dd0c-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="9dd0c-108">Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement.</span><span class="sxs-lookup"><span data-stu-id="9dd0c-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="9dd0c-109">Méthode GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="9dd0c-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="9dd0c-110">À partir de l’adresse de début du code natif, retourne les informations de mappage natives à IL pour cette version JIT du code.</span><span class="sxs-lookup"><span data-stu-id="9dd0c-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="9dd0c-111">Méthode GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="9dd0c-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="9dd0c-112">À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code.</span><span class="sxs-lookup"><span data-stu-id="9dd0c-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="9dd0c-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9dd0c-113">Requirements</span></span>  
<span data-ttu-id="9dd0c-114">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="9dd0c-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="9dd0c-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9dd0c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="9dd0c-116">**Versions de .net :** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dd0c-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9dd0c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dd0c-117">See also</span></span>

- [<span data-ttu-id="9dd0c-118">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="9dd0c-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
