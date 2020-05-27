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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004688"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="068cf-102">IMetaDataEmit::DefineImportType, méthode</span><span class="sxs-lookup"><span data-stu-id="068cf-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="068cf-103">Crée une référence au type spécifié qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.</span><span class="sxs-lookup"><span data-stu-id="068cf-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="068cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="068cf-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="068cf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="068cf-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="068cf-106">dans Interface [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) qui représente l’assembly à partir duquel le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="068cf-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="068cf-107">dans Tableau qui contient le hachage de l’assembly spécifié par `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="068cf-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="068cf-108">[in] Nombre d'octets dans le tableau `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="068cf-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="068cf-109">dans Interface [IMetaDataImport](imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="068cf-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="068cf-110">dans `mdTypeDef`Jeton qui spécifie le type de cible.</span><span class="sxs-lookup"><span data-stu-id="068cf-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="068cf-111">dans Interface [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) qui représente l’assembly dans lequel le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="068cf-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="068cf-112">à `mdTypeRef`Jeton qui est défini dans la portée actuelle pour la référence de type.</span><span class="sxs-lookup"><span data-stu-id="068cf-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="068cf-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="068cf-113">Remarks</span></span>  
 <span data-ttu-id="068cf-114">Avant d’appeler la méthode [IMetaDataEmit ::D efineimportmember](imetadataemit-defineimportmember-method.md) , vous pouvez utiliser la `DefineImportType` méthode pour créer une référence de type, dans la portée actuelle, pour la classe parente ou l’interface parente du membre.</span><span class="sxs-lookup"><span data-stu-id="068cf-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="068cf-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="068cf-115">Requirements</span></span>  
 <span data-ttu-id="068cf-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="068cf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="068cf-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="068cf-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="068cf-118">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="068cf-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="068cf-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="068cf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="068cf-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="068cf-120">See also</span></span>

- [<span data-ttu-id="068cf-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="068cf-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="068cf-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="068cf-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
