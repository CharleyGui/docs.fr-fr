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
ms.openlocfilehash: 7ef6dbc46806febc6fba89b39a8b894377225c23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003956"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="9b01f-102">IMetaDataEmit::TranslateSigWithScope, méthode</span><span class="sxs-lookup"><span data-stu-id="9b01f-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="9b01f-103">Importe un assembly dans la portée actuelle et obtient une nouvelle signature de métadonnées pour la portée fusionnée.</span><span class="sxs-lookup"><span data-stu-id="9b01f-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b01f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b01f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9b01f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b01f-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="9b01f-106">dans Interface pour l’assembly d’importation (où la signature est définie).</span><span class="sxs-lookup"><span data-stu-id="9b01f-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="9b01f-107">dans Objet blob de hachage pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9b01f-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="9b01f-108">dans Nombre d’octets dans `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="9b01f-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="9b01f-109">dans Interface pour l’importation de la portée des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9b01f-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="9b01f-110">dans Signature à importer.</span><span class="sxs-lookup"><span data-stu-id="9b01f-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9b01f-111">dans Taille, en octets, de `pbSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="9b01f-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="9b01f-112">dans Interface pour l’assembly d’exportation.</span><span class="sxs-lookup"><span data-stu-id="9b01f-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="9b01f-113">dans Interface pour l’exportation de la portée des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9b01f-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="9b01f-114">à Mémoire tampon devant contenir l’objet blob de signature traduit.</span><span class="sxs-lookup"><span data-stu-id="9b01f-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="9b01f-115">dans Capacité, en octets, de `pvTranslatedSig` .</span><span class="sxs-lookup"><span data-stu-id="9b01f-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="9b01f-116">à Nombre d’octets réels dans la signature traduite.</span><span class="sxs-lookup"><span data-stu-id="9b01f-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b01f-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9b01f-117">Requirements</span></span>  
 <span data-ttu-id="9b01f-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b01f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b01f-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9b01f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b01f-120">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b01f-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b01f-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b01f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b01f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b01f-122">See also</span></span>

- [<span data-ttu-id="9b01f-123">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9b01f-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="9b01f-124">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="9b01f-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="9b01f-125">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9b01f-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9b01f-126">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="9b01f-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="9b01f-127">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="9b01f-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
