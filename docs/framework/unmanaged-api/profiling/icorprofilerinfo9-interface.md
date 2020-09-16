---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f38195b1a7983e23c7f5c20055ea8c2a8bfcb7d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556848"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="67fc1-102">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="67fc1-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="67fc1-103">Sous-classe de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) qui fournit des méthodes pour demander des informations sur les fonctions avec plusieurs versions de code natif.</span><span class="sxs-lookup"><span data-stu-id="67fc1-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="67fc1-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="67fc1-104">Methods</span></span>  

| <span data-ttu-id="67fc1-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="67fc1-105">Method</span></span>|<span data-ttu-id="67fc1-106">Description</span><span class="sxs-lookup"><span data-stu-id="67fc1-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="67fc1-107">Méthode GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="67fc1-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="67fc1-108">Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement.</span><span class="sxs-lookup"><span data-stu-id="67fc1-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="67fc1-109">Méthode GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="67fc1-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="67fc1-110">À partir de l’adresse de début du code natif, retourne les informations de mappage natives à IL pour cette version JIT du code.</span><span class="sxs-lookup"><span data-stu-id="67fc1-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="67fc1-111">Méthode GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="67fc1-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="67fc1-112">À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code.</span><span class="sxs-lookup"><span data-stu-id="67fc1-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="67fc1-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="67fc1-113">Requirements</span></span>  
<span data-ttu-id="67fc1-114">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="67fc1-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="67fc1-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67fc1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="67fc1-116">**Versions de .net :**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67fc1-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="67fc1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67fc1-117">See also</span></span>

- [<span data-ttu-id="67fc1-118">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="67fc1-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
