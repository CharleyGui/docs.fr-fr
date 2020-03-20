---
title: IMetaDataEmit::SetParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 13220dcfdd260688494d5aebc50f94abf8a82215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177503"
---
# <a name="imetadataemitsetparamprops-method"></a>IMetaDataEmit::SetParamProps, méthode
Définit ou modifie les caractéristiques d’un paramètre de méthode qui a été défini par un appel antérieur à [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pd`  
 [dans] Le jeton pour le paramètre cible.  
  
 `szName`  
 [dans] Le nom du paramètre dans Unicode.  
  
 `dwParamFlags`  
 [dans] Les drapeaux pour le paramètre.  
  
 `dwCPlusTypeFlag`  
 [dans] Le ELEMENT_TYPE_ pour la valeur constante.  
  
 `pValue`  
 [dans] La valeur constante du paramètre.  
  
 `cchValue`  
 [dans] La taille dans (Unicode) caractères de `pValue`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
