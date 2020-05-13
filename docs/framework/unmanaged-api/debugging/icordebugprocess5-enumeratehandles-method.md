---
title: ICorDebugProcess5::EnumerateHandles, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: 291b384d6f0c8c1404b380c653693ec65fcfc960
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213411"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="d4500-102">ICorDebugProcess5::EnumerateHandles, méthode</span><span class="sxs-lookup"><span data-stu-id="d4500-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="d4500-103">Obtient un énumérateur pour les handles d’objet dans un processus.</span><span class="sxs-lookup"><span data-stu-id="d4500-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4500-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4500-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4500-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4500-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="d4500-106">dans Combinaison d’opérations de bits de valeurs [corgcreferencetype,](corgcreferencetype-enumeration.md) qui spécifient le type de handles à inclure dans la collection.</span><span class="sxs-lookup"><span data-stu-id="d4500-106">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="d4500-107">à Pointeur vers l’adresse d’un [icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md) qui est un énumérateur pour les objets qui doivent être récupérés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="d4500-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4500-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d4500-108">Remarks</span></span>  
 <span data-ttu-id="d4500-109">`EnumerateHandles`est une fonction d’assistance qui prend en charge l’inspection de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="d4500-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="d4500-110">Elle est similaire à la méthode [ICorDebugProcess5 :: enumerategcreferences,](icordebugprocess5-enumerategcreferences-method.md) , à ceci près qu’au lieu de remplir une collection [icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md) avec tous les objets qui doivent être récupérés par le garbage collector, elle comprend uniquement les objets qui ont des descripteurs de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="d4500-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="d4500-111">Le `types` paramètre spécifie les types de handles à inclure dans la collection.</span><span class="sxs-lookup"><span data-stu-id="d4500-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="d4500-112">`types`Il peut s’agir de l’un des trois membres suivants de l’énumération [corgcreferencetype,](corgcreferencetype-enumeration.md) :</span><span class="sxs-lookup"><span data-stu-id="d4500-112">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="d4500-113">`CorHandleStrongOnly`(Handles vers des références fortes uniquement).</span><span class="sxs-lookup"><span data-stu-id="d4500-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="d4500-114">`CorHandleWeakOnly`(Handles vers des références faibles uniquement).</span><span class="sxs-lookup"><span data-stu-id="d4500-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="d4500-115">`CorHandleAll`(tous les descripteurs).</span><span class="sxs-lookup"><span data-stu-id="d4500-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4500-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d4500-116">Requirements</span></span>  
 <span data-ttu-id="d4500-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4500-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4500-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4500-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4500-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4500-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4500-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4500-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4500-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4500-121">See also</span></span>

- [<span data-ttu-id="d4500-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="d4500-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="d4500-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="d4500-123">Debugging</span></span>](index.md)
