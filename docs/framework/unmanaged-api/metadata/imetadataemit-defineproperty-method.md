---
title: IMetaDataEmit::DefineProperty, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175783"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty, méthode
Crée une définition de propriété pour `get` le `set` type spécifié, avec les accesseurs spécifiés et la méthode, et obtient un jeton à cette définition de propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [dans] Le jeton pour la classe ou l’interface sur laquelle la propriété est définie.  
  
 `szProperty`  
 [in] Nom de la propriété.  
  
 `dwPropFlags`  
 [dans] Les drapeaux de la propriété.  
  
 `pvSig`  
 [dans] La signature de la propriété.  
  
 `cbSig`  
 [dans] Le compte d’octets dans `pvSig`.  
  
 `dwCPlusTypeFlag`  
 [dans] Le type de valeur par défaut de la propriété.  
  
 `pValue`  
 [dans] La valeur par défaut pour la propriété.  
  
 `cchValue`  
 [dans] Le nombre de caractères `pValue`(Unicode) dans .  
  
 `mdSetter`  
 [dans] La méthode qui définit la valeur de la propriété.  
  
 `mdGetter`  
 [dans] La méthode qui obtient la valeur de la propriété.  
  
 `rmdOtherMethods[]`  
 [dans] Un éventail d’autres méthodes associées à la propriété. Terminez le `mdTokenNil`tableau avec un .  
  
 `pmdProp`  
 [out] Le `mdProperty` jeton assigné.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
