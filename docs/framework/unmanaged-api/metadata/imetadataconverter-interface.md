---
title: IMetaDataConverter, interface
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: 74804cdc9dc04c3ede5cc26a6310dbb3948cd78a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729484"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter, interface

Fournit des méthodes pour mapper des bibliothèques de types à leurs signatures de métadonnées et effectuer la conversion entre les deux.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo, méthode](imetadataconverter-getmetadatafromtypeinfo-method.md)|Obtient un pointeur vers une instance [IMetaDataImport](imetadataimport-interface.md) qui représente la signature de métadonnées pour la bibliothèque de types référencée par l' `ITypeInfo` instance spécifiée.|  
|[GetMetaDataFromTypeLib, méthode](imetadataconverter-getmetadatafromtypelib-method.md)|Obtient un pointeur vers une `IMetaDataImport` instance qui représente la signature de métadonnées pour la bibliothèque de types représentée par l' `ITypeLib` instance spécifiée.|  
|[GetTypeLibFromMetaData, méthode](imetadataconverter-gettypelibfrommetadata-method.md)|Obtient un pointeur vers une `ITypeLib` instance de qui représente la bibliothèque de types qui contient les noms de module et de bibliothèque spécifiés.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
