---
title: IMetaDataTables::GetNextGuid, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: 645a9913d0de6f93e59df3dd8ba7267ddb13b41b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490235"
---
# <a name="imetadatatablesgetnextguid-method"></a>IMetaDataTables::GetNextGuid, méthode
Obtient l’index de la valeur GUID suivante dans la colonne de table actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ixGuid`  
 dans Valeur d’index d’une colonne de table GUID.  
  
 `pNext`  
 à Pointeur vers l’index de la valeur GUID suivante.  
  
## <a name="remarks"></a>Remarques  

  Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents. Pour plus d’informations sur la table GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : définition et sémantique des métadonnées ». La documentation est disponible en ligne. consultez [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](imetadatatables-interface.md)
- [IMetaDataTables2, interface](imetadatatables2-interface.md)
