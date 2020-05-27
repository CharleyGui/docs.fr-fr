---
title: IMetaDataEmit::SetPropertyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007778"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps, méthode
Définit les fonctionnalités stockées dans les métadonnées d’une propriété définie par un appel antérieur à la [méthode DefineProperty](imetadataemit-defineproperty-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pr`  
 dans Jeton de la propriété à modifier.  
  
 `dwPropFlags`  
 dans Indicateurs de propriété.  
  
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
 dans Tableau d’autres méthodes associées à la propriété. Mettez fin à ce tableau avec un `mdTokenNil` jeton.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
