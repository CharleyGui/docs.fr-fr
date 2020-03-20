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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177678"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="e8ddb-102">IMetaDataEmit::DefineImportType, méthode</span><span class="sxs-lookup"><span data-stu-id="e8ddb-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="e8ddb-103">Crée une référence au type spécifié qui est défini en dehors de la portée actuelle, et définit un jeton pour cette référence.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ddb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8ddb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e8ddb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8ddb-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="e8ddb-106">[dans] Une interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) qui représente l’assemblage à partir duquel le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="e8ddb-107">[dans] Un tableau qui contient le hachage pour l’assemblage spécifié par `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="e8ddb-108">[in] Nombre d'octets dans le tableau `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="e8ddb-109">[dans] Une interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="e8ddb-110">[dans] Un `mdTypeDef` jeton qui spécifie le type de cible.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="e8ddb-111">[dans] Une interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) qui représente l’assemblage dans lequel le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="e8ddb-112">[out] Le `mdTypeRef` jeton qui est défini dans la portée actuelle pour la référence de type.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8ddb-113">Notes </span><span class="sxs-lookup"><span data-stu-id="e8ddb-113">Remarks</span></span>  
 <span data-ttu-id="e8ddb-114">Avant d’appeler la méthode [IMetaDataEmit::DefineImportMember,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) vous `DefineImportType` pouvez utiliser la méthode pour créer une référence type, dans la portée actuelle, pour la classe mère du membre ou l’interface parente.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ddb-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8ddb-115">Requirements</span></span>  
 <span data-ttu-id="e8ddb-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ddb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ddb-117">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="e8ddb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8ddb-118">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8ddb-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8ddb-119">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ddb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ddb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8ddb-120">See also</span></span>

- [<span data-ttu-id="e8ddb-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e8ddb-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e8ddb-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e8ddb-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
