---
title: IMetaDataEmit::DefineImportMember, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
ms.openlocfilehash: 75711b3d87699ff5db21a04351ff0acaccabb5aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431855"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="7e163-102">IMetaDataEmit::DefineImportMember, méthode</span><span class="sxs-lookup"><span data-stu-id="7e163-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="7e163-103">Crée une référence au membre spécifié d’un type ou d’un module qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.</span><span class="sxs-lookup"><span data-stu-id="7e163-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e163-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e163-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e163-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e163-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="7e163-106">dans Interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) qui représente l’assembly à partir duquel le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="7e163-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="7e163-107">dans Tableau qui contient le hachage de l’assembly spécifié par `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="7e163-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="7e163-108">[in] Nombre d'octets dans le tableau `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="7e163-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="7e163-109">dans Interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="7e163-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="7e163-110">dans Jeton de métadonnées qui spécifie le membre cible.</span><span class="sxs-lookup"><span data-stu-id="7e163-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="7e163-111">Le jeton peut être une `mdMethodDef` (pour une méthode membre), `mdProperty` (pour une propriété de membre) ou `mdFieldDef` (pour un champ de membre).</span><span class="sxs-lookup"><span data-stu-id="7e163-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="7e163-112">dans Interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) qui représente l’assembly dans lequel le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="7e163-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="7e163-113">dans Jeton `mdTypeRef` ou `mdModuleRef` pour le type ou le module, respectivement, qui possède le membre cible.</span><span class="sxs-lookup"><span data-stu-id="7e163-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="7e163-114">à Jeton `mdMemberRef` qui est défini dans la portée actuelle pour la référence de membre.</span><span class="sxs-lookup"><span data-stu-id="7e163-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e163-115">Notes</span><span class="sxs-lookup"><span data-stu-id="7e163-115">Remarks</span></span>  
 <span data-ttu-id="7e163-116">La méthode `DefineImportMember` recherche le membre, spécifié par `mbMember`, qui est défini dans une autre étendue, spécifié par `pImport`et récupère ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="7e163-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="7e163-117">Elle utilise ces informations pour appeler la méthode [IMetaDataEmit ::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) dans l’étendue actuelle afin de créer la référence de membre.</span><span class="sxs-lookup"><span data-stu-id="7e163-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="7e163-118">En règle générale, avant d’utiliser la méthode `DefineImportMember`, vous devez créer, dans la portée actuelle, une référence de type ou une référence de module pour la classe, l’interface ou le module parent du membre cible.</span><span class="sxs-lookup"><span data-stu-id="7e163-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="7e163-119">Le jeton de métadonnées pour cette référence est ensuite passé dans l’argument `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="7e163-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="7e163-120">Vous n’avez pas besoin de créer une référence au parent du membre cible s’il sera résolu ultérieurement par le compilateur ou l’éditeur de liens.</span><span class="sxs-lookup"><span data-stu-id="7e163-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="7e163-121">En résumé :</span><span class="sxs-lookup"><span data-stu-id="7e163-121">To summarize:</span></span>  
  
- <span data-ttu-id="7e163-122">Si le membre cible est un champ ou une méthode, utilisez la méthode [IMetaDataEmit ::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [IMetaDataEmit ::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) pour créer une référence de type, dans la portée actuelle, pour la classe parente ou l’interface parente du membre.</span><span class="sxs-lookup"><span data-stu-id="7e163-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="7e163-123">Si le membre cible est une variable globale ou une fonction globale (autrement dit, pas un membre d’une classe ou d’une interface), utilisez la méthode [IMetaDataEmit ::D efinemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) pour créer une référence de module, dans la portée actuelle, pour le module parent du membre.</span><span class="sxs-lookup"><span data-stu-id="7e163-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="7e163-124">Si le parent du membre cible sera résolu ultérieurement par le compilateur ou l’éditeur de liens, transmettez `mdTokenNil` dans `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="7e163-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="7e163-125">Le seul scénario dans lequel cela s’applique est lorsqu’une fonction globale ou une variable globale est importée à partir d’un fichier. obj qui sera finalement lié dans le module actuel et les métadonnées fusionnées.</span><span class="sxs-lookup"><span data-stu-id="7e163-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e163-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7e163-126">Requirements</span></span>  
 <span data-ttu-id="7e163-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e163-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e163-128">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7e163-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e163-129">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7e163-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e163-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e163-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e163-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e163-131">See also</span></span>

- [<span data-ttu-id="7e163-132">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7e163-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7e163-133">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="7e163-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
