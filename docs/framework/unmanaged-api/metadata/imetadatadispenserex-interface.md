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
ms.openlocfilehash: 985cdea670714394119fb846e9e55a01713559a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431143"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx, interface
Étend l’interface d' [interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) pour permettre de contrôler la manière dont les API de métadonnées fonctionnent sur la portée de métadonnées actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[FindAssembly, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Cette méthode n’est pas implémentée. Si elle est appelée, elle retourne E_NOTIMPL.|  
|[FindAssemblyModule, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Cette méthode n’est pas implémentée. Si elle est appelée, elle retourne E_NOTIMPL.|  
|[GetCORSystemDirectory, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Obtient le répertoire qui contient le common language runtime actuel (CLR). Cette méthode est prise en charge uniquement par les débogueurs hors processus. Si elle est appelée à partir d’un autre composant, elle retourne E_NOTIMPL.|  
|[GetOption, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Obtient la valeur de l’option spécifiée pour la portée des métadonnées actuelle. L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.|  
|[OpenScopeOnITypeInfo, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Cette méthode n’est pas implémentée. Si elle est appelée, elle retourne E_NOTIMPL.|  
|[SetOption, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Définit l’option spécifiée sur une valeur donnée pour la portée de métadonnées actuelle. L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
