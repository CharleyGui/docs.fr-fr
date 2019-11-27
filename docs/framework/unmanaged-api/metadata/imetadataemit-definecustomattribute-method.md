---
title: IMetaDataEmit::DefineCustomAttribute, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: e6a732b98ae02ba2b273b45921b7de61ab4fd29f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432639"
---
# <a name="imetadataemitdefinecustomattribute-method"></a>IMetaDataEmit::DefineCustomAttribute, méthode
Crée une définition pour un attribut personnalisé avec la signature de métadonnées spécifiée, à attacher à l’objet spécifié et obtient un jeton pour cette définition d’attribut personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tkObj`  
 dans Jeton pour l’élément propriétaire.  
  
 `tkType`  
 dans Jeton qui identifie l’attribut personnalisé.  
  
 `pCustomAttribute`  
 dans Pointeur vers l’attribut personnalisé.  
  
 `cbCustomAttribute`  
 dans Nombre d’octets dans `pCustomAttribute`.  
  
 `pcv`  
 à Jeton `mdCustomAttribute` assigné.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
