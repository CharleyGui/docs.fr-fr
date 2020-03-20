---
title: IMetaDataTables::GetColumn, méthode
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177142"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn, méthode
Obtient un pointeur à la valeur contenue dans la cellule de la colonne spécifiée et la ligne dans le tableau donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>Paramètres

 `ixTbl`  
 [dans] L’index du tableau.  
  
 `ixCol`  
 [dans] L’index de la colonne dans le tableau.  
  
 `rid`  
 [dans] L’index de la ligne dans le tableau.  
  
 `pVal`  
 [out] Un pointeur à la valeur de la cellule.  

## <a name="remarks"></a>Notes 

L’interprétation de la `pVal` valeur retournée dépend du type de la colonne. Le type de colonne peut être déterminé en appelant [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).

- La méthode **GetColumn** convertit automatiquement les colonnes de type **Rid** `mdToken` ou **CodedToken** en valeurs 32 bits complètes.
- Il convertit également automatiquement les valeurs 8 ou 16 bits en valeurs 32 bits complètes.
- Pour les colonnes de type *tas,* le *pVal* retourné sera un index dans le tas correspondant.

| Type de colonne              | pVal contient | Commentaire                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)  | mdToken     | *pVal* contiendra un jeton complet. La fonction convertit automatiquement le Rid en un jeton complet. |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | mdToken | Au retour, *pVal* contiendra un jeton complet. La fonction décomprime automatiquement le CodedToken en un jeton complet. |
| `iSHORT`(96)            | Int16         | Automatiquement signé-étendu à 32 bits.  |
| `iUSHORT`(97)           | UInt16        | Automatiquement signé-étendu à 32 bits.  |
| `iLONG`(98)             | Int32         |                                        |
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | Automatiquement signé-étendu à 32 bits.  |
| `iSTRING`(101)          | Index de tas de cordes | *pVal* est un index dans le tas de cordes. Utilisez [IMetadataTables::GetString](imetadatatables-getstring-method.md) pour obtenir la valeur de chaîne de colonne réelle. |
| `iGUID`(102)            | Indice de tas Guid | *pVal* est un index dans le tas Guid. Utilisez [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) pour obtenir la vraie colonne Guid valeur. |
| `iBLOB`(103)            | Indice de tas blob | *pVal* est un index dans le tas Blob. Utilisez [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) pour obtenir la valeur Blob colonne réelle. |
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **Versions cadre .NET**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
