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
ms.openlocfilehash: 94ce4443be210fdfeb1bab197c3e603255e1cc4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723244"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="7ec58-102">IMetaDataEmit::DefineImportType, méthode</span><span class="sxs-lookup"><span data-stu-id="7ec58-102">IMetaDataEmit::DefineImportType Method</span></span>

<span data-ttu-id="7ec58-103">Crée une référence au type spécifié qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.</span><span class="sxs-lookup"><span data-stu-id="7ec58-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ec58-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7ec58-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ec58-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="7ec58-106">dans Interface [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) qui représente l’assembly à partir duquel le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="7ec58-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="7ec58-107">dans Tableau qui contient le hachage de l’assembly spécifié par `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="7ec58-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="7ec58-108">[in] Nombre d'octets dans le tableau `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="7ec58-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="7ec58-109">dans Interface [IMetaDataImport](imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="7ec58-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="7ec58-110">dans `mdTypeDef` Jeton qui spécifie le type de cible.</span><span class="sxs-lookup"><span data-stu-id="7ec58-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="7ec58-111">dans Interface [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) qui représente l’assembly dans lequel le type cible est importé.</span><span class="sxs-lookup"><span data-stu-id="7ec58-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="7ec58-112">à `mdTypeRef` Jeton qui est défini dans la portée actuelle pour la référence de type.</span><span class="sxs-lookup"><span data-stu-id="7ec58-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ec58-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="7ec58-113">Remarks</span></span>  

 <span data-ttu-id="7ec58-114">Avant d’appeler la méthode [IMetaDataEmit ::D efineimportmember](imetadataemit-defineimportmember-method.md) , vous pouvez utiliser la `DefineImportType` méthode pour créer une référence de type, dans la portée actuelle, pour la classe parente ou l’interface parente du membre.</span><span class="sxs-lookup"><span data-stu-id="7ec58-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ec58-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7ec58-115">Requirements</span></span>  

 <span data-ttu-id="7ec58-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ec58-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec58-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7ec58-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ec58-118">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ec58-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ec58-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec58-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec58-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ec58-120">See also</span></span>

- [<span data-ttu-id="7ec58-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7ec58-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7ec58-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="7ec58-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
