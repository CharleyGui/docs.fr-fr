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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177122"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo, méthode
Obtient des données sur la colonne spécifiée dans le tableau spécifié.  
  
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
 [dans] L’index du tableau souhaité.  
  
 `ixCol`  
 [dans] L’index de la colonne souhaitée.  
  
 `poCol`  
 [out] Un pointeur à la compensation de la colonne dans la rangée.  
  
 `pcbCol`  
 [out] Un pointeur sur la taille, dans les octets, de la colonne.  
  
 `pType`  
 [out] Un pointeur sur le type de valeurs de la colonne.  
  
 `ppName`  
 [out] Un pointeur à un pointeur au nom de la colonne.  

## <a name="remarks"></a>Notes 

Le type de colonne retournée se situe dans une gamme de valeurs :

| pType (en)                    | Description   | Fonction d’aide                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)   | Débarrasser           | **IsRidType (isRidType)**<br>**IsRidOrToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | Jeton codé | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT`(96)            | Int16         | **IsFixedType (en)**                   |
| `iUSHORT`(97)           | UInt16        | **IsFixedType (en)**                   |
| `iLONG`(98)             | Int32         | **IsFixedType (en)**                   |
| `iULONG`(99)            | UInt32        | **IsFixedType (en)**                   |
| `iBYTE`(100)            | Byte          | **IsFixedType (en)**                   |
| `iSTRING`(101)          | String        | **IsHeapType**                    |
| `iGUID`(102)            | Guid          | **IsHeapType**                    |
| `iBLOB`(103)            | Objet blob          | **IsHeapType**                    |

Les valeurs qui *heap* sont stockées dans `IsHeapType == true`le tas (c’est-à-dire) peuvent être lues à l’aide de :

- `iSTRING`: **IMetadataTables.GetString**
- `iGUID`: **IMetadataTables.GetGUID**
- `iBLOB`: **IMetadataTables.GetBlob**

> [!IMPORTANT]
> Pour utiliser les constantes définies dans `#define _DEFINE_META_DATA_META_CONSTANTS` le tableau ci-dessus, inclure la directive fournie par le fichier d’en-tête *cor.h.*

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
