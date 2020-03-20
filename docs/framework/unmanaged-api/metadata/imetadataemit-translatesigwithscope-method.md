---
title: IMetaDataEmit::TranslateSigWithScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: 2662af41fbd2cdc3ce8a6df1e036dfc5b22ff6a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175549"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="f6a26-102">IMetaDataEmit::TranslateSigWithScope, méthode</span><span class="sxs-lookup"><span data-stu-id="f6a26-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="f6a26-103">Importe une assemblée dans la portée actuelle et obtient une nouvelle signature de métadonnées pour la portée fusionnée.</span><span class="sxs-lookup"><span data-stu-id="f6a26-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6a26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6a26-104">Syntax</span></span>  
  
```cpp  
HRESULT TranslateSigWithScope (
    [in]  IMetaDataAssemblyImport   *pAssemImport,
    [in]  const void                *pbHashValue,
    [in]  ULONG                     cbHashValue,
    [in]  IMetaDataImport           *import,
    [in]  PCCOR_SIGNATURE           pbSigBlob,
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,
    [in]  IMetaDataEmit             *emit,
    [out] PCOR_SIGNATURE            pvTranslatedSig,
    [in]  ULONG                     cbTranslatedSigMax,
    [out] ULONG                     *pcbTranslatedSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6a26-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6a26-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="f6a26-106">[dans] L’interface pour l’assemblage d’importation (où la signature est définie).</span><span class="sxs-lookup"><span data-stu-id="f6a26-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f6a26-107">[dans] Le blob de hachage pour l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="f6a26-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f6a26-108">[dans] Le compte d’octets dans `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f6a26-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="f6a26-109">[dans] L’interface pour la portée des métadonnées d’importation.</span><span class="sxs-lookup"><span data-stu-id="f6a26-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="f6a26-110">[dans] La signature à importer.</span><span class="sxs-lookup"><span data-stu-id="f6a26-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f6a26-111">[dans] La taille, dans les `pbSigBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="f6a26-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="f6a26-112">[dans] L’interface pour l’assemblage d’exportation.</span><span class="sxs-lookup"><span data-stu-id="f6a26-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="f6a26-113">[dans] L’interface pour la portée des métadonnées d’exportation.</span><span class="sxs-lookup"><span data-stu-id="f6a26-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="f6a26-114">[out] Le tampon pour tenir le blob signature traduite.</span><span class="sxs-lookup"><span data-stu-id="f6a26-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="f6a26-115">[dans] La capacité, dans les `pvTranslatedSig`octets, de .</span><span class="sxs-lookup"><span data-stu-id="f6a26-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="f6a26-116">[out] Le nombre d’octets réels dans la signature traduite.</span><span class="sxs-lookup"><span data-stu-id="f6a26-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6a26-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f6a26-117">Requirements</span></span>  
 <span data-ttu-id="f6a26-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6a26-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6a26-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="f6a26-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6a26-120">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6a26-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6a26-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6a26-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a26-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6a26-122">See also</span></span>

- [<span data-ttu-id="f6a26-123">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f6a26-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="f6a26-124">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="f6a26-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="f6a26-125">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f6a26-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f6a26-126">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f6a26-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="f6a26-127">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f6a26-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
