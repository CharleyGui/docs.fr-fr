---
title: IMetaDataTables, interface
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: 073e73f082416308b893974471e39cbf5243d01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708853"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables, interface

Fournit des méthodes pour le stockage et la récupération d'informations de métadonnées dans des tables.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBlob, méthode](imetadatatables-getblob-method.md)|Obtient un pointeur vers l’objet BLOB (Binary Large Object) situé à l’index de colonne spécifié.|  
|[GetBlobHeapSize, méthode](imetadatatables-getblobheapsize-method.md)|Obtient la taille, en octets, du tas d’objets BLOB.|  
|[GetCodedTokenInfo, méthode](imetadatatables-getcodedtokeninfo-method.md)|Obtient un pointeur vers un tableau de jetons associé à l’index de ligne spécifié.|  
|[GetColumn, méthode](imetadatatables-getcolumn-method.md)|Obtient un pointeur vers les valeurs contenues dans la colonne à l’index de colonne spécifié, dans la table au niveau de l’index de table spécifié.|  
|[GetColumnInfo, méthode](imetadatatables-getcolumninfo-method.md)|Obtient les données relatives à la colonne spécifiée dans la table spécifiée.|  
|[GetGuid, méthode](imetadatatables-getguid-method.md)|Obtient un GUID à partir de la ligne à l’index spécifié.|  
|[GetGuidHeapSize, méthode](imetadatatables-getguidheapsize-method.md)|Obtient la taille, en octets, du tas GUID.|  
|[GetNextBlob, méthode](imetadatatables-getnextblob-method.md)|Obtient l’index de l’objet BLOB suivant dans la table.|  
|[GetNextGuid, méthode](imetadatatables-getnextguid-method.md)|Obtient l’index de la valeur GUID suivante dans la colonne de table actuelle.|  
|[GetNextString, méthode](imetadatatables-getnextstring-method.md)|Obtient l’index de la chaîne suivante dans la colonne de table actuelle.|  
|[GetNextUserString, méthode](imetadatatables-getnextuserstring-method.md)|Obtient l’index de la ligne qui contient la chaîne codée en dur suivante dans la colonne de table actuelle.|  
|[GetNumTables, méthode](imetadatatables-getnumtables-method.md)|Obtient le nombre de tables dans la portée de l' `IMetaDataTables` instance actuelle.|  
|[GetRow, méthode](imetadatatables-getrow-method.md)|Obtient la ligne à l’index de ligne spécifié dans la table au niveau de l’index de table spécifié.|  
|[GetString, méthode](imetadatatables-getstring-method.md)|Obtient la chaîne à l’index spécifié à partir de la colonne de table dans la portée de référence actuelle.|  
|[GetStringHeapSize, méthode](imetadatatables-getstringheapsize-method.md)|Obtient la taille, en octets, du tas de la chaîne.|  
|[GetTableIndex, méthode](imetadatatables-gettableindex-method.md)|Obtient l’index de la table référencée par le jeton spécifié.|  
|[GetTableInfo, méthode](imetadatatables-gettableinfo-method.md)|Obtient le nom, la taille de ligne, le nombre de lignes, le nombre de colonnes et l’index de colonne clé de la table au niveau de l’index de table spécifié.|  
|[GetUserString, méthode](imetadatatables-getuserstring-method.md)|Obtient la chaîne codée en dur à l’index spécifié dans la colonne de chaîne de l’étendue actuelle.|  
|[GetUserStringHeapSize, méthode](imetadatatables-getuserstringheapsize-method.md)|Obtient la taille, en octets, du tas de la chaîne utilisateur.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IMetaDataTables2, interface](imetadatatables2-interface.md)
