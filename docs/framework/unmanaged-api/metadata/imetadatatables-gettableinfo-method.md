---
title: IMetaDataTables::GetTableInfo, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 7e60dd9535809ca13f3bbe6ac76f5ea1209df734
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501166"
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo, méthode
Obtient le nom, la taille de ligne, le nombre de lignes, le nombre de colonnes et l’index de colonne clé de la table spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ixTbl`  
 dans Identificateur de la table dont les propriétés doivent être retournées.  
  
 `pcbRow`  
 à Pointeur vers la taille, en octets, d’une ligne de table.  
  
 `pcRows`  
 à Pointeur vers le nombre de lignes dans la table.  
  
 `pcCols`  
 à Pointeur vers le nombre de colonnes dans la table.  
  
 `piKey`  
 à Pointeur vers l’index de la colonne clé, ou-1 si la table n’a pas de colonne clé.  
  
 `ppName`  
 à Pointeur vers un pointeur vers le nom de la table.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](imetadatatables-interface.md)
- [IMetaDataTables2, interface](imetadatatables2-interface.md)
