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
ms.openlocfilehash: 2bc2b983171dc41d5ac37eda0359f1aaee4ebd6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725753"
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
 dans `mdTypeDef` Jeton de l’interface ou de la classe englobante.  
  
 `szName`  
 dans Nom du champ en Unicode.  
  
 `dwFieldFlags`  
 dans Attributs du champ. Il s’agit d’un masque de `CorFieldAttr` valeur de valeurs.  
  
 `pvSigBlob`  
 dans Signature de champ en tant qu’objet BLOB.  
  
 `cbSigBlob`  
 dans Nombre d’octets dans `pvSigBlob` .  
  
 `dwCPlusTypeFlag`  
 dans `ELEMENT_TYPE_` *\** Pour la valeur de constante. Il s’agit d’une `CorElementType` valeur. Si vous ne définissez pas de valeur de constante pour le champ, utilisez `ELEMENT_TYPE_END` .  
  
 `pValue`  
 dans Valeur de constante pour le champ.  
  
 `cchValue`  
 dans Taille en (Unicode) caractères de `pValue` .  
  
 `pmd`  
 à `mdFieldDef` Jeton assigné.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
