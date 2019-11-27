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
ms.openlocfilehash: cea84f47a5289df4bc9c50381e18d7077b3b8dad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440474"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope, méthode
Importe un assembly dans la portée actuelle et obtient une nouvelle signature de métadonnées pour la portée fusionnée.  
  
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
 dans Interface pour l’assembly d’importation (où la signature est définie).  
  
 `pbHashValue`  
 dans Objet blob de hachage pour l’assembly.  
  
 `cbHashValue`  
 dans Nombre d’octets dans `pbHashValue`.  
  
 `import`  
 dans Interface pour l’importation de la portée des métadonnées.  
  
 `pbSigBlob`  
 dans Signature à importer.  
  
 `cbSigBlob`  
 dans Taille, en octets, de `pbSigBlob`.  
  
 `pAssemEmit`  
 dans Interface pour l’assembly d’exportation.  
  
 `emit`  
 dans Interface pour l’exportation de la portée des métadonnées.  
  
 `pvTranslatedSig`  
 à Mémoire tampon devant contenir l’objet blob de signature traduit.  
  
 `cbTranslatedSigMax`  
 dans Capacité, en octets, de `pvTranslatedSig`.  
  
 `pcbTranslatedSig`  
 à Nombre d’octets réels dans la signature traduite.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
