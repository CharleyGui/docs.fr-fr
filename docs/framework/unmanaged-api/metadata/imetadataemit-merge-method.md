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
ms.openlocfilehash: e64d644b511f7c3249c48b9642bfd3163142af3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722009"
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
 dans Pointeur vers un objet [IMetaDataImport](imetadataimport-interface.md) qui identifie l’étendue importée à fusionner.  
  
 `pIMap`  
 dans Pointeur vers un objet [IMapToken](imaptoken-interface.md) qui spécifie le nouveau mappage du jeton.  
  
 `pHandler`  
 dans Pointeur vers un objet [IUnknown](/cpp/atl/iunknown) qui spécifie les erreurs.  
  
## <a name="remarks"></a>Remarques  

 Appelez [IMetaDataEmit :: MergeEnd,](imetadataemit-mergeend-method.md) pour déclencher la fusion des métadonnées dans une seule portée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
