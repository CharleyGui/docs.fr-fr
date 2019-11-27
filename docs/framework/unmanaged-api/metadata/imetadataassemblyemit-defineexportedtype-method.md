---
title: IMetaDataAssemblyEmit::DefineExportedType, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 44f97ef498eb8e64c55fc86b9f290b9e088293f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432068"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="f7ebd-102">IMetaDataAssemblyEmit::DefineExportedType, méthode</span><span class="sxs-lookup"><span data-stu-id="f7ebd-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="f7ebd-103">Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7ebd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7ebd-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7ebd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7ebd-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f7ebd-106">dans Nom du type à exporter.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="f7ebd-107">Pour la version 1,1 de la common language runtime, le nom du type exporté doit correspondre exactement au nom donné dans le `TypeDef` pour le type.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="f7ebd-108">dans Jeton spécifiant où le type exporté est implémenté.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="f7ebd-109">Les valeurs valides et les significations qui leur sont associées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f7ebd-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="f7ebd-110">`mdFile` le type est implémenté dans un fichier différent au sein de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="f7ebd-111">`mdAssemblyRef` le type est implémenté dans un assembly différent.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="f7ebd-112">`mdExportedTYpe` le type est imbriqué dans un autre type.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="f7ebd-113">`mdFileNil` le type se trouve dans le même fichier que le manifeste et n’est pas un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="f7ebd-114">dans Jeton pour les métadonnées qui spécifie le type à exporter.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="f7ebd-115">Cette valeur est entrée dans la table `TypeDef` du fichier qui implémente le type et s’applique uniquement si ce fichier se trouve dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="f7ebd-116">dans Combinaison d’opérations de bits de valeurs d’énumération [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) qui définissent les paramètres de propriété pour le type exporté.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="f7ebd-117">à Pointeur vers le jeton de métadonnées retourné qui indique le type exporté.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7ebd-118">Notes</span><span class="sxs-lookup"><span data-stu-id="f7ebd-118">Remarks</span></span>  
 <span data-ttu-id="f7ebd-119">Une structure de métadonnées `ExportedType` doit être définie pour chaque type exposé par cet assembly et implémenté dans un module autre que celui contenant le manifeste.</span><span class="sxs-lookup"><span data-stu-id="f7ebd-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7ebd-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7ebd-120">Requirements</span></span>  
 <span data-ttu-id="f7ebd-121">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7ebd-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7ebd-122">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f7ebd-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7ebd-123">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f7ebd-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7ebd-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7ebd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ebd-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7ebd-125">See also</span></span>

- [<span data-ttu-id="f7ebd-126">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f7ebd-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
