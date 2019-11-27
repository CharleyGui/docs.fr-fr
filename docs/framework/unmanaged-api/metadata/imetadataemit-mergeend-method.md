---
title: IMetaDataEmit::MergeEnd, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: 34ecfc2f01f22971e135358806adeea632e02f8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448029"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="2bf56-102">IMetaDataEmit::MergeEnd, méthode</span><span class="sxs-lookup"><span data-stu-id="2bf56-102">IMetaDataEmit::MergeEnd Method</span></span>

<span data-ttu-id="2bf56-103">Fusionne dans la portée actuelle toutes les portées de métadonnées spécifiées par un ou plusieurs appels antérieurs à [IMetaDataEmit :: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="2bf56-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="2bf56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bf56-104">Syntax</span></span>

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a><span data-ttu-id="2bf56-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2bf56-105">Parameters</span></span>

<span data-ttu-id="2bf56-106">Cette méthode n’accepte aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="2bf56-106">This method takes no parameters.</span></span>

## <a name="remarks"></a><span data-ttu-id="2bf56-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2bf56-107">Remarks</span></span>

<span data-ttu-id="2bf56-108">Cette routine déclenche la fusion réelle des métadonnées, de toutes les étendues d’importation spécifiées par les appels précédents à `IMetaDataEmit::Merge`, dans l’étendue de sortie actuelle.</span><span class="sxs-lookup"><span data-stu-id="2bf56-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>

<span data-ttu-id="2bf56-109">Les conditions spéciales suivantes s’appliquent à la fusion :</span><span class="sxs-lookup"><span data-stu-id="2bf56-109">The following special conditions apply to the merge:</span></span>

- <span data-ttu-id="2bf56-110">Un identificateur de version de module (MVID) n’est jamais importé, car il est unique aux métadonnées dans la portée d’importation.</span><span class="sxs-lookup"><span data-stu-id="2bf56-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>

- <span data-ttu-id="2bf56-111">Aucune propriété existante à l’ensemble du module n’est remplacée.</span><span class="sxs-lookup"><span data-stu-id="2bf56-111">No existing module-wide properties are overwritten.</span></span>

  <span data-ttu-id="2bf56-112">Si des propriétés de module ont déjà été définies pour l’étendue actuelle, aucune propriété de module n’est importée.</span><span class="sxs-lookup"><span data-stu-id="2bf56-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="2bf56-113">Toutefois, si les propriétés du module n’ont pas été définies dans la portée actuelle, elles ne sont importées qu’une seule fois, quand elles sont rencontrées pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="2bf56-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="2bf56-114">Si ces propriétés de module sont à nouveau rencontrées, il s’agit de doublons.</span><span class="sxs-lookup"><span data-stu-id="2bf56-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="2bf56-115">Si les valeurs de toutes les propriétés de module (à l’exception de MVID) sont comparées et qu’aucun doublon n’est trouvé, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="2bf56-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>

- <span data-ttu-id="2bf56-116">Pour les définitions de type (`TypeDef`), aucun doublon n’est fusionné dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="2bf56-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="2bf56-117">les objets `TypeDef` sont recherchés en tant que doublons pour chaque *nom d’objet* complet + le *numéro de version*du *GUID* + .</span><span class="sxs-lookup"><span data-stu-id="2bf56-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="2bf56-118">S’il existe une correspondance sur un nom ou un GUID et que l’un des deux autres éléments est différent, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="2bf56-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="2bf56-119">Sinon, si les trois éléments correspondent, `MergeEnd` effectue un contrôle de curseur pour s’assurer que les entrées sont effectivement des doublons ; Si ce n’est pas le cas, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="2bf56-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="2bf56-120">Ce contrôle de curseur recherche les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2bf56-120">This cursory check looks for:</span></span>

  - <span data-ttu-id="2bf56-121">Les mêmes déclarations de membre, qui se produisent dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="2bf56-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="2bf56-122">Les membres marqués comme `mdPrivateScope` (Voir l’énumération [CorMethodAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) ) ne sont pas inclus dans cette vérification ; elles sont fusionnées de manière spéciale.</span><span class="sxs-lookup"><span data-stu-id="2bf56-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>

  - <span data-ttu-id="2bf56-123">La même disposition de classe.</span><span class="sxs-lookup"><span data-stu-id="2bf56-123">The same class layout.</span></span>

  <span data-ttu-id="2bf56-124">Cela signifie qu’un objet `TypeDef` doit toujours être défini de manière complète et cohérente dans chaque portée de métadonnées dans laquelle il est déclaré ; Si ses implémentations de membres (pour une classe) sont réparties sur plusieurs unités de compilation, la définition complète est supposée être présente dans chaque portée et non incrémentielle pour chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="2bf56-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="2bf56-125">Par exemple, si les noms de paramètres sont pertinents pour le contrat, ils doivent être émis de la même manière dans toutes les étendues ; Si elles ne sont pas pertinentes, elles ne doivent pas être émises dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2bf56-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>

  <span data-ttu-id="2bf56-126">L’exception est qu’un objet `TypeDef` peut avoir des membres incrémentiels marqués comme `mdPrivateScope`.</span><span class="sxs-lookup"><span data-stu-id="2bf56-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="2bf56-127">Si vous les rencontrez, `MergeEnd` les ajoute de manière incrémentielle à la portée actuelle sans tenir compte des doublons.</span><span class="sxs-lookup"><span data-stu-id="2bf56-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="2bf56-128">Étant donné que le compilateur comprend la portée privée, le compilateur doit être responsable de l’application des règles.</span><span class="sxs-lookup"><span data-stu-id="2bf56-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>

- <span data-ttu-id="2bf56-129">Les adresses virtuelles relatives (RVA) ne sont pas importées ou fusionnées ; le compilateur est supposé émettre à nouveau ces informations.</span><span class="sxs-lookup"><span data-stu-id="2bf56-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>

- <span data-ttu-id="2bf56-130">Les attributs personnalisés sont fusionnés uniquement lorsque l’élément auquel ils sont attachés est fusionné.</span><span class="sxs-lookup"><span data-stu-id="2bf56-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="2bf56-131">Par exemple, les attributs personnalisés associés à une classe sont fusionnés lorsque la classe est rencontrée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="2bf56-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="2bf56-132">Si des attributs personnalisés sont associés à un `TypeDef` ou `MemberDef` qui est spécifique à l’unité de compilation (telle que l’horodatage d’une compilation de membre), ils ne sont pas fusionnés et il revient au compilateur de supprimer ou de mettre à jour ces métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2bf56-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="2bf56-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2bf56-133">Requirements</span></span>

<span data-ttu-id="2bf56-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bf56-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="2bf56-135">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2bf56-135">**Header:** Cor.h</span></span>

<span data-ttu-id="2bf56-136">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2bf56-136">**Library:** Used as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="2bf56-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bf56-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2bf56-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bf56-138">See also</span></span>

- [<span data-ttu-id="2bf56-139">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="2bf56-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2bf56-140">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="2bf56-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
