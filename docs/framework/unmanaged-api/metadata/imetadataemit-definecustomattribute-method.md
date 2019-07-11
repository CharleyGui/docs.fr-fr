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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 994e007eabf8b7fdcf5446d905c06eb4ab91bb3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777682"
---
# <a name="imetadataemitdefinecustomattribute-method"></a>IMetaDataEmit::DefineCustomAttribute, méthode
Crée une définition pour un attribut personnalisé avec la signature de métadonnées spécifié, à joindre à l’objet spécifié et obtient un jeton pour cette définition d’attribut personnalisé.  
  
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
 [in] Le jeton pour l’élément propriétaire.  
  
 `tkType`  
 [in] Le jeton qui identifie l’attribut personnalisé.  
  
 `pCustomAttribute`  
 [in] Pointeur vers l’attribut personnalisé.  
  
 `cbCustomAttribute`  
 [in] Le nombre d’octets dans `pCustomAttribute`.  
  
 `pcv`  
 [out] Le `mdCustomAttribute` jeton attribué.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
