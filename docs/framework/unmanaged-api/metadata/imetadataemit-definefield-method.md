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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177711"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField, méthode
Crée une définition pour un champ avec la signature spécifiée de métadonnées, et obtient un jeton à cette définition de champ.  
  
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
 [dans] Le `mdTypeDef` jeton pour la classe ou l’interface d’enceinte.  
  
 `szName`  
 [dans] Le nom de champ dans Unicode.  
  
 `dwFieldFlags`  
 [dans] Le champ attribue. C’est un peu `CorFieldAttr` de valeur.  
  
 `pvSigBlob`  
 [dans] La signature de champ comme un BLOB.  
  
 `cbSigBlob`  
 [dans] Le compte d’octets dans `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [dans] Le `ELEMENT_TYPE_` *\** pour la valeur constante. C’est `CorElementType` une valeur. Si ce n’est pas définir `ELEMENT_TYPE_END`une valeur constante pour le champ, utilisez .  
  
 `pValue`  
 [dans] La valeur constante pour le domaine.  
  
 `cchValue`  
 [dans] La taille dans (Unicode) caractères de `pValue`.  
  
 `pmd`  
 [out] Le `mdFieldDef` jeton assigné.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
