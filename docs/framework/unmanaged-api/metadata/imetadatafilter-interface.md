---
title: IMetaDataFilter, interface
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: 821936d20a421739e8eb3d5df228888df7f022e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503781"
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter, interface
Fournit des méthodes pour marquer et filtrer des jetons de métadonnées pour éviter de répéter des actions qui ont déjà été prises.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IsTokenMarked, méthode](imetadatafilter-istokenmarked-method.md)|Obtient une valeur indiquant si le jeton de métadonnées spécifié a été traité.|  
|[MarkToken, méthode](imetadatafilter-marktoken-method.md)|Définit une valeur indiquant que le jeton de métadonnées spécifié a été traité.|  
|[UnmarkAll, méthode](imetadatafilter-unmarkall-method.md)|Supprime les marques de traitement de tous les jetons dans la portée de métadonnées actuelle.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
