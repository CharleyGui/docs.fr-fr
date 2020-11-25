---
title: IMetaDataEmit2, interface
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: b8ad159dace734c343297b256092162f17ab829b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726481"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2, interface

Étend l’interface [IMetaDataEmit](imetadataemit-interface.md) principalement pour offrir la possibilité d’utiliser des types génériques.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineGenericParam, méthode](imetadataemit2-definegenericparam-method.md)|Crée une définition pour un paramètre de type générique et obtient un jeton pour ce paramètre de type générique.|  
|[DefineMethodSpec, méthode](imetadataemit2-definemethodspec-method.md)|Crée une instance générique d’une méthode et obtient un jeton pour la définition.|  
|[GetDeltaSaveSize, méthode](imetadataemit2-getdeltasavesize-method.md)|Obtient une valeur qui indique la différence de taille des données requises pour exprimer les modifications de la session de modification et de continuation en cours.|  
|[ResetENCLog, méthode](imetadataemit2-resetenclog-method.md)|Réinitialise le journal Edit-and-continue et démarre une nouvelle session.|  
|[SaveDelta, méthode](imetadataemit2-savedelta-method.md)|Enregistre les modifications de la session de modification et de poursuite en cours dans le fichier spécifié.|  
|[SaveDeltaToMemory, méthode](imetadataemit2-savedeltatomemory-method.md)|Enregistre les modifications de la session en cours de modification et de continuation dans la mémoire.|  
|[SaveDeltaToStream, méthode](imetadataemit2-savedeltatostream-method.md)|Enregistre les modifications de la session de modification et de continuation actuelle dans le flux spécifié.|  
|[SetGenericParamProps, méthode](imetadataemit2-setgenericparamprops-method.md)|Définit des valeurs de propriété pour la définition de paramètre générique référencée par le jeton spécifié.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataEmit, interface](imetadataemit-interface.md)
