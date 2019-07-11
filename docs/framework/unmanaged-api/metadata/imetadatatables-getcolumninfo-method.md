---
title: IMetaDataTables::GetColumnInfo, méthode
ms.date: 03/30/2017
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
ms.openlocfilehash: c0755cb2a91d61725338562cb1fe249a9cfacc38
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781514"
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
 `ixTbl`  
 [in] Index de la table souhaitée.  
  
 `ixCol`  
 [in] Index de la colonne souhaitée.  
  
 `poCol`  
 [out] Pointeur vers l’offset de la colonne dans la ligne.  
  
 `pcbCol`  
 [out] Pointeur vers la taille, en octets, de la colonne.  
  
 `pType`  
 [out] Un pointeur vers le type des valeurs dans la colonne.  
  
 `ppName`  
 [out] Pointeur vers un pointeur vers le nom de colonne.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
