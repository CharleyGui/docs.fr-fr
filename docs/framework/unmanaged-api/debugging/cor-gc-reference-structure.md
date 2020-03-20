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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179316"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="9b952-102">COR_GC_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="9b952-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="9b952-103">Contient des informations sur un objet qui doit faire l'objet d'une récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="9b952-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b952-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b952-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="9b952-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9b952-105">Members</span></span>  
  
|<span data-ttu-id="9b952-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9b952-106">Member</span></span>|<span data-ttu-id="9b952-107">Description</span><span class="sxs-lookup"><span data-stu-id="9b952-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="9b952-108">Un pointeur vers le domaine d’application auquel appartient la poignée ou l’objet.</span><span class="sxs-lookup"><span data-stu-id="9b952-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="9b952-109">Sa valeur `null`peut être .</span><span class="sxs-lookup"><span data-stu-id="9b952-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="9b952-110">Soit une ICorDebugValue, soit une interface ICorDebugReferenceValue qui correspond à l’objet à collecter.</span><span class="sxs-lookup"><span data-stu-id="9b952-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="9b952-111">Une valeur d’énumération [CorGCReferenceType](corgcreferencetype-enumeration.md) qui indique d’où vient la racine.</span><span class="sxs-lookup"><span data-stu-id="9b952-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="9b952-112">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="9b952-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="9b952-113">Des données supplémentaires sur l’objet à collecter.</span><span class="sxs-lookup"><span data-stu-id="9b952-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="9b952-114">Ces informations dépendent de la source de `type` l’objet, comme indiqué par le champ.</span><span class="sxs-lookup"><span data-stu-id="9b952-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="9b952-115">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="9b952-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b952-116">Notes </span><span class="sxs-lookup"><span data-stu-id="9b952-116">Remarks</span></span>  
 <span data-ttu-id="9b952-117">Le `type` champ est une valeur de recensement [CorGCReferenceType](corgcreferencetype-enumeration.md) qui indique d’où vient la référence.</span><span class="sxs-lookup"><span data-stu-id="9b952-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="9b952-118">Une `COR_GC_REFERENCE` valeur particulière peut refléter n’importe lequel des types suivants d’objets gérés :</span><span class="sxs-lookup"><span data-stu-id="9b952-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="9b952-119">Objets de toutes les`CorGCReferenceType.CorReferenceStack`piles gérées ( ).</span><span class="sxs-lookup"><span data-stu-id="9b952-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="9b952-120">Cela inclut les références en direct dans le code géré, ainsi que les objets créés par l’heure d’exécution de la langue commune.</span><span class="sxs-lookup"><span data-stu-id="9b952-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="9b952-121">Objets de la`CorGCReferenceType.CorHandle*`table de poignée ( ).</span><span class="sxs-lookup"><span data-stu-id="9b952-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="9b952-122">Cela comprend des`HNDTYPE_STRONG` `HNDTYPE_REFCOUNT`références fortes ( et ) et des variables statiques dans un module.</span><span class="sxs-lookup"><span data-stu-id="9b952-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="9b952-123">Objets de la file`CorGCReferenceType.CorReferenceFinalizer`d’attente finalisateur ( ).</span><span class="sxs-lookup"><span data-stu-id="9b952-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="9b952-124">La file d’attente de finalisation racines objets jusqu’à ce que le finalizer a couru.</span><span class="sxs-lookup"><span data-stu-id="9b952-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="9b952-125">Le `extraData` champ contient des données supplémentaires en fonction de la source (ou du type) de la référence.</span><span class="sxs-lookup"><span data-stu-id="9b952-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="9b952-126">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9b952-126">Possible values are:</span></span>  
  
- <span data-ttu-id="9b952-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="9b952-127">`DependentSource`.</span></span> <span data-ttu-id="9b952-128">Si `type` l’est `CorGCREferenceType.CorHandleStrongDependent`, ce champ est l’objet qui, si `COR_GC_REFERENCE.Location`vivant, racines de l’objet à collecter à la poubelle à .</span><span class="sxs-lookup"><span data-stu-id="9b952-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="9b952-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="9b952-129">`RefCount`.</span></span> <span data-ttu-id="9b952-130">Si `type` le `CorGCREferenceType.CorHandleStrongRefCount`est , ce champ est le nombre de références de la poignée.</span><span class="sxs-lookup"><span data-stu-id="9b952-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="9b952-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="9b952-131">`Size`.</span></span> <span data-ttu-id="9b952-132">Si `type` c’est `CorGCREferenceType.CorHandleStrongSizedByref`le cas, ce champ est la dernière taille de l’arbre objet pour lequel le éboueur a calculé les racines de l’objet.</span><span class="sxs-lookup"><span data-stu-id="9b952-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="9b952-133">Notez que ce calcul n’est pas nécessairement à jour.</span><span class="sxs-lookup"><span data-stu-id="9b952-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b952-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9b952-134">Requirements</span></span>  
 <span data-ttu-id="9b952-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b952-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b952-136">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b952-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b952-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b952-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b952-138">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b952-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b952-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b952-139">See also</span></span>

- [<span data-ttu-id="9b952-140">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="9b952-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="9b952-141">Débogage</span><span class="sxs-lookup"><span data-stu-id="9b952-141">Debugging</span></span>](index.md)
