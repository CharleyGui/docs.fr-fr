---
title: IMetaDataTables::GetGuid, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 2ac29de437e746f1524fc1427c47eb8f5c761be7
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937808"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid, méthode
Obtient un GUID à partir de la ligne à l’index spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `ixGuid`  
 dans Index de la ligne à partir de laquelle le GUID doit être obtenu.  
  
 `ppGuid`  
 à Pointeur vers un pointeur vers le GUID.  
  
## <a name="remarks"></a>Notes  

  Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents. Pour plus d’informations sur la table GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : définition et sémantique des métadonnées ». La documentation est disponible en ligne. consultez [les C# normes ECMA et Common Language Infrastructure](../../../standard/components.md#applicable-standards) [standard et ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
