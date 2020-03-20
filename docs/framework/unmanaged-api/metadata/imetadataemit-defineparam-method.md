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
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177694"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam, méthode
Crée une définition de paramètre avec la signature spécifiée pour la méthode référencée par le jeton spécifié, et obtient un jeton pour cette définition de paramètre.  
  
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
 [dans] Le jeton de la méthode dont le paramètre est défini.  
  
 `ulParamSeq`  
 [dans] Le numéro de séquence de paramètres.  
  
 `szName`  
 [dans] Le nom du paramètre dans Unicode.  
  
 `dwParamFlags`  
 [dans] Drapeaux pour le paramètre. C’est un peu `CorParamAttr` de valeur.  
  
 `dwCPlusTypeFlag`  
 [dans] `ELEMENT_TYPE_` pour la valeur *\** constante.  
  
 `pValue`  
 [dans] La valeur constante du paramètre.  
  
 `cchValue`  
 [dans] La taille, dans les `pValue`caractères Unicode, de .  
  
 `ppd`  
 [out] Le `mdParamDef` jeton assigné.  
  
## <a name="remarks"></a>Notes   
 Les valeurs `ulParamSeq` de séquence commencent par 1 pour les paramètres. Une valeur de retour a un nombre de séquences de 0.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
