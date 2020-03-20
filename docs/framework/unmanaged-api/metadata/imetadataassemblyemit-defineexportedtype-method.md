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
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177883"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="ad4cc-102">IMetaDataAssemblyEmit::DefineExportedType, méthode</span><span class="sxs-lookup"><span data-stu-id="ad4cc-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="ad4cc-103">Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad4cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad4cc-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad4cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad4cc-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ad4cc-106">[dans] Le nom du type à exporter.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="ad4cc-107">Pour la version 1.1 de l’heure courante, le nom du type `TypeDef` exporté doit exactement correspondre au nom donné dans le type.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="ad4cc-108">[dans] Un jeton précisant où le type exporté est implémenté.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="ad4cc-109">Les valeurs valides et leurs significations associées sont les suivante :</span><span class="sxs-lookup"><span data-stu-id="ad4cc-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="ad4cc-110">`mdFile`Le type est implémenté dans un fichier différent au sein de cette assemblée.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="ad4cc-111">`mdAssemblyRef`Le type est mis en œuvre dans un assemblage différent.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="ad4cc-112">`mdExportedTYpe`Le type est imbriqué dans un autre type.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="ad4cc-113">`mdFileNil`Le type est dans le même fichier que le manifeste et n’est pas un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="ad4cc-114">[dans] Un jeton aux métadonnées qui spécifie le type à exporter.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="ad4cc-115">Cette valeur est `TypeDef` saisie dans le tableau du fichier qui implémente le type et n’est pertinente que si ce fichier est dans cette assemblée.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="ad4cc-116">[dans] Une combinaison bitwise de valeurs d’énumération [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) qui définissent les paramètres de propriété pour le type exporté.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="ad4cc-117">[out] Un pointeur sur les métadonnées retournées qui indique le type exporté.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad4cc-118">Notes </span><span class="sxs-lookup"><span data-stu-id="ad4cc-118">Remarks</span></span>  
 <span data-ttu-id="ad4cc-119">Une `ExportedType` structure de métadonnées doit être définie pour chaque type exposé par cet assemblage et qui est implémentée dans un module autre que celui contenant le manifeste.</span><span class="sxs-lookup"><span data-stu-id="ad4cc-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad4cc-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ad4cc-120">Requirements</span></span>  
 <span data-ttu-id="ad4cc-121">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad4cc-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad4cc-122">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ad4cc-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad4cc-123">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad4cc-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad4cc-124">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad4cc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad4cc-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad4cc-125">See also</span></span>

- [<span data-ttu-id="ad4cc-126">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ad4cc-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
