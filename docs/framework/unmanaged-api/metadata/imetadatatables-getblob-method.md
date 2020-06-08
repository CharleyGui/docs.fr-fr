---
title: IMetaDataTables::GetBlob, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: ff97e419c5309fa7cb820cb7e82db96fee34f30c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501272"
---
# <a name="imetadatatablesgetblob-method"></a>IMetaDataTables::GetBlob, méthode
Obtient un pointeur vers l’objet BLOB (Binary Large Object) situé à l’index de colonne spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ixBlob`  
 dans Adresse mémoire à partir de laquelle effectuer l’extraction `ppData` .  
  
 `pcbData`  
 à Pointeur vers la taille, en octets, de `ppData` .  
  
 `ppData`  
 à Pointeur vers un pointeur vers les données binaires récupérées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](imetadatatables-interface.md)
- [IMetaDataTables2, interface](imetadatatables2-interface.md)
