---
title: IMetaDataTables::GetColumnInfo, méthode
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd67d9faafedf4fb92c69618d4464ebb2ce47dcc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774259"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo, méthode
Obtient les données relatives à la colonne spécifiée dans la table spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>Paramètres
=======

 `ixTbl`  
 dans Index de la table souhaitée.  
  
 `ixCol`  
 dans Index de la colonne souhaitée.  
  
 `poCol`  
 à Pointeur vers le décalage de la colonne dans la ligne.  
  
 `pcbCol`  
 à Pointeur vers la taille, en octets, de la colonne.  
  
 `pType`  
 à Pointeur vers le type des valeurs de la colonne.  
  
 `ppName`  
 à Pointeur vers un pointeur vers le nom de la colonne.  
 
## <a name="remarks"></a>Notes

Le type de colonne retourné est compris dans une plage de valeurs :

| pType                    | Description   | Fonction d’assistance                   |
|--------------------------|---------------|-----------------------------------|
| `0`.. `iRidMax`<br>(0.. 63)   | RID           | **IsRidType**<br>**IsRidOrToken** |
| `iCodedToken`.. `iCodedTokenMax`<br>(64.. 95) | Jeton codé | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT` (96)            | Int16         | **IsFixedType**                   |
| `iUSHORT` (97)           | UInt16        | **IsFixedType**                   |
| `iLONG` (98)             | Int32         | **IsFixedType**                   |
| `iULONG` (99)            | UInt32        | **IsFixedType**                   |
| `iBYTE` (100)            | Byte          | **IsFixedType**                   |
| `iSTRING` (101)          | Chaîne        | **IsHeapType**                    |
| `iGUID` (102)            | GUID          | **IsHeapType**                    |
| `iBLOB` (103)            | Blob          | **IsHeapType**                    |

Les valeurs stockées dans le *tas* (autrement dit, `IsHeapType == true`) peuvent être lues à l’aide de :

- `iSTRING` : **IMetadataTables. GetString**
- `iGUID` : **IMetadataTables. GetGuid**
- `iBLOB` : **IMetadataTables. getBlob**

> [!IMPORTANT]
> Pour utiliser les constantes définies dans le tableau ci-dessus, incluez la directive `#define _DEFINE_META_DATA_META_CONSTANTS` fournie par le fichier d’en-tête *Cor. h* .

## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
