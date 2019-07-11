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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d64a1ef21cd4fa4224609c7cd415c1611313769
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777548"
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
 [in] Le jeton pour la méthode dont le paramètre est défini.  
  
 `ulParamSeq`  
 [in] Numéro de séquence du paramètre.  
  
 `szName`  
 [in] Le nom du paramètre au format Unicode.  
  
 `dwParamFlags`  
 [in] Indicateurs pour le paramètre. Il s’agit d’un masque de bits de `CorParamAttr` valeurs.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** pour la valeur de constante.  
  
 `pValue`  
 [in] La valeur de constante pour le paramètre.  
  
 `cchValue`  
 [in] La taille, en caractères Unicode, de `pValue`.  
  
 `ppd`  
 [out] Le `mdParamDef` jeton attribué.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de séquence dans `ulParamSeq` commencent par 1 pour les paramètres. Une valeur de retour a un numéro de séquence 0.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
