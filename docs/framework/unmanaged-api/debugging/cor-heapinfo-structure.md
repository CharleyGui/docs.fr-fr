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
ms.openlocfilehash: f7b340a73aa9eaebca9c0d78563ae298557039b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274189"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="53a23-102">COR_HEAPINFO, structure</span><span class="sxs-lookup"><span data-stu-id="53a23-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="53a23-103">Fournit des informations générales sur le tas du récupérateur de mémoire, y compris s’il est ou non énumérable.</span><span class="sxs-lookup"><span data-stu-id="53a23-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53a23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53a23-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="53a23-105">Membres</span><span class="sxs-lookup"><span data-stu-id="53a23-105">Members</span></span>  
  
|<span data-ttu-id="53a23-106">Membre</span><span class="sxs-lookup"><span data-stu-id="53a23-106">Member</span></span>|<span data-ttu-id="53a23-107">Description</span><span class="sxs-lookup"><span data-stu-id="53a23-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="53a23-108">`true`Si les structures garbage collection sont valides et que le tas peut être énuméré ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="53a23-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="53a23-109">Taille, en octets, des pointeurs sur l’architecture cible.</span><span class="sxs-lookup"><span data-stu-id="53a23-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="53a23-110">Nombre de tas de garbage collection logiques dans le processus.</span><span class="sxs-lookup"><span data-stu-id="53a23-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="53a23-111">`TRUE`Si la garbage collection simultanée (arrière-plan) est activée ; Sinon, `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="53a23-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="53a23-112">Membre de l’énumération [cordebuggctype,](cordebuggctype-enumeration.md) qui indique si le garbage collector s’exécute sur une station de travail ou sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="53a23-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53a23-113">Notes</span><span class="sxs-lookup"><span data-stu-id="53a23-113">Remarks</span></span>  
 <span data-ttu-id="53a23-114">Une instance de la `COR_HEAPINFO` structure est retournée en appelant la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53a23-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="53a23-115">Avant d’énumérer des objets sur le tas garbage collection, vous devez toujours `areGCStructuresValid` vérifier le champ pour vous assurer que le tas est dans un État énumérable.</span><span class="sxs-lookup"><span data-stu-id="53a23-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="53a23-116">Pour plus d’informations, consultez la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53a23-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53a23-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="53a23-117">Requirements</span></span>  
 <span data-ttu-id="53a23-118">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53a23-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53a23-119">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="53a23-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53a23-120">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53a23-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53a23-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53a23-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53a23-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53a23-122">See also</span></span>

- [<span data-ttu-id="53a23-123">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="53a23-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="53a23-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="53a23-124">Debugging</span></span>](index.md)
