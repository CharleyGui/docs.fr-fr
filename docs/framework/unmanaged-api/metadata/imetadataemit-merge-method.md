---
title: IMetaDataEmit::Merge, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 06894f238f9fda3111d5484bb1b2add183a5abb2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448057"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge, méthode
Ajoute l’étendue importée spécifiée à la liste des étendues à fusionner.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pImport`  
 dans Pointeur vers un objet [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui identifie l’étendue importée à fusionner.  
  
 `pIMap`  
 dans Pointeur vers un objet [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) qui spécifie le nouveau mappage du jeton.  
  
 `pHandler`  
 dans Pointeur vers un objet [IUnknown](/cpp/atl/iunknown) qui spécifie les erreurs.  
  
## <a name="remarks"></a>Notes  
 Appelez [IMetaDataEmit :: MergeEnd,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) pour déclencher la fusion des métadonnées dans une seule portée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
