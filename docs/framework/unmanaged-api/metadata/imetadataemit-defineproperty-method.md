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
ms.openlocfilehash: d2a4a15126f34666a58021a59e9e193685b15a49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719487"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty, méthode

Crée une définition de propriété pour le type spécifié, avec les `get` accesseurs de méthode et spécifiés `set` , et obtient un jeton pour cette définition de propriété.  
  
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
 dans Jeton de la classe ou de l’interface sur laquelle la propriété est définie.  
  
 `szProperty`  
 [in] Nom de la propriété.  
  
 `dwPropFlags`  
 dans Indicateurs de propriété.  
  
 `pvSig`  
 dans Signature de la propriété.  
  
 `cbSig`  
 dans Nombre d’octets dans `pvSig` .  
  
 `dwCPlusTypeFlag`  
 dans Type de la valeur par défaut de la propriété.  
  
 `pValue`  
 dans Valeur par défaut de la propriété.  
  
 `cchValue`  
 dans Nombre de caractères (Unicode) dans `pValue` .  
  
 `mdSetter`  
 dans Méthode qui définit la valeur de la propriété.  
  
 `mdGetter`  
 dans Méthode qui obtient la valeur de la propriété.  
  
 `rmdOtherMethods[]`  
 dans Tableau d’autres méthodes associées à la propriété. Terminez le tableau par un `mdTokenNil` .  
  
 `pmdProp`  
 à `mdProperty` Jeton assigné.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
