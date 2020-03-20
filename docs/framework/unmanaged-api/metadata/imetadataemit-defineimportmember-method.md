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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175861"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="d4bcf-102">IMetaDataEmit::DefineImportMember, méthode</span><span class="sxs-lookup"><span data-stu-id="d4bcf-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="d4bcf-103">Crée une référence au membre spécifié d’un type ou d’un module qui est défini en dehors de la portée actuelle, et définit un jeton pour cette référence.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4bcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4bcf-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d4bcf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4bcf-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="d4bcf-106">[dans] Une interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) qui représente l’assemblage à partir duquel le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="d4bcf-107">[dans] Un tableau qui contient le hachage pour l’assemblage spécifié par `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="d4bcf-108">[in] Nombre d'octets dans le tableau `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="d4bcf-109">[dans] Une interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="d4bcf-110">[dans] Le jeton des métadonnées qui spécifie le membre cible.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="d4bcf-111">Le jeton peut `mdMethodDef` être un jeton (pour une méthode membre), `mdProperty` (pour une propriété membre), ou `mdFieldDef` (pour un champ membre) jeton.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="d4bcf-112">[dans] Une interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) qui représente l’assemblage dans lequel le membre cible est importé.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="d4bcf-113">[dans] Le `mdTypeRef` `mdModuleRef` ou le jeton pour le type ou le module, respectivement, qui possède le membre cible.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="d4bcf-114">[out] Le `mdMemberRef` jeton qui est défini dans la portée actuelle de la référence du membre.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4bcf-115">Notes </span><span class="sxs-lookup"><span data-stu-id="d4bcf-115">Remarks</span></span>  
 <span data-ttu-id="d4bcf-116">La `DefineImportMember` méthode recherche le membre, spécifié par `mbMember`, qui `pImport`est défini dans une autre portée, spécifiée par , et récupère ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="d4bcf-117">Il utilise ces informations pour appeler la méthode [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) dans la portée actuelle pour créer la référence des membres.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="d4bcf-118">En général, avant `DefineImportMember` d’utiliser la méthode, vous devez créer, dans la portée actuelle, une référence type ou une référence de module pour la classe, l’interface ou le module parent du membre cible.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="d4bcf-119">Le jeton des métadonnées pour `tkParent` cette référence est ensuite adopté dans l’argument.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="d4bcf-120">Vous n’avez pas besoin de créer une référence au parent du membre cible si elle sera résolue plus tard par le compilateur ou le lien.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="d4bcf-121">Pour résumer :</span><span class="sxs-lookup"><span data-stu-id="d4bcf-121">To summarize:</span></span>  
  
- <span data-ttu-id="d4bcf-122">Si le membre cible est un champ ou une méthode, utilisez soit la méthode [IMetaDataEmit: :DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou la méthode [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) pour créer une référence type, dans la portée actuelle, pour la classe mère du membre ou l’interface parente.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="d4bcf-123">Si le membre cible est une fonction variable ou globale globale globale (c’est-à-dire non membre d’une classe ou d’une interface), utilisez la méthode [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) pour créer une référence de module, dans la portée actuelle, pour le module parent du membre.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="d4bcf-124">Si le parent du membre cible sera résolu plus tard par le `mdTokenNil` `tkParent`compilateur ou le lien, puis passez dedans .</span><span class="sxs-lookup"><span data-stu-id="d4bcf-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="d4bcf-125">Le seul scénario dans lequel cela s’applique est quand une fonction globale ou une variable globale est importée à partir d’un fichier .obj qui sera finalement lié dans le module actuel et les métadonnées fusionnées.</span><span class="sxs-lookup"><span data-stu-id="d4bcf-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4bcf-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d4bcf-126">Requirements</span></span>  
 <span data-ttu-id="d4bcf-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4bcf-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4bcf-128">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="d4bcf-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4bcf-129">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4bcf-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4bcf-130">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4bcf-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bcf-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4bcf-131">See also</span></span>

- [<span data-ttu-id="d4bcf-132">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d4bcf-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d4bcf-133">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d4bcf-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
