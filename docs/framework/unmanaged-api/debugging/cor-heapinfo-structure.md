---
title: COR_HEAPINFO, structure
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179309"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="b42d9-102">COR_HEAPINFO, structure</span><span class="sxs-lookup"><span data-stu-id="b42d9-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="b42d9-103">Fournit des informations générales sur le tas du récupérateur de mémoire, y compris s’il est ou non énumérable.</span><span class="sxs-lookup"><span data-stu-id="b42d9-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b42d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b42d9-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b42d9-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b42d9-105">Members</span></span>  
  
|<span data-ttu-id="b42d9-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b42d9-106">Member</span></span>|<span data-ttu-id="b42d9-107">Description</span><span class="sxs-lookup"><span data-stu-id="b42d9-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="b42d9-108">`true`si les structures de collecte des ordures sont valides et que le tas peut être énuméré; autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="b42d9-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="b42d9-109">La taille, dans les octets, des pointeurs sur l’architecture cible.</span><span class="sxs-lookup"><span data-stu-id="b42d9-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="b42d9-110">Le nombre de tas logiques de collecte des ordures dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b42d9-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="b42d9-111">`TRUE`si la collecte simultanée des ordures (arrière-plan) est activée; autrement, `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="b42d9-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="b42d9-112">Un membre du [recensement CorDebugGCType](cordebuggctype-enumeration.md) qui indique si le collecteur d’ordures fonctionne sur un poste de travail ou un serveur.</span><span class="sxs-lookup"><span data-stu-id="b42d9-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b42d9-113">Notes </span><span class="sxs-lookup"><span data-stu-id="b42d9-113">Remarks</span></span>  
 <span data-ttu-id="b42d9-114">Un exemple `COR_HEAPINFO` de la structure est retourné en appelant le [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="b42d9-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="b42d9-115">Avant d’énumérer les objets sur le tas `areGCStructuresValid` de collecte des ordures, vous devez toujours vérifier le champ pour vous assurer que le tas est dans un état enumerable.</span><span class="sxs-lookup"><span data-stu-id="b42d9-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="b42d9-116">Pour plus d’informations, voir la méthode [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)</span><span class="sxs-lookup"><span data-stu-id="b42d9-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b42d9-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b42d9-117">Requirements</span></span>  
 <span data-ttu-id="b42d9-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b42d9-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b42d9-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b42d9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b42d9-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b42d9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b42d9-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b42d9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42d9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b42d9-122">See also</span></span>

- [<span data-ttu-id="b42d9-123">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="b42d9-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="b42d9-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="b42d9-124">Debugging</span></span>](index.md)
