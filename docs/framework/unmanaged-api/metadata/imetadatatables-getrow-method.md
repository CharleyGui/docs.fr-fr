---
title: IMetaDataTables::GetRow, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177115"
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow, méthode
Obtient la ligne à l’indice de ligne spécifié, dans le tableau à l’indice de table spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ixTbl`  
 [dans] L’index de la table à partir de laquelle la ligne sera récupérée.  
  
 `rid`  
 [dans] L’index de la ligne à obtenir.  
  
 `ppRow`  
 [out] Un pointeur à un pointeur de la ligne.  
  
## <a name="remarks"></a>Notes   

  Nous ne recommandons pas l’utilisation de cette méthode, car elle ne donne pas de résultats cohérents. Pour plus d’informations sur le tableau GUID, consultez la documentation sur l’infrastructure linguistique commune (CLI), en particulier «Partition II: Metadata Definition and Semantics». La documentation est disponible en ligne; voir [ECMA C et Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and Standard [ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **Versions cadre .NET**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
