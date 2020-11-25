---
title: IMetaDataDispenserEx, interface
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 60d321c1a87a5da433437c9d4587fa9f8947acf4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713377"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx, interface

Étend l’interface d' [interface IMetaDataDispenser](imetadatadispenser-interface.md) pour permettre de contrôler la manière dont les API de métadonnées fonctionnent sur la portée de métadonnées actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[FindAssembly, méthode](imetadatadispenserex-findassembly-method.md)|Cette méthode n’est pas implémentée. Si elle est appelée, elle retourne E_NOTIMPL.|  
|[FindAssemblyModule, méthode](imetadatadispenserex-findassemblymodule-method.md)|Cette méthode n’est pas implémentée. Si elle est appelée, elle retourne E_NOTIMPL.|  
|[GetCORSystemDirectory, méthode](imetadatadispenserex-getcorsystemdirectory-method.md)|Obtient le répertoire qui contient le common language runtime actuel (CLR). Cette méthode est prise en charge uniquement par les débogueurs hors processus. Si elle est appelée à partir d’un autre composant, elle retourne E_NOTIMPL.|  
|[GetOption, méthode](imetadatadispenserex-getoption-method.md)|Obtient la valeur de l’option spécifiée pour la portée des métadonnées actuelle. L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.|  
|[OpenScopeOnITypeInfo, méthode](imetadatadispenserex-openscopeonitypeinfo-method.md)|Cette méthode n’est pas implémentée. Si elle est appelée, elle retourne E_NOTIMPL.|  
|[SetOption, méthode](imetadatadispenserex-setoption-method.md)|Définit l’option spécifiée sur une valeur donnée pour la portée de métadonnées actuelle. L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataDispenser, interface](imetadatadispenser-interface.md)
- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
