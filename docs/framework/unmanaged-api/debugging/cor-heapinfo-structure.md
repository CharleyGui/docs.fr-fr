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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd233643bd18b60b7d6176c34ee57e4061daf7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740654"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="a6866-102">COR_HEAPINFO, structure</span><span class="sxs-lookup"><span data-stu-id="a6866-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="a6866-103">Fournit des informations générales sur le tas du récupérateur de mémoire, y compris s’il est ou non énumérable.</span><span class="sxs-lookup"><span data-stu-id="a6866-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6866-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6866-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a6866-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a6866-105">Members</span></span>  
  
|<span data-ttu-id="a6866-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a6866-106">Member</span></span>|<span data-ttu-id="a6866-107">Description</span><span class="sxs-lookup"><span data-stu-id="a6866-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="a6866-108">`true` Si les structures de garbage collection sont valides et peuvent être énuméré le tas ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="a6866-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="a6866-109">La taille, en octets, des pointeurs de sur l’architecture cible.</span><span class="sxs-lookup"><span data-stu-id="a6866-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="a6866-110">Le nombre de nettoyage de la logique segments de mémoire dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a6866-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="a6866-111">`TRUE` Si simultanées (arrière-plan) le garbage collection est activé ; Sinon, `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="a6866-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="a6866-112">Un membre de la [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) énumération qui indique si le garbage collector s’exécute sur une station de travail ou un serveur.</span><span class="sxs-lookup"><span data-stu-id="a6866-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6866-113">Notes</span><span class="sxs-lookup"><span data-stu-id="a6866-113">Remarks</span></span>  
 <span data-ttu-id="a6866-114">Une instance de la `COR_HEAPINFO` structure est retournée en appelant le [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="a6866-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="a6866-115">Avant de l’énumération des objets sur le tas de garbage collection, vous devez toujours vérifier le `areGCStructuresValid` champ pour vous assurer que le tas est dans un état énumérable.</span><span class="sxs-lookup"><span data-stu-id="a6866-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="a6866-116">Pour plus d’informations, consultez le [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="a6866-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6866-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6866-117">Requirements</span></span>  
 <span data-ttu-id="a6866-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6866-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6866-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6866-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6866-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6866-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6866-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6866-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6866-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6866-122">See also</span></span>

- [<span data-ttu-id="a6866-123">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="a6866-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="a6866-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="a6866-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
