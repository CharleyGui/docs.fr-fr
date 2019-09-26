---
title: COR_GC_REFERENCE, structure
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc0b67621f77c0741e0b63b84ab1794530d6280b
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274223"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="1d673-102">COR_GC_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="1d673-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="1d673-103">Contient des informations sur un objet qui doit faire l'objet d'une récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="1d673-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d673-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d673-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="1d673-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1d673-105">Members</span></span>  
  
|<span data-ttu-id="1d673-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1d673-106">Member</span></span>|<span data-ttu-id="1d673-107">Description</span><span class="sxs-lookup"><span data-stu-id="1d673-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="1d673-108">Pointeur vers le domaine d’application auquel le handle ou l’objet appartient.</span><span class="sxs-lookup"><span data-stu-id="1d673-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="1d673-109">Sa valeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="1d673-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="1d673-110">Une interface ICorDebugValue ou ICorDebugReferenceValue qui correspond à l’objet devant faire l’objet d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1d673-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="1d673-111">Valeur d’énumération [corgcreferencetype,](corgcreferencetype-enumeration.md) qui indique où provient la racine.</span><span class="sxs-lookup"><span data-stu-id="1d673-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="1d673-112">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="1d673-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="1d673-113">Données supplémentaires sur l’objet qui doit être récupéré par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="1d673-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="1d673-114">Ces informations dépendent de la source de l’objet, comme indiqué par le `type` champ.</span><span class="sxs-lookup"><span data-stu-id="1d673-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="1d673-115">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="1d673-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d673-116">Notes</span><span class="sxs-lookup"><span data-stu-id="1d673-116">Remarks</span></span>  
 <span data-ttu-id="1d673-117">Le `type` champ est une valeur d’énumération [corgcreferencetype,](corgcreferencetype-enumeration.md) qui indique l’origine de la référence.</span><span class="sxs-lookup"><span data-stu-id="1d673-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="1d673-118">Une valeur `COR_GC_REFERENCE` particulière peut refléter l’un des types d’objets managés suivants :</span><span class="sxs-lookup"><span data-stu-id="1d673-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="1d673-119">Objets de toutes les piles managées`CorGCReferenceType.CorReferenceStack`().</span><span class="sxs-lookup"><span data-stu-id="1d673-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="1d673-120">Cela comprend les références dynamiques en code managé, ainsi que les objets créés par l’common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1d673-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="1d673-121">Objets de la table de handles (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="1d673-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="1d673-122">Cela comprend des références fortes`HNDTYPE_STRONG` ( `HNDTYPE_REFCOUNT`et) et des variables statiques dans un module.</span><span class="sxs-lookup"><span data-stu-id="1d673-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="1d673-123">Objets de la file d’attente du`CorGCReferenceType.CorReferenceFinalizer`finaliseur ().</span><span class="sxs-lookup"><span data-stu-id="1d673-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="1d673-124">Le finaliseur met les objets racine en file d’attente jusqu’à l’exécution du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="1d673-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="1d673-125">Le `extraData` champ contient des données supplémentaires en fonction de la source (ou du type) de la référence.</span><span class="sxs-lookup"><span data-stu-id="1d673-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="1d673-126">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="1d673-126">Possible values are:</span></span>  
  
- <span data-ttu-id="1d673-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="1d673-127">`DependentSource`.</span></span> <span data-ttu-id="1d673-128">Si le `type` est `CorGCREferenceType.CorHandleStrongDependent`, ce champ est l’objet qui, s’il est actif, racine l’objet à `COR_GC_REFERENCE.Location`nettoyer.</span><span class="sxs-lookup"><span data-stu-id="1d673-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="1d673-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="1d673-129">`RefCount`.</span></span> <span data-ttu-id="1d673-130">`type` Si est `CorGCREferenceType.CorHandleStrongRefCount`, ce champ est le décompte de références du handle.</span><span class="sxs-lookup"><span data-stu-id="1d673-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="1d673-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="1d673-131">`Size`.</span></span> <span data-ttu-id="1d673-132">`type` Si est `CorGCREferenceType.CorHandleStrongSizedByref`, ce champ est la dernière taille de l’arborescence d’objets pour laquelle le garbage collector a calculé les racines de l’objet.</span><span class="sxs-lookup"><span data-stu-id="1d673-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="1d673-133">Notez que ce calcul n’est pas nécessairement à jour.</span><span class="sxs-lookup"><span data-stu-id="1d673-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d673-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1d673-134">Requirements</span></span>  
 <span data-ttu-id="1d673-135">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d673-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d673-136">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1d673-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d673-137">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d673-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d673-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d673-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d673-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d673-139">See also</span></span>

- [<span data-ttu-id="1d673-140">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="1d673-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="1d673-141">Débogage</span><span class="sxs-lookup"><span data-stu-id="1d673-141">Debugging</span></span>](index.md)
