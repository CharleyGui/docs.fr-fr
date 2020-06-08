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
ms.openlocfilehash: 76d23fe9221ae5a07d79b8c5c1a7ad297922b003
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501246"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn, méthode
Obtient un pointeur vers la valeur contenue dans la cellule de la colonne et de la ligne spécifiées dans la table donnée.  
  
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
 dans Index de la table.  
  
 `ixCol`  
 dans Index de la colonne dans la table.  
  
 `rid`  
 dans Index de la ligne dans la table.  
  
 `pVal`  
 à Pointeur vers la valeur dans la cellule.  

## <a name="remarks"></a>Remarques

L’interprétation de la valeur retournée par `pVal` dépend du type de la colonne. Le type de colonne peut être déterminé en appelant [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).

- La méthode **GetColumn** convertit automatiquement les colonnes de type **RID** ou **CodedToken** en valeurs 32 bits complètes `mdToken` .
- Il convertit également automatiquement les valeurs de 8 ou 16 bits en valeurs 32 bits complètes.
- Pour les colonnes de type *Heap* , le *pval* retourné est un index dans le tas correspondant.

| Type de colonne              | pVal contient | Commentaire                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)  | mdToken     | *pval* contient un jeton complet. La fonction convertit automatiquement le RID en jeton complet. |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | mdToken | Lors du retour, *pval* contient un jeton complet. La fonction décompresse automatiquement le CodedToken en jeton complet. |
| `iSHORT`(96)            | Int16         | Signature automatique-étendu à 32 bits.  |
| `iUSHORT`(97)           | UInt16        | Signature automatique-étendu à 32 bits.  |
| `iLONG`(98)             | Int32         |                                        |
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | Signature automatique-étendu à 32 bits.  |
| `iSTRING`(101)          | Index du tas de chaîne | *pval* est un index dans le tas de chaîne. Utilisez [IMetadataTables :: GetString](imetadatatables-getstring-method.md) pour récupérer la valeur de la chaîne de colonne réelle. |
| `iGUID`(102)            | Index du tas GUID | *pval* est un index dans le tas GUID. Utilisez [IMetadataTables :: GetGuid](imetadatatables-getguid-method.md) pour récupérer la valeur du GUID de colonne réel. |
| `iBLOB`(103)            | Index du tas d’objets BLOB | *pval* est un index dans le tas d’objets BLOB. Utilisez [IMetadataTables :: GetBlob](imetadatatables-getblob-method.md) pour récupérer la valeur réelle de l’objet blob de colonne. |
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](imetadatatables-interface.md)
- [IMetaDataTables2, interface](imetadatatables2-interface.md)
