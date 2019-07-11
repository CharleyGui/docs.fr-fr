---
title: IMetaDataTables::GetNextString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c2008556ebf1b1961aef7dc0f24fd0a3161d06e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781450"
---
# <a name="imetadatatablesgetnextstring-method"></a>IMetaDataTables::GetNextString, méthode
Obtient l’index de la chaîne suivante dans la colonne de table actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ixString`  
 [in] La valeur d’index d’une colonne de table de chaînes.  
  
 `pNext`  
 [out] Pointeur vers l’index de la chaîne suivante dans la colonne.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
