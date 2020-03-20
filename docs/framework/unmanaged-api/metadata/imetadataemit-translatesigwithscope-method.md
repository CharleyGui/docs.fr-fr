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
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope, méthode
Importe une assemblée dans la portée actuelle et obtient une nouvelle signature de métadonnées pour la portée fusionnée.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="parameters"></a>Paramètres  
 `pAssemImport`  
 [dans] L’interface pour l’assemblage d’importation (où la signature est définie).  
  
 `pbHashValue`  
 [dans] Le blob de hachage pour l’assemblage.  
  
 `cbHashValue`  
 [dans] Le compte d’octets dans `pbHashValue`.  
  
 `import`  
 [dans] L’interface pour la portée des métadonnées d’importation.  
  
 `pbSigBlob`  
 [dans] La signature à importer.  
  
 `cbSigBlob`  
 [dans] La taille, dans les `pbSigBlob`octets, de .  
  
 `pAssemEmit`  
 [dans] L’interface pour l’assemblage d’exportation.  
  
 `emit`  
 [dans] L’interface pour la portée des métadonnées d’exportation.  
  
 `pvTranslatedSig`  
 [out] Le tampon pour tenir le blob signature traduite.  
  
 `cbTranslatedSigMax`  
 [dans] La capacité, dans les `pvTranslatedSig`octets, de .  
  
 `pcbTranslatedSig`  
 [out] Le nombre d’octets réels dans la signature traduite.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
