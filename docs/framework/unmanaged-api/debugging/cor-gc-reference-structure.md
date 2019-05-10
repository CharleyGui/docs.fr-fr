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
ms.openlocfilehash: 848765a4ea9657020bd84e476f992ae69750dda9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617692"
---
# <a name="corgcreference-structure"></a><span data-ttu-id="9d59b-102">COR_GC_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="9d59b-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="9d59b-103">Contient des informations sur un objet qui doit faire l'objet d'une récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="9d59b-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d59b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d59b-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="9d59b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9d59b-105">Members</span></span>  
  
|<span data-ttu-id="9d59b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9d59b-106">Member</span></span>|<span data-ttu-id="9d59b-107">Description</span><span class="sxs-lookup"><span data-stu-id="9d59b-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="9d59b-108">Pointeur vers le domaine d’application à laquelle appartient l’objet ou un handle.</span><span class="sxs-lookup"><span data-stu-id="9d59b-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="9d59b-109">Sa valeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="9d59b-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="9d59b-110">ICorDebugValue ou une interface ICorDebugReferenceValue qui correspond à l’objet d’être le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="9d59b-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="9d59b-111">Un [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valeur d’énumération qui indique la provenance de la racine.</span><span class="sxs-lookup"><span data-stu-id="9d59b-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="9d59b-112">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="9d59b-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="9d59b-113">Données supplémentaires sur l’objet de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="9d59b-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="9d59b-114">Ces informations dépendent de la source de l’objet, comme indiqué par le `type` champ.</span><span class="sxs-lookup"><span data-stu-id="9d59b-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="9d59b-115">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="9d59b-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d59b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="9d59b-116">Remarks</span></span>  
 <span data-ttu-id="9d59b-117">Le `type` champ est un [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valeur d’énumération qui indique la provenance de la référence.</span><span class="sxs-lookup"><span data-stu-id="9d59b-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="9d59b-118">Un particulier `COR_GC_REFERENCE` valeur peut refléter un des types suivants d’objets gérés :</span><span class="sxs-lookup"><span data-stu-id="9d59b-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="9d59b-119">Objets à partir de toutes les piles gérées (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="9d59b-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="9d59b-120">Cela inclut des références en direct dans le code managé, ainsi que les objets créés par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9d59b-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="9d59b-121">Objets à partir de la table de handles (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="9d59b-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="9d59b-122">Cela inclut des références fortes (`HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT`) et les variables statiques dans un module.</span><span class="sxs-lookup"><span data-stu-id="9d59b-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="9d59b-123">Objets à partir de la file d’attente du finaliseur (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="9d59b-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="9d59b-124">La file d’attente du finaliseur racines des objets jusqu'à ce que le finaliseur s’est exécutée.</span><span class="sxs-lookup"><span data-stu-id="9d59b-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="9d59b-125">Le `extraData` champ contient des données supplémentaires en fonction de la source (ou type) de la référence.</span><span class="sxs-lookup"><span data-stu-id="9d59b-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="9d59b-126">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="9d59b-126">Possible values are:</span></span>  
  
- <span data-ttu-id="9d59b-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="9d59b-127">`DependentSource`.</span></span> <span data-ttu-id="9d59b-128">Si le `type` est `CorGCREferenceType.CorHandleStrongDependent`, ce champ est l’objet qui, si elle est actif, de l’objet pour le garbage collector à racines `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="9d59b-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="9d59b-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="9d59b-129">`RefCount`.</span></span> <span data-ttu-id="9d59b-130">Si le `type` est `CorGCREferenceType.CorHandleStrongRefCount`, ce champ est le nombre de références du handle.</span><span class="sxs-lookup"><span data-stu-id="9d59b-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="9d59b-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="9d59b-131">`Size`.</span></span> <span data-ttu-id="9d59b-132">Si le `type` est `CorGCREferenceType.CorHandleStrongSizedByref`, ce champ est la dernière taille de l’arborescence de l’objet pour lequel le garbage collector calculé les racines de l’objet.</span><span class="sxs-lookup"><span data-stu-id="9d59b-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="9d59b-133">Notez que ce calcul n’est pas nécessairement à jour.</span><span class="sxs-lookup"><span data-stu-id="9d59b-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d59b-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d59b-134">Requirements</span></span>  
 <span data-ttu-id="9d59b-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d59b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d59b-136">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d59b-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d59b-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d59b-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d59b-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d59b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d59b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d59b-139">See also</span></span>

- [<span data-ttu-id="9d59b-140">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="9d59b-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="9d59b-141">Débogage</span><span class="sxs-lookup"><span data-stu-id="9d59b-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
