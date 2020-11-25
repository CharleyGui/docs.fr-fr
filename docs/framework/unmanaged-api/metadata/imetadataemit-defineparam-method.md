---
title: IMetaDataEmit::DefineParam, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 5b3f89bb14be0d7128682f8702548545b1e50928
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719526"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam, méthode

Crée une définition de paramètre avec la signature spécifiée pour la méthode référencée par le jeton spécifié et obtient un jeton pour cette définition de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `md`  
 dans Jeton pour la méthode dont le paramètre est défini.  
  
 `ulParamSeq`  
 dans Numéro de séquence du paramètre.  
  
 `szName`  
 dans Nom du paramètre en Unicode.  
  
 `dwParamFlags`  
 dans Indicateurs pour le paramètre. Il s’agit d’un masque de `CorParamAttr` valeur de valeurs.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** pour la valeur de constante.  
  
 `pValue`  
 dans Valeur de constante pour le paramètre.  
  
 `cchValue`  
 dans Taille, en caractères Unicode, de `pValue` .  
  
 `ppd`  
 à `mdParamDef` Jeton assigné.  
  
## <a name="remarks"></a>Remarques  

 Les valeurs de séquence dans `ulParamSeq` commencent par 1 pour les paramètres. Une valeur de retour a un numéro de séquence égal à 0.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
