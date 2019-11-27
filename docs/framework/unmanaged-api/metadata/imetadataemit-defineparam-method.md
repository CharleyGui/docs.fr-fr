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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431686"
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
 dans Indicateurs pour le paramètre. Il s’agit d’un masque de ré`CorParamAttr` valeurs.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** pour la valeur constante.  
  
 `pValue`  
 dans Valeur de constante pour le paramètre.  
  
 `cchValue`  
 dans Taille, en caractères Unicode, de `pValue`.  
  
 `ppd`  
 à Jeton `mdParamDef` assigné.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de séquence dans `ulParamSeq` commencent par 1 pour les paramètres. Une valeur de retour a un numéro de séquence égal à 0.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
