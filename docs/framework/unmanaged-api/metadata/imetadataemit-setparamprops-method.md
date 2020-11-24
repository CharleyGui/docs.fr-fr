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
ms.openlocfilehash: b0cc28807938bcfb9b2465093ff4cfb94066ee98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675059"
---
# <a name="imetadataemitsetparamprops-method"></a>IMetaDataEmit::SetParamProps, méthode

Définit ou modifie les fonctionnalités d’un paramètre de méthode qui a été défini par un appel antérieur à [IMetaDataEmit ::D efineparam](imetadataemit-defineparam-method.md).  
  
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
 dans Jeton pour le paramètre cible.  
  
 `szName`  
 dans Nom du paramètre en Unicode.  
  
 `dwParamFlags`  
 dans Indicateurs du paramètre.  
  
 `dwCPlusTypeFlag`  
 dans ELEMENT_TYPE_ * pour la valeur constante.  
  
 `pValue`  
 dans Valeur de constante pour le paramètre.  
  
 `cchValue`  
 dans Taille en (Unicode) caractères de `pValue` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
