---
title: IMetaDataEmit::DefineField, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432547"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField, méthode
Crée une définition pour un champ avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 dans Jeton `mdTypeDef` pour l’interface ou la classe englobante.  
  
 `szName`  
 dans Nom du champ en Unicode.  
  
 `dwFieldFlags`  
 dans Attributs du champ. Il s’agit d’un masque de ré`CorFieldAttr` valeurs.  
  
 `pvSigBlob`  
 dans Signature de champ en tant qu’objet BLOB.  
  
 `cbSigBlob`  
 dans Nombre d’octets dans `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 dans `ELEMENT_TYPE_` *\** pour la valeur de constante. Il s’agit d’une valeur `CorElementType`. Si vous ne définissez pas de valeur de constante pour le champ, utilisez `ELEMENT_TYPE_END`.  
  
 `pValue`  
 dans Valeur de constante pour le champ.  
  
 `cchValue`  
 dans Taille en caractères (Unicode) de `pValue`.  
  
 `pmd`  
 à Jeton `mdFieldDef` assigné.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
