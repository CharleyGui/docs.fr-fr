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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8851b3090685b19c4a7ef711d5adab232e46872e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665037"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="d2faf-102">IMetaDataEmit::DefineImportMember, méthode</span><span class="sxs-lookup"><span data-stu-id="d2faf-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="d2faf-103">Crée une référence au membre spécifié d’un type ou un module qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.</span><span class="sxs-lookup"><span data-stu-id="d2faf-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2faf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2faf-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="d2faf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2faf-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="d2faf-106">[in] Un [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface qui représente l’assembly à partir duquel le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="d2faf-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="d2faf-107">[in] Un tableau qui contient le hachage pour l’assembly spécifié par `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="d2faf-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="d2faf-108">[in] Nombre d'octets dans le tableau `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="d2faf-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="d2faf-109">[in] Un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface qui représente la portée des métadonnées à partir duquel le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="d2faf-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="d2faf-110">[in] Le jeton de métadonnées qui spécifie le membre cible.</span><span class="sxs-lookup"><span data-stu-id="d2faf-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="d2faf-111">Le jeton peut être un `mdMethodDef` (pour une méthode membre), `mdProperty` (pour une propriété de membre) ou `mdFieldDef` (pour un champ de membre) jeton.</span><span class="sxs-lookup"><span data-stu-id="d2faf-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="d2faf-112">[in] Un [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface qui représente l’assembly dans lequel le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="d2faf-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="d2faf-113">[in] Le `mdTypeRef` ou `mdModuleRef` jeton pour le type ou le module, respectivement, qui possède le membre cible.</span><span class="sxs-lookup"><span data-stu-id="d2faf-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="d2faf-114">[out] Le `mdMemberRef` jeton qui est défini dans la portée actuelle pour la référence de membre.</span><span class="sxs-lookup"><span data-stu-id="d2faf-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2faf-115">Notes</span><span class="sxs-lookup"><span data-stu-id="d2faf-115">Remarks</span></span>  
 <span data-ttu-id="d2faf-116">Le `DefineImportMember` méthode recherche le membre spécifié par `mbMember`, qui est défini dans une autre portée spécifiée par `pImport`et récupère ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="d2faf-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="d2faf-117">Il utilise ces informations pour appeler le [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) méthode dans la portée actuelle pour créer la référence de membre.</span><span class="sxs-lookup"><span data-stu-id="d2faf-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="d2faf-118">En règle générale, avant d’utiliser le `DefineImportMember` (méthode), vous devez créer, dans la portée actuelle, une référence de type ou la référence de module pour le membre cible parent classe, interface ou le module.</span><span class="sxs-lookup"><span data-stu-id="d2faf-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="d2faf-119">Le jeton de métadonnées pour cette référence est ensuite passé dans le `tkParent` argument.</span><span class="sxs-lookup"><span data-stu-id="d2faf-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="d2faf-120">Vous n’avez pas besoin créer une référence au parent du membre cible si elle doit être résolu ultérieurement par le compilateur ou l’éditeur de liens.</span><span class="sxs-lookup"><span data-stu-id="d2faf-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="d2faf-121">Pour récapituler :</span><span class="sxs-lookup"><span data-stu-id="d2faf-121">To summarize:</span></span>  
  
- <span data-ttu-id="d2faf-122">Si le membre cible est un champ ou une méthode, utilisez la [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) méthode pour créer une référence de type, dans la portée actuelle, pour le classe parente ou l’interface parente du membre.</span><span class="sxs-lookup"><span data-stu-id="d2faf-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="d2faf-123">Si le membre cible est une fonction globale ou de variable globale (autrement dit, pas un membre d’une classe ou une interface), utilisez le [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) pour créer une référence de module, dans la portée actuelle, pour le parent du membre (méthode) module.</span><span class="sxs-lookup"><span data-stu-id="d2faf-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="d2faf-124">Si le parent du membre cible doit être résolu ultérieurement par le compilateur ou l’éditeur de liens, puis passer `mdTokenNil` dans `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="d2faf-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="d2faf-125">Le seul scénario dans lequel cela s’applique est lorsqu’une fonction globale ou variable globale est en cours d’importation à partir d’un fichier .obj qui sera finalement lié dans le module actuel, et les métadonnées fusionnées.</span><span class="sxs-lookup"><span data-stu-id="d2faf-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2faf-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2faf-126">Requirements</span></span>  
 <span data-ttu-id="d2faf-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2faf-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2faf-128">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d2faf-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2faf-129">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2faf-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2faf-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2faf-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2faf-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2faf-131">See also</span></span>

- [<span data-ttu-id="d2faf-132">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d2faf-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d2faf-133">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d2faf-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
