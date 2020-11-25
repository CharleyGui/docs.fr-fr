---
title: IMetaDataDispenser, interface
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: c798aeba46adf91a8c13f8143c00f02173a0bb52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726104"
---
# <a name="imetadatadispenser-interface"></a>IMetaDataDispenser, interface

Fournit des méthodes pour créer une portée de métadonnées ou en ouvrir une existante.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineScope, méthode](imetadatadispenser-definescope-method.md)|Crée une zone en mémoire dans laquelle vous pouvez créer des métadonnées.|  
|[OpenScope, méthode](imetadatadispenser-openscope-method.md)|Ouvre un fichier sur disque existant et mappe ses métadonnées en mémoire.|  
|[OpenScopeOnMemory, méthode](imetadatadispenser-openscopeonmemory-method.md)|Ouvre une zone de mémoire qui contient des métadonnées existantes. Autrement dit, cette méthode ouvre une zone de mémoire spécifiée dans laquelle les données existantes sont traitées en tant que métadonnées.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenserEx, interface](imetadatadispenserex-interface.md)
- [Interfaces de métadonnées](metadata-interfaces.md)
