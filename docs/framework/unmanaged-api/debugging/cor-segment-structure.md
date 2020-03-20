---
title: COR_SEGMENT, structure
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: a5c743064b8ca645cf45d02b8800c88187bf4c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179282"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="d8bcb-102">COR_SEGMENT, structure</span><span class="sxs-lookup"><span data-stu-id="d8bcb-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="d8bcb-103">Contient des informations sur une région de la mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8bcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8bcb-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="d8bcb-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d8bcb-105">Members</span></span>  
  
|<span data-ttu-id="d8bcb-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d8bcb-106">Member</span></span>|<span data-ttu-id="d8bcb-107">Description</span><span class="sxs-lookup"><span data-stu-id="d8bcb-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="d8bcb-108">Adresse de départ de la zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="d8bcb-109">Adresse de fin de la zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="d8bcb-110">Membre d’énumération [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) qui indique la génération de la zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="d8bcb-111">Numéro du tas dans lequel réside la zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="d8bcb-112">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8bcb-113">Notes </span><span class="sxs-lookup"><span data-stu-id="d8bcb-113">Remarks</span></span>  
 <span data-ttu-id="d8bcb-114">La structure `COR_SEGMENTS` représente une zone de mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="d8bcb-115">Les objets `COR_SEGMENTS` sont des membres de l’objet de collection [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md), qui est rempli en appelant la méthode [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8bcb-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="d8bcb-116">Le champ `heap` est le numéro de processeur, qui correspond au tas signalé.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="d8bcb-117">Pour les récupérateurs de mémoire de station de travail, sa valeur est toujours égale à zéro, car les stations de travail n’ont qu’un seul tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="d8bcb-118">Pour les récupérateurs de mémoire de serveur, sa valeur correspond au processeur auquel le tas est attaché.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="d8bcb-119">Notez qu’il peut y avoir plus ou moins de tas de garbage collection que de processeurs, en raison des détails d’implémentation du récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d8bcb-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8bcb-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d8bcb-120">Requirements</span></span>  
 <span data-ttu-id="d8bcb-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8bcb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8bcb-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8bcb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8bcb-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8bcb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8bcb-124">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8bcb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bcb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8bcb-125">See also</span></span>

- [<span data-ttu-id="d8bcb-126">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="d8bcb-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="d8bcb-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="d8bcb-127">Debugging</span></span>](index.md)
