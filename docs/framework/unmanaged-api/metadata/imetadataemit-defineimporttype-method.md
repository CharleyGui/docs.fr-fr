---
title: IMetaDataEmit::DefineImportType, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff0660ef2b30e32af540fe7bef5936ab6d0a359f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777626"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="ad692-102">IMetaDataEmit::DefineImportType, méthode</span><span class="sxs-lookup"><span data-stu-id="ad692-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="ad692-103">Crée une référence au type spécifié qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.</span><span class="sxs-lookup"><span data-stu-id="ad692-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad692-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad692-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad692-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad692-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="ad692-106">[in] Un [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface qui représente l’assembly à partir duquel le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="ad692-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="ad692-107">[in] Un tableau qui contient le hachage pour l’assembly spécifié par `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="ad692-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="ad692-108">[in] Nombre d'octets dans le tableau `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="ad692-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="ad692-109">[in] Un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface qui représente la portée des métadonnées à partir de laquelle le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="ad692-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="ad692-110">[in] Un `mdTypeDef` jeton qui spécifie le type de cible.</span><span class="sxs-lookup"><span data-stu-id="ad692-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="ad692-111">[in] Un [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface qui représente l’assembly dans lequel le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="ad692-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="ad692-112">[out] Le `mdTypeRef` jeton qui est défini dans l’étendue actuelle pour la référence de type.</span><span class="sxs-lookup"><span data-stu-id="ad692-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad692-113">Notes</span><span class="sxs-lookup"><span data-stu-id="ad692-113">Remarks</span></span>  
 <span data-ttu-id="ad692-114">Avant d’appeler le [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) (méthode), vous pouvez utiliser la `DefineImportType` méthode pour créer une référence de type, dans la portée actuelle, pour la classe parente ou l’interface parente du membre.</span><span class="sxs-lookup"><span data-stu-id="ad692-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad692-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ad692-115">Requirements</span></span>  
 <span data-ttu-id="ad692-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad692-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad692-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad692-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad692-118">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad692-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad692-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad692-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad692-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad692-120">See also</span></span>

- [<span data-ttu-id="ad692-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ad692-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ad692-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ad692-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
